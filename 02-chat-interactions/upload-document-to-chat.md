# Upload Document to Chat Context

## Overview
**Flow ID**: `upload-document-to-chat`  
**Category**: Chat Interactions  
**Estimated Duration**: 1-3 minutes  
**User Role**: All Users  
**Complexity**: Moderate  

**Purpose**: Upload documents (PDF, DOCX, TXT, CSV) to chat input to include their content in your message. System extracts text from files and combines with your typed message, allowing AI to reference document content. Up to 10 documents can be added to a single message.

---

## Trigger

**What initiates this flow:**
- [x] User manually initiates

**Specific trigger**: User wants AI to reference specific document content without creating permanent dataset.

---

## Prerequisites

**Before starting, users must have:**
- [x] Active chat open
- [x] Document files to upload
- [x] Files under size limit (~2000 characters extracted text)

---

## User Intent Analysis

### Primary Intent
Include document content in chat message for AI to reference, analyze, or discuss.

### Secondary Intents
- Get AI to summarize documents
- Ask questions about document content
- Compare multiple documents
- Extract information from files

---

## Step-by-Step Flow

### Main Path

**Step 1: Locate Upload Button**
- **User Action**: In chat input area, find paperclip or upload icon
- **System Response**: N/A
- **UI Elements Visible**: 
  - Chat input text area
  - Upload icon button (paperclip)
  - Other controls (send, dataset toggle)

**Step 2: Click Upload Icon**
- **User Action**: Click paperclip/upload icon
- **System Response**: File browser opens
- **UI Elements Visible**: 
  - Operating system file selector
  - File type filter (PDF, DOCX, TXT, CSV)

**Step 3: Select Document File**
- **User Action**: Navigate to file, select, click "Open"
- **System Response**: 
  - File uploads
  - Text extraction begins
  - Progress indicator appears
- **UI Elements Visible**: 
  - Upload progress indicator or tooltip
  - Status: "Uploading..." then "Extracting text..."
  - May show filename

**Step 4: Text Extraction Completes**
- **User Action**: Wait briefly (usually seconds)
- **System Response**: 
  - Text extracted from file
  - Document "pill" or badge appears in input area
  - Character count updates to include document text
- **UI Elements Visible**: 
  - Document pill/badge showing:
    - Filename
    - X button to remove
  - Character counter increases
  - Document count (e.g., "1 document")

**Step 5: Optional - Add More Documents**
- **User Action**: Click upload icon again to add additional files (up to 10 total)
- **System Response**: Each document adds as separate pill
- **UI Elements Visible**: 
  - Multiple document pills
  - Counter: "3 documents"
  - Character total includes all documents

**Step 6: Type Message About Documents**
- **User Action**: Type question or instruction related to uploaded documents
- **System Response**: Text appears in input
- **UI Elements Visible**: 
  - Text input with message
  - Document pills remain visible
  - Total character count shown

**Step 7: Send Message with Documents**
- **User Action**: Click send button
- **System Response**: 
  - Message sent with both typed text and document contents
  - User message shows typed text
  - AI receives full context including documents
  - Documents listed in message as "Reference Documents:"
- **UI Elements Visible**: 
  - User message in chat
  - Document references shown
  - AI generates response considering documents

**Step 8: Optional - Remove Document**
- **User Action**: Before sending, click X on document pill to remove it
- **System Response**: 
  - Document removed
  - Pill disappears
  - Character count decreases

**Final Step: Documents Included in Conversation**
- **Success Indicator**: 
  - AI response references document content
  - Documents successfully processed
  - Can continue with document context
- **System State Change**: 
  - Document content included in message
  - AI has access to file information
  - Message history includes document reference
- **Next Possible Actions**: 
  - Send follow-up questions about documents
  - Upload different documents
  - Continue conversation with document context

---

## Alternative Paths & Strategies

### Strategy A: Drag and Drop Files
**When to use**: Convenient file access

**Steps**:
1. Open file manager alongside browser
2. Drag document file to chat input area
3. Drop file
4. Extraction proceeds automatically
5. Continue as normal

**QA Note**: Drag-drop not confirmed but common UX pattern. May not be implemented.

---

## Error States & Recovery

### Error 1: File Too Large
**Cause**: Extracted text exceeds 2000 character limit  
**User Experience**: 
- Error: "File too large" or "Exceeds character limit"
- Document not added

**Recovery Steps**:
1. Use smaller document
2. Extract relevant sections manually
3. Create dataset instead for large documents

### Error 2: Cannot Extract Text
**Cause**: Image-based PDF, corrupted file, or unsupported format  
**User Experience**: 
- Error: "Text extraction failed"
- Document pill shows error state

**Recovery Steps**:
1. Remove failed document
2. Convert to text-based format
3. Use OCR for scanned PDFs
4. Try different file

### Error 3: 10 Document Limit Reached
**Cause**: Already have 10 documents attached  
**User Experience**: 
- Error: "Maximum 10 documents"
- Cannot add more

**Recovery Steps**:
1. Remove less important documents
2. Combine information manually
3. Send multiple messages
4. Create dataset for large document sets

---

## Pain Points & Friction

**Identified Issues**:

1. **10 Document Limit**
   - **Impact**: Cannot include many documents at once
   - **Potential Improvement**: Increase limit or remove limit

2. **Documents Lost After Sending**
   - **Impact**: Must re-upload for next message
   - **Potential Improvement**: Keep documents for subsequent messages

3. **No Preview of Extracted Text**
   - **Impact**: Can't verify extraction quality
   - **Potential Improvement**: Show extracted text preview

---

## Design Considerations

**Following Contextual Design Principles**:

1. **Automation Opportunities**: Auto-extract on upload
2. **Simplification Opportunities**: Drag-drop support
3. **User Trust**: Show extraction success clearly

---

## Related Flows

- [Chat with Dataset Query Enabled](./rag-enabled-chat.md) - Alternative for permanent document access
- [Create New Blockify Job](../05-blockify-processing/create-blockify-job.md) - For large document sets
- [Conduct Multi-Turn Conversation](./multi-turn-conversation.md) - Using documents in conversation

---

## Technical References

**Knowledge Base Sections**:
- src/components/chat/chat-input.js - Document upload functionality
- src/handlers/upload/extract-utils.js - Text extraction

---

## Version History

| Date | Version | Author | Changes |
|------|---------|--------|---------|
| 2025-10-04 | 1.1 | [Iternal Technologies](https://iternal.ai/airgapai) | Initial comprehensive documentation |

---

## Notes

**Important Considerations**:
- Documents are temporary; included only in current message
- Text extraction happens automatically
- Supports PDF, DOCX, TXT, CSV
- Maximum 10 documents per message
- Each document limited to ~2000 characters extracted text
- For large or permanent document sets, use datasets instead

**Use Cases**:
- Ask AI to summarize a report
- Compare multiple documents
- Extract specific information from files
- Analyze document content

**Best Practices**:
- Use for one-off document references
- For frequent use, create dataset instead
- Verify extraction succeeded (document pill appears)
- Keep documents concise for better results

**Common User Questions**:
- "Can I use same document in multiple messages?" - Must re-upload each time
- "What if file is too large?" - Use datasets feature for large documents
- "Does AI remember documents from previous messages?" - No, include in each message if needed
- "Can I see extracted text?" - Currently no preview; improvement opportunity

