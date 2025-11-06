# Chat with Dataset Query Enabled

## Overview
**Flow ID**: `rag-enabled-chat`  
**Category**: Chat Interactions  
**Estimated Duration**: 2-5 minutes per exchange  
**User Role**: All Users  
**Complexity**: Moderate  

**Purpose**: This flow enables users to have conversations with the AI where responses are informed by a specific dataset (corpus) of documents. When dataset query is enabled, the system automatically searches your uploaded documents for relevant information and includes that context in the AI's response, resulting in more accurate, grounded answers based on your specific knowledge base.

---

## Trigger

**What initiates this flow:**
- [x] User manually initiates


**Specific trigger**: User wants to ask questions that should be answered using information from their specific documents, typically because:
- They have technical documentation and need accurate answers from it
- They want to chat about specific company information
- They need to reference specific content from uploaded documents
- They want answers grounded in their own data rather than general AI knowledge
- They're conducting research using a curated document collection

---

## Prerequisites

**Before starting, users must have:**
- [x] Application installed and running
- [x] At least one AI language model uploaded and active
- [x] At least one dataset (corpus) uploaded and available
- [x] The desired dataset set as the active dataset in settings
- [x] Understanding that dataset query adds processing time to responses

---

## User Intent Analysis

### Primary Intent
Ask questions that are answered using information specifically from the user's uploaded document collection, ensuring responses are grounded in accurate, user-provided information rather than relying solely on the AI's general training.

### Secondary Intents
- Verify information exists in their documents
- Get specific quotes or references from documents
- Explore content across multiple documents simultaneously
- Cross-reference information from different sources
- Ensure factual accuracy by grounding responses in known data
- Save time compared to manually searching through documents

### Subintents
- Quickly identify relevant information in large document sets
- Get synthesized answers that combine multiple document sources
- Understand relationships between concepts across documents
- Validate that claimed information actually exists in source materials

---

## Step-by-Step Flow

### Main Path (Happy Path)

**Step 1: Verify Dataset is Configured**
- **User Action**: Before starting a chat, verify that a dataset is available and active
- **System Response**: Dataset status can be checked in Settings or will be visible in chat interface
- **UI Elements Visible**: 
  - Settings page showing active dataset (if checking there)
  - OR chat interface showing dataset selector
- **Visual Cues**: Active dataset indicated by name or status indicator
- **Note**: See corpus-activation.md for how to activate a dataset if needed

**Step 2: Navigate to Chat or Create New Chat**
- **User Action**: Go to Chat page (click "Chat" in navigation) or start a new conversation
- **System Response**: Chat interface loads
- **UI Elements Visible**: 
  - Chat page with conversation area
  - Text input box at bottom
  - Dataset selector/toggle (collapsible control, usually 100px wide)
  - Send button
  - Previous messages (if continuing existing chat)
- **Visual Cues**: Dataset icon visible in input area

**Step 3: Locate Dataset Control**
- **User Action**: Look for the dataset toggle control, typically in the message input area
- **System Response**: N/A (static UI element)
- **UI Elements Visible**: 
  - Dataset icon (brain or database symbol)
  - Text showing current dataset status ("ON" or "OFF" and dataset name)
  - Collapsible selector that expands when hovered
- **Visual Cues**: 
  - Icon color indicates status (blue for enabled, gray for disabled)
  - Control is usually in the bottom-left of input area

**Step 4: Enable Dataset Query**
- **User Action**: Click the dataset icon or toggle to enable dataset query
- **System Response**: 
  - Dataset selector may expand to show full width (from 100px to ~235px)
  - Dropdown appears showing available datasets
  - Current selection is highlighted
  - Toggle switches to "ON" state
- **UI Elements Visible**: 
  - Expanded dataset selector
  - Dropdown list of available datasets
  - Dataset names
  - Currently selected dataset highlighted
  - "ON" indicator
- **Visual Cues**: 
  - Icon changes color (typically gray → blue)
  - Icon may change from "OFF" to "ON" symbol
  - Border or background color change indicates active state
  - Dataset name becomes visible

**Step 5: Confirm Correct Dataset Selected**
- **User Action**: Review the selected dataset name to ensure it's the right one for your question
- **System Response**: Selected dataset name is displayed
- **UI Elements Visible**: 
  - Dataset name in the selector
  - Dropdown remains open showing all options
- **Visual Cues**: Selected dataset has different styling (highlighted, checkmark, or bold)
- **Note**: If wrong dataset is selected, click dropdown to choose a different one

**Step 6: Compose Question for Dataset**
- **User Action**: Type a question that should be answered using the dataset documents
- **System Response**: 
  - Text appears in input box as typed
  - Send button becomes enabled
  - Dataset remains enabled (icon stays blue)
- **UI Elements Visible**: 
  - Text input with your question
  - Enabled send button
  - Active dataset indicator
  - Character count (if applicable)
- **Visual Cues**: 
  - Dataset icon remains blue indicating dataset query is active
  - Standard text input behavior

**Step 7: Send Message**
- **User Action**: Click send button or press Enter
- **System Response**: 
  - Message is sent
  - Text input clears
  - User message appears in conversation
  - System begins processing with dataset query
  - Loading indicator appears
- **UI Elements Visible**: 
  - User's message in conversation thread
  - Loading indicator with status text
  - May show specific status: "Searching dataset..." or "Querying documents..."
- **Visual Cues**: 
  - Animated loading indicator
  - Status message indicates dataset is being searched
  - May be slightly longer loading time than without dataset

**Step 8: System Searches Dataset**
- **User Action**: Wait (no action required)
- **System Response**: 
  - System converts your question into a search query
  - Searches through dataset documents for relevant information
  - Identifies top matches (typically 5 results)
  - Extracts relevant passages
  - Prepares context for AI
- **UI Elements Visible**: 
  - Loading indicator continues
  - Status may update: "Found X relevant passages" or similar
  - Progress indication
- **Visual Cues**: 
  - Animated indicator shows system is working
  - Process may take 2-5 seconds longer than normal chat

**Step 9: AI Generates Response with Dataset Context**
- **User Action**: Continue waiting
- **System Response**: 
  - AI receives your question plus relevant dataset passages
  - AI formulates response using both its knowledge and the dataset information
  - Response begins streaming
- **UI Elements Visible**: 
  - AI response bubble begins appearing
  - Text streams in progressively
  - Dataset icon may appear near the response
- **Visual Cues**: 
  - Streaming text animation
  - Response appears in AI message style

**Step 10: View Response with Dataset References**
- **User Action**: Read the AI's response
- **System Response**: 
  - Complete response is displayed
  - Response may include references to source documents
  - May see specific formatting for dataset-sourced information
- **UI Elements Visible**: 
  - Full AI response text
  - Possibly: Special icon or indicator showing dataset was used
  - Possibly: Expandable section showing which dataset passages were used
  - Action buttons (Copy, Redo, Like/Dislike)
  - Dataset results icon (if results were found and used)
- **Visual Cues**: 
  - Response may have distinct formatting for dataset-sourced content
  - Dataset results icon (stacked layers symbol) may appear

**Step 11: Optional - View Source Passages**
- **User Action**: If a dataset results icon appears, hover over or click it to see source passages
- **System Response**: Tooltip or expandable panel shows the actual passages from your documents that were used
- **UI Elements Visible**: 
  - Popup or panel displaying dataset passages
  - For each passage: 
    - Block name (document identifier)
    - Critical question (if using Blockify format)
    - Trusted answer (the actual content)
    - Similarity score (percentage match)
- **Visual Cues**: 
  - Green-bordered boxes for dataset content
  - Percentage indicators showing relevance
  - Clear formatting distinguishes source material from AI response

**Step 12: Continue Conversation with Dataset Enabled**
- **User Action**: Type another question in the input box
- **System Response**: Dataset remains enabled for subsequent messages
- **UI Elements Visible**: 
  - Text input ready
  - Dataset icon still showing "ON" (blue)
  - Previous conversation visible above
- **Visual Cues**: Dataset status persists (stays blue)
- **Note**: Each subsequent message will also query the dataset unless you disable it

**Step 13: Optional - Disable Dataset for Next Message**
- **User Action**: Click dataset icon to toggle it OFF if you want to ask a question without dataset query
- **System Response**: 
  - Dataset selector collapses back to icon-only
  - Icon color changes to gray/inactive
  - Shows "OFF" state
- **UI Elements Visible**: 
  - Collapsed dataset control (100px width)
  - Gray/inactive icon
  - "OFF" indicator
- **Visual Cues**: Color change from blue to gray indicates dataset is no longer active

**Final Step: Dataset-Enhanced Conversation**
- **Success Indicator**: 
  - Responses reference specific information from your documents
  - Dataset results icon appears when relevant passages are found
  - Answers are more specific and accurate to your data
  - Can view source passages to verify information
- **System State Change**: 
  - Conversation history includes both dataset-queried and non-dataset messages
  - Each message retains metadata about whether dataset was used
  - Dataset remains active or inactive based on last toggle state
- **Next Possible Actions**: 
  - Continue asking dataset-related questions
  - Toggle dataset off for general questions
  - View and verify source passages
  - Export conversation with dataset references
  - Switch to a different dataset
  - Continue conversation with context maintained

---

## Alternative Paths & Strategies

### Strategy A: Toggle Dataset On/Off During Conversation
**When to use**: User wants to mix dataset-specific questions with general AI questions in the same chat

**Steps**:
1. Start conversation with dataset enabled
2. Ask dataset-specific question, get response
3. Toggle dataset OFF for next message
4. Ask general question without dataset
5. Toggle dataset back ON for another dataset question
6. Continue alternating as needed

### Strategy B: Compare Multiple Datasets
**When to use**: User has multiple datasets and wants to compare information across them

**Steps**:
1. Enable dataset query and select first dataset
2. Ask question, note response
3. Open dataset dropdown
4. Select second dataset
5. Ask same or similar question
6. Compare responses to see differences in information
7. Can document which dataset provides better information for specific topics

### Strategy C: Verify AI Claims with Dataset
**When to use**: User gets an AI response without dataset and wants to verify against documents

**Steps**:
1. Ask question with dataset OFF, get general AI response
2. Enable dataset query
3. Ask "Can you verify that using my documents?" or rephrase original question
4. Compare general response to dataset-grounded response
5. View source passages to validate claims

### Strategy D: Drill Down on Dataset Results
**When to use**: User wants more detail from the source documents

**Steps**:
1. Ask initial question with dataset enabled
2. View response and source passages
3. Click on or reference specific passage in follow-up
4. Ask "Tell me more about [specific passage]"
5. AI focuses on that specific document content
6. Continue drilling into specifics

---

## Error States & Recovery

### Error 1: No Dataset Selected/Available
**Cause**: User tries to enable dataset query but no dataset is configured  
**User Experience**: 
- Dataset toggle may not work or show disabled state
- Error message: "No dataset available" or "Please upload a dataset"
- Icon may be grayed out and unclickable

**Recovery Steps**:
1. Navigate to Settings or Datasets page
2. Upload a dataset if none exist (see corpus-upload.md)
3. Activate a dataset if one exists but isn't active (see corpus-activation.md)
4. Return to Chat and enable dataset query
5. Dataset should now be selectable

### Error 2: Dataset Search Returns No Results
**Cause**: Question doesn't match any content in the dataset  
**User Experience**: 
- Response may indicate "No relevant information found in dataset"
- AI provides general response without dataset grounding
- Dataset results icon may not appear
- Response might state "I don't see relevant information in your documents about..."

**Recovery Steps**:
1. Rephrase question using different terms
2. Make question more general or specific
3. Verify question relates to content actually in your dataset
4. Check if correct dataset is selected
5. If no results consistently, may need to add more documents to dataset

**QA Note**: This is not a technical error but expected behavior when dataset lacks relevant information. No system error occurs.

### Error 3: Dataset Loading Failed
**Cause**: Technical issue loading the dataset into memory  
**User Experience**: 
- Error message: "Failed to load dataset" or "Dataset unavailable"
- Dataset toggle may show error state
- Cannot complete query

**Recovery Steps**:
1. Wait a moment and try again
2. Refresh the page
3. Check if dataset file still exists (Settings > Datasets)
4. Try selecting a different dataset
5. Restart application if issue persists

### Error 4: Embedding Model Not Available
**Cause**: No embedding model is loaded (required for dataset search)  
**User Experience**: 
- Error message: "Embedding model required for dataset query"
- Dataset feature may be disabled entirely
- Cannot enable dataset toggle

**Recovery Steps**:
1. Navigate to Settings
2. Upload an embedding model if none exist
3. Select an embedding model as active
4. Wait for model to load
5. Return to Chat and try enabling dataset again

### Error 5: Query Takes Too Long / Times Out
**Cause**: Very large dataset or complex query  
**User Experience**: 
- Loading indicator continues for extended time (>30 seconds)
- May eventually timeout with error message
- Response may fail to generate

**Recovery Steps**:
1. Wait a bit longer (large datasets can take time)
2. Simplify your question
3. Check system resources (RAM, CPU)
4. Consider breaking dataset into smaller, topic-specific datasets
5. Try question again after timeout

---

## Pain Points & Friction

**Identified Issues**:

1. **Dataset Search Process Not Transparent**
   - **Impact**: Users don't know what's happening during the 2-5 second dataset search delay
   - **Frequency**: Every dataset-enabled message
   - **Potential Improvement**: 
     - Show search process: "Searching 1,247 documents...", "Found 5 matches...", "Reading passages..."
     - Display progress indicator for dataset search phase
     - Show which documents are being searched

2. **No Indication of Dataset Quality/Coverage**
   - **Impact**: Users don't know if their dataset has relevant information before asking
   - **Frequency**: Constant uncertainty, especially with new datasets
   - **Potential Improvement**: 
     - Show dataset statistics (number of documents, topics covered, last updated)
     - Preview dataset contents
     - Suggest dataset improvements based on common queries with no results

3. **Source Passages Hidden by Default**
   - **Impact**: Users may not realize they can view the actual source material
   - **Frequency**: Common for new users
   - **Potential Improvement**: 
     - Make source passages more prominent
     - Auto-expand sources on first use
     - Add tutorial or tooltip explaining the feature

4. **Cannot Select Specific Documents**
   - **Impact**: If dataset contains many documents, can't limit search to specific ones
   - **Frequency**: Users with large, diverse datasets
   - **Potential Improvement**: 
     - Add document filtering option
     - Allow "search only in these documents" selection
     - Create sub-datasets or tags

5. **Dataset Toggle Easy to Miss**
   - **Impact**: Users may not notice the dataset feature exists or how to enable it
   - **Frequency**: Common for first-time users
   - **Potential Improvement**: 
     - Make toggle more prominent
     - Add onboarding tooltip
     - Highlight feature when dataset is first uploaded

6. **No Confidence Scores on Responses**
   - **Impact**: Users can't tell how strongly the response is supported by dataset vs. AI's general knowledge
   - **Frequency**: Every dataset-enabled response
   - **Potential Improvement**: 
     - Show percentage of response based on dataset vs. general knowledge
     - Highlight dataset-sourced sentences differently
     - Add confidence indicators

---

## Design Considerations

**Following Contextual Design Principles**:

1. **Automation Opportunities**: 
   - Auto-enable dataset when question keywords match dataset content
   - Auto-select most relevant dataset if multiple are available
   - Auto-suggest rephrasing if no results found
   - Auto-highlight key information from dataset in the response

2. **Simplification Opportunities**: 
   - Consider making dataset query the default behavior when dataset is active
   - Eliminate need to manually toggle if user primarily uses dataset feature
   - Streamline dataset selection if user only has one dataset
   - Reduce clicks required to view source passages

3. **Transition Smoothness**: 
   - Seamless flow between dataset-enabled and disabled states
   - Smooth display of source passages when requested
   - Natural integration of dataset information into responses
   - Easy to switch between different datasets

4. **User Trust**: 
   - Clear indication when dataset is being used
   - Visible source passages build confidence in accuracy
   - Transparent search process shows system is working
   - Similarity scores help users judge relevance

5. **Cognitive Load**: 
   - Don't require users to remember when dataset is enabled
   - Persistent visual indicator of dataset state
   - Simple on/off toggle without complex configuration
   - Clear distinction between AI knowledge and dataset knowledge

---

## Related Flows

- [Upload New Dataset](../04-dataset-management/corpus-upload.md) - Add documents for querying
- [Activate/Deactivate Dataset](../04-dataset-management/corpus-activation.md) - Switch active dataset
- [View Dataset Details](../04-dataset-management/view-dataset-details.md) - See what's in your dataset
- [Create New Empty Chat](./new-chat-empty.md) - Start a conversation
- [Conduct Multi-Turn Conversation](./multi-turn-conversation.md) - Continue with dataset context
- [Upload Document to Chat Context](./upload-document-to-chat.md) - Alternative to dataset for one-off documents

---

## Technical References

**Knowledge Base Sections**:
- src/components/ui/corpus-chooser.js - Dataset selector control
- src/components/chat/chat-input.js - Input area with dataset toggle
- src/engines/vector-search.js - Dataset search functionality
- src/engines/embedding.js - Document embedding for search
- src/components/chat/chat-message.js - Display with dataset results

**Key Components**:
- Dataset toggle control with on/off states
- Vector search engine for document matching
- Embedding model for semantic search
- Results display with source passage viewing

---

## Version History

| Date | Version | Author | Changes |
|------|---------|--------|---------|
| 2025-10-04 | 1.1 | [Iternal Technologies](https://iternal.ai/airgapai) | Initial comprehensive documentation |

---

## Notes

**Important Considerations**:
- Dataset search adds 2-5 seconds to response time but significantly improves accuracy
- The number of results used (typically 5) can be configured in chat settings
- Similarity scores show how well each passage matches your question (higher is better)
- Dataset query uses an embedding model (separate from the chat model) to search documents
- Very large datasets may take longer to search; consider breaking into topic-specific sets
- Dataset feature requires both a chat model and an embedding model to be configured

**Best Practices for Dataset Query**:
- Use clear, specific questions that relate to your document content
- Enable dataset when you need factual information from your documents
- Disable dataset for general questions that don't require specific document references
- Review source passages to verify the AI correctly interpreted the information
- Organize documents into focused datasets by topic for faster, more relevant results
- Include metadata or clear document names to help identify source materials

**Common User Questions**:
- "Why does it take longer with dataset enabled?" - The system must search through all documents to find relevant passages
- "How does it know which documents to use?" - Semantic search finds the most similar content to your question
- "Can I see the exact source?" - Yes, hover over or click the dataset results icon
- "What if my question isn't in the dataset?" - The AI will provide a general response or indicate no relevant information was found
- "How many documents can I have in a dataset?" - Thousands, but larger datasets take longer to search

