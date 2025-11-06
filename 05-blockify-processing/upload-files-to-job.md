# Upload Files for Processing

## Overview
**Flow ID**: `upload-files-to-job`  
**Category**: Blockify Processing  
**Estimated Duration**: 2-10 minutes (depending on file count and size)  
**User Role**: All Users  
**Complexity**: Moderate  

**Purpose**: This flow describes how users upload document files to a blockify or chunking job for AI processing. The system extracts text from various file formats (PDF, DOCX, TXT, CSV, ZIP) and prepares them for chunking and structuring. Multiple files can be uploaded, and ZIP archives are automatically extracted.

---

## Trigger

**What initiates this flow:**
- [x] User manually initiates


**Specific trigger**: User is creating a blockify or chunking job and needs to add document files for processing, occurring during job setup workflow.

---

## Prerequisites

**Before starting, users must have:**
- [x] Blockify job creation screen open
- [x] Document files prepared on computer (PDF, DOCX, TXT, CSV, or ZIP formats)
- [x] Files contain text content to extract
- [x] Sufficient disk space for uploads and text extraction

---

## User Intent Analysis

### Primary Intent
Upload document files to the job so they can be processed, structured, and made searchable through the blockify or chunking pipeline.

### Secondary Intents
- Batch upload multiple documents efficiently
- Verify files upload correctly before processing begins
- Handle different file formats seamlessly
- Extract ZIP archives automatically
- Retry failed uploads without losing progress

### Subintents
- Ensure all intended files are included
- Verify text extraction succeeds
- See upload progress for large files
- Identify and resolve problematic files

---

## Step-by-Step Flow

### Main Path (Happy Path)

**Step 1: Locate File Upload Area**
- **User Action**: On blockify job creation screen, find the file upload section
- **System Response**: Upload interface is displayed
- **UI Elements Visible**: 
  - File upload dropzone (area with dashed border)
  - "Choose Files" or "Upload Files" button
  - Upload icon (cloud, paperclip, or folder)
  - Supported formats text: "Supports: PDF, DOCX, DOC, TXT, CSV, ZIP"
  - Empty file list area (or existing files if any uploaded)
- **Visual Cues**: 
  - Dashed border around upload area
  - Clear call-to-action button
  - Upload icon

**Step 2: Initiate File Selection**
- **User Action**: Click "Choose Files" button OR drag files from file manager
- **System Response**: 
  - If clicked: File browser dialog opens
  - If dragged: Dropzone highlights to show ready to accept
- **UI Elements Visible**: 
  - File browser (if clicked) showing computer's file system
  - OR highlighted dropzone (if dragging)
- **Visual Cues**: 
  - Dropzone may change color when files dragged over
  - File browser standard appearance

**Step 3: Select Files**
- **User Action**: 
  - In file browser: Navigate to files, select one or multiple files (Ctrl+click or Shift+click), click "Open"
  - OR drag files from file manager and drop into dropzone
- **System Response**: 
  - File browser closes (if used)
  - Files immediately begin uploading
  - File list table appears/updates on right side
- **UI Elements Visible**: 
  - File list table with columns:
    - Icon (file type icon)
    - Filename
    - Size
    - Status
    - Actions (retry, delete)
  - Each file showing initial status
- **Visual Cues**: 
  - Files appear in list immediately
  - Status shows "Uploading..." or "Processing..."

**Step 4: Upload and Text Extraction Begins**
- **User Action**: Watch as files upload and text is extracted
- **System Response**: 
  - For each file:
    1. File uploads to server
    2. System detects file type
    3. Text extraction begins automatically
    4. PDF: Text extracted from PDF pages
    5. DOCX: Text extracted from document
    6. TXT/CSV: Text loaded directly
    7. ZIP: Archive expanded, each file within processed separately
  - Status updates for each file
- **UI Elements Visible**: 
  - File table with real-time status updates:
    - Loading spinner icon while extracting
    - Status text: "Extracting..." or "Processing..."
    - Progress indication (if available)
    - Estimated time (if available)
  - For ZIP files: May show nested file structure
- **Visual Cues**: 
  - Animated spinners
  - Status text changes
  - File type icons (PDF, Word document, text file icons)

**Step 5: ZIP File Expansion (if applicable)**
- **User Action**: If ZIP file uploaded, watch it expand
- **System Response**: 
  - ZIP file entry shows expansion control (chevron/arrow)
  - Child files extracted and listed
  - Each child file processes individually
- **UI Elements Visible**: 
  - Parent ZIP entry with expand/collapse control
  - Indented child files listed beneath ZIP
  - Each child shows own status
  - ZIP shows overall status based on children
- **Visual Cues**: 
  - Hierarchical indentation
  - Expand/collapse arrow
  - Child files clearly associated with parent ZIP

**Step 6: Text Extraction Completes**
- **User Action**: Wait for all files to finish extraction
- **System Response**: 
  - Status changes to "Done" or "Ready"
  - Checkmark icon appears
  - Text length displayed (e.g., "45,230 characters")
- **UI Elements Visible**: 
  - All files showing success status
  - Green checkmark icons
  - Status: "Done" or "Ready"
  - Character counts for each file
  - No more loading spinners
  - Total file count: "5 files ready"
- **Visual Cues**: 
  - Green checkmarks
  - Completed status color
  - All animations stopped

**Step 7: Review Uploaded Files**
- **User Action**: Review file list to ensure all intended files are present and successfully extracted
- **System Response**: Complete file list displayed
- **UI Elements Visible**: 
  - Table showing all files
  - Success indicators
  - File sizes
  - Character counts
  - Action buttons (delete) for each file
- **Visual Cues**: 
  - Clean table layout
  - All green/success indicators

**Step 8: Optional - Handle Failed Files**
- **User Action**: If any files show error status, address them
- **System Response**: Error details shown for failed files
- **UI Elements Visible**: 
  - Failed file with red X icon
  - Error message: "Extraction failed" or specific reason
  - "Retry" button next to failed file
  - "Remove" button to delete failed file
- **Visual Cues**: 
  - Red error indicators
  - Clear error messages
- **Note**: See Error States section for recovery steps

**Step 9: Optional - Remove Unwanted Files**
- **User Action**: Click "Remove" or delete icon on any file to remove it from the job
- **System Response**: 
  - Confirmation may appear
  - File removed from list
  - File count updates
- **UI Elements Visible**: 
  - Updated file list without removed file
  - Updated file count
- **Visual Cues**: Smooth removal animation

**Step 10: Optional - Add More Files**
- **User Action**: Click "Choose Files" again or drag additional files to upload more
- **System Response**: New files added to existing list
- **UI Elements Visible**: 
  - Additional files appear in table
  - New files go through same upload/extraction process
  - File count increases
- **Visual Cues**: New files appear at bottom of list

**Final Step: Files Ready for Processing**
- **Success Indicator**: 
  - All files show "Done" or "Ready" status
  - No error indicators
  - Character counts visible for all files
  - Can proceed to next job creation step
- **System State Change**: 
  - Files uploaded to temporary storage
  - Text extracted and cached
  - Files ready for chunking/blockify stage
  - File metadata stored in job configuration
- **Next Possible Actions**: 
  - Proceed to configure chunk settings
  - Add more files if needed
  - Remove files if uploaded incorrectly
  - Continue with job creation workflow
  - Start processing job

---

## Alternative Paths & Strategies

### Strategy A: Drag and Drop Entire Folder
**When to use**: User has files organized in folder

**Steps**:
1. Open file manager, navigate to folder
2. Select all files in folder (Ctrl+A or Cmd+A)
3. Drag selected files to upload dropzone
4. All files upload simultaneously
5. Faster than selecting individually

### Strategy B: Upload ZIP Archive
**When to use**: Many files to upload or files already in ZIP

**Steps**:
1. Create ZIP archive of all documents on computer
2. Upload single ZIP file
3. System automatically extracts all files
4. Each file processes individually
5. Saves time vs. selecting many individual files

### Strategy C: Incremental Upload
**When to use**: Organizing files as you find them

**Steps**:
1. Upload initial batch of files
2. While those extract, locate more files on computer
3. Upload second batch
4. Repeat until all files uploaded
5. Allows parallel work while waiting for extraction

### Strategy D: Upload and Remove Workflow
**When to use**: Quickly uploading batch, then curating

**Steps**:
1. Select and upload large batch of files
2. Wait for all to extract
3. Review results
4. Remove files that didn't extract well or aren't needed
5. Keeps only good files for processing

---

## Error States & Recovery

### Error 1: File Type Not Supported
**Cause**: Uploaded file format not in supported list  
**User Experience**: 
- Error message: "Unsupported file type" or "File format not supported"
- File shows error status in table
- Cannot extract text from file

**Recovery Steps**:
1. Remove unsupported file from list
2. Convert file to supported format (PDF, DOCX, TXT, CSV)
3. Re-upload converted file
4. Or manually copy text from file and save as TXT

**QA Note**: File type validation should occur before upload. If upload accepts then fails, indicates validation gap.

### Error 2: PDF Text Extraction Fails
**Cause**: PDF is image-based (scanned) or has protection/encryption  
**User Experience**: 
- Error: "No text found in PDF" or "PDF extraction failed"
- File status shows error
- Character count is 0 or extraction failed

**Recovery Steps**:
1. Verify PDF contains actual text (not just images)
2. If scanned PDF, use OCR software to convert to text-based PDF
3. Or manually extract text and save as TXT file
4. If encrypted, remove encryption before uploading
5. Remove and re-upload corrected file

### Error 3: File Too Large
**Cause**: File exceeds maximum upload size  
**User Experience**: 
- Error: "File too large" or "Exceeds maximum size"
- Upload fails or stalls
- File not added to list

**Recovery Steps**:
1. Split large file into smaller sections
2. Or compress file (though may reduce quality)
3. Check if file can be optimized (e.g., remove embedded images from DOCX)
4. Upload sections as separate files

### Error 4: Network/Upload Interruption
**Cause**: Upload interrupted before completion  
**User Experience**: 
- File stuck at "Uploading..."
- Status doesn't change
- May show timeout error eventually

**Recovery Steps**:
1. Wait a moment (may just be slow)
2. Click "Retry" if button appears
3. Remove file and re-upload
4. Check file isn't corrupted
5. Verify sufficient disk space

### Error 5: Corrupted File
**Cause**: File is damaged or incomplete  
**User Experience**: 
- Extraction fails with error
- Message: "File corrupted" or "Cannot read file"
- Status shows error state

**Recovery Steps**:
1. Try opening file on computer in native application (e.g., Adobe Reader for PDF)
2. If file won't open, it's corrupted
3. Obtain fresh copy of file
4. Remove corrupted file from list
5. Upload working copy

### Error 6: ZIP Extraction Fails
**Cause**: ZIP is corrupted, password-protected, or too large  
**User Experience**: 
- Error: "Failed to extract ZIP" or "ZIP processing failed"
- Child files don't appear
- ZIP shows error status

**Recovery Steps**:
1. Verify ZIP is not password-protected
2. Test ZIP by extracting on computer
3. If corrupted, recreate ZIP from source files
4. If too large, split into smaller ZIP files
5. Or extract manually and upload individual files

### Error 7: Special Characters in Filename
**Cause**: Filename contains characters that cause filesystem issues  
**User Experience**: 
- May upload but show warning
- Filename sanitized automatically (special chars removed/replaced)
- File works but name changed

**Recovery Steps**:
1. Accept sanitized filename
2. Or rename file on computer before uploading to control final name
3. Avoid characters like: / \ : * ? " < > |

**QA Note**: System should sanitize filenames automatically. This is handled behavior, not error requiring recovery.

---

## Pain Points & Friction

**Identified Issues**:

1. **No Bulk Progress Indicator**
   - **Impact**: When uploading many files, can't see overall progress easily
   - **Frequency**: Jobs with 10+ files
   - **Potential Improvement**: 
     - Overall progress bar: "15 of 20 files extracted"
     - Summary status at top
     - Completion percentage for all files

2. **Cannot Reorder Files**
   - **Impact**: Files appear in upload order; can't organize after uploading
   - **Frequency**: Users wanting specific processing order
   - **Potential Improvement**: 
     - Drag-to-reorder in file list
     - Sort options (name, size, date)
     - Number/priority assignment

3. **No File Preview or Content Verification**
   - **Impact**: Can't verify correct file uploaded until viewing results
   - **Frequency**: Users with similar filenames
   - **Potential Improvement**: 
     - Show first few lines of extracted text
     - Preview button to view full extracted text
     - Thumbnail for PDFs
     - Content summary

4. **Retry Process Not Obvious**
   - **Impact**: Users may remove and re-upload failed files instead of retrying
   - **Frequency**: When files fail extraction
   - **Potential Improvement**: 
     - Make retry button more prominent
     - Auto-retry once before showing error
     - Explain retry vs. re-upload

5. **Unclear Why Extraction Takes Long**
   - **Impact**: Users uncertain if system working or stuck during multi-minute extractions
   - **Frequency**: Large or complex files (especially PDFs)
   - **Potential Improvement**: 
     - Show extraction progress (page 5 of 50)
     - Explain factors affecting speed
     - Show system is working (animated indicator)

6. **Cannot Edit Filenames After Upload**
   - **Impact**: If filename isn't descriptive, stuck with it
   - **Frequency**: Files with generic names like "document1.pdf"
   - **Potential Improvement**: 
     - Allow renaming files in list
     - Show original filename and allow custom display name
     - Auto-suggest better names based on content

---

## Design Considerations

**Following Contextual Design Principles**:

1. **Automation Opportunities**: 
   - Auto-extract text immediately upon upload
   - Auto-expand ZIP files without user action
   - Auto-retry failed extractions once
   - Auto-remove files with zero text content with confirmation

2. **Simplification Opportunities**: 
   - Single action for upload and extraction (no separate steps)
   - Drag-and-drop as primary method (simpler than file browser)
   - Auto-accept all supported formats without confirmation
   - Hide technical extraction details

3. **Transition Smoothness**: 
   - Smooth upload-to-extraction flow
   - No interruptions between upload and extraction
   - Natural progression to next job creation step
   - Easy to add more files without disruption

4. **User Trust**: 
   - Clear status for each file
   - Transparent extraction process
   - Success confirmation for each file
   - Retry option builds confidence
   - Character count proves text was extracted

5. **Cognitive Load**: 
   - Don't require understanding of file formats or extraction
   - Clear visual indicators of status
   - Simple drag-drop interaction
   - Automated handling of complex formats (ZIP, DOCX)

---

## Related Flows

- [Create New Blockify Job](./create-blockify-job.md) - Parent workflow
- [Create Basic Chunking Job](./create-chunking-job.md) - Alternative job type
- [Configure Basic Chunk Settings](./configure-basic-chunks.md) - Next step after upload
- [Configure Advanced Chunk Settings with Preview](./configure-advanced-chunks.md) - See how files will be chunked
- [View Job Details Dashboard](../06-job-management/view-job-details.md) - Monitor uploaded files processing

---

## Technical References

**Knowledge Base Sections**:
- src/components/blockify-corpus/file-upload-section.js - Upload interface
- src/components/blockify-corpus/file-upload-table.js - File list display
- src/handlers/upload/upload-handler.js - File processing
- src/handlers/upload/extract-utils.js - Text extraction
- src/utils/filename-sanitizer.js - Filename cleaning

**Key Components**:
- Drag-and-drop upload area
- File list table with status tracking
- Multi-format text extraction
- ZIP expansion handling
- Retry mechanism for failed uploads

---

## Version History

| Date | Version | Author | Changes |
|------|---------|--------|---------|
| 2025-10-04 | 1.1 | [Iternal Technologies](https://iternal.ai/airgapai) | Initial comprehensive documentation |

---

## Notes

**Important Considerations**:
- Text extraction happens automatically after upload; no separate action needed
- ZIP files are expanded automatically; each contained file appears as separate entry
- Filenames are automatically sanitized (special characters removed) for filesystem compatibility
- Original files remain on your computer; application creates copies
- Maximum file sizes may vary by system configuration
- Scanned PDFs (image-only) will fail text extraction; must OCR first

**Supported File Formats**:
- **PDF**: Adobe Acrobat documents (text-based only, not scanned images)
- **DOCX/DOC**: Microsoft Word documents
- **TXT**: Plain text files
- **CSV**: Comma-separated values (text extracted as single block)
- **ZIP**: Archives containing any of the above formats

**Text Extraction Details**:
- PDF extraction preserves basic structure and paragraphs
- DOCX extraction includes body text (may exclude headers/footers)
- Text files loaded as-is
- Special characters and formatting largely preserved
- Extraction may take seconds to minutes depending on file complexity

**Best Practices**:
- Use descriptive filenames before uploading for easier identification
- Test extraction on sample file first if unsure about format compatibility
- Organize files in ZIP if uploading many related documents
- Remove unnecessary files before creating ZIP to avoid extra processing
- Keep individual files under 50MB for optimal processing
- Use text-based PDFs, not scanned images

**Common User Questions**:
- "Why is extraction taking so long?" - Large PDFs or complex DOCX files take time to process
- "Can I upload images?" - No, images contain no extractable text
- "What happens to formatting?" - Basic structure preserved, but complex formatting may be lost
- "Can I upload the same file twice?" - Yes, but creates duplicates; better to remove and re-upload if needed
- "What if extraction finds no text?" - File shows error; likely image-based PDF or empty file
- "Do I need to wait for all files before continuing?" - Can proceed once essential files are ready, add more later if needed

