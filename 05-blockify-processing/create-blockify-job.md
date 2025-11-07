# Create New Blockify Job

## Overview
**Flow ID**: `create-blockify-job`  
**Category**: Blockify Processing  
**Estimated Duration**: 5-15 minutes (setup); processing time varies by document size  
**User Role**: All Users  
**Complexity**: Complex  

**Purpose**: This flow enables users to process documents using AI to break them down into structured "IdeaBlocks" - meaningful chunks of information with names, critical questions, and trusted answers. This structured format makes documents more searchable and useful for AI-powered conversations. The process creates a searchable dataset from your documents.

---

## Trigger

**What initiates this flow:**
- [x] User manually initiates


**Specific trigger**: User wants to transform unstructured documents into a structured, searchable dataset, typically because:
- They have documents they want to query during AI conversations
- They need to make technical documentation more accessible
- They want to create a knowledge base from existing files
- They're preparing documents for semantic search
- They want AI-enhanced structure rather than simple chunking

---

## Prerequisites

**Before starting, users must have:**
- [x] Application installed and running
- [x] Blockify AI model uploaded and available
- [x] Embedding model uploaded and available (for creating the searchable dataset)
- [x] Document files ready to upload (PDF, DOCX, TXT, CSV, or ZIP containing these)
- [x] Understanding that processing may take 10 minutes to several hours depending on document size
- [x] Sufficient disk space for processed results

---

## User Intent Analysis

### Primary Intent
Convert raw documents into a structured, AI-searchable dataset where information is organized into meaningful blocks with clear questions and answers, enabling precise information retrieval during conversations.

### Secondary Intents
- Organize knowledge for easy AI-powered retrieval
- Improve the quality of AI responses by providing structured context
- Make large document collections more manageable and searchable
- Create a permanent knowledge base from temporary documents
- Extract key information and concepts from documents automatically

### Subintents
- Ensure documents are processed accurately
- Preview how documents will be chunked before processing
- Configure processing parameters for optimal results
- Monitor processing progress
- Verify results after processing completes

---

## Step-by-Step Flow

### Main Path

**Step 1: Navigate to Blockify Page**
- **User Action**: Click "Blockify" in the main navigation menu
- **System Response**: Blockify page loads
- **UI Elements Visible**: 
  - Navigation menu with "Blockify" highlighted
  - Mode selection or welcome screen
  - Two options: "Blockify" and "Chunk Only" (typically as buttons or tabs)
  - Description text explaining each option
- **Visual Cues**: Clean interface with clear choice between two processing modes

**Step 2: Select Blockify Mode**
- **User Action**: Click "Blockify" option to use AI-enhanced processing
- **System Response**: Blockify job creation interface loads
- **UI Elements Visible**: 
  - Page header showing "Blockify Mode" or similar
  - Back button to return to mode selection
  - Multi-step form interface
  - Step indicators or progress markers
- **Visual Cues**: Blockify option is highlighted/selected, interface changes to show job setup
- **Note**: Alternative is "Chunk Only" mode - see create-chunking-job.md for that flow

**Step 3: Configure Target Dataset**
- **User Action**: In the dataset configuration section, either select existing dataset or choose "Create New Dataset"
- **System Response**: Form updates based on selection
- **UI Elements Visible**: 
  - "Target Dataset" dropdown showing:
    - "Create New Dataset" option at top
    - List of existing datasets (if any)
  - If "Create New" selected:
    - Text input field for "Dataset Name" appears
    - Embedding model selector appears (if not locked to existing dataset's model)
  - If existing dataset selected:
    - Dataset name shown (read-only)
    - Embedding model auto-populated from dataset (locked)
  - Optional: Schedule job picker (calendar icon)
- **Visual Cues**: 
  - Form sections appear/disappear based on selections
  - Required fields may have asterisks
  - Active field has focus indicator

**Step 4: Name New Dataset (if creating new)**
- **User Action**: If creating new dataset, type a descriptive name in the Dataset Name field
- **System Response**: Text appears as typed
- **UI Elements Visible**: 
  - Text input with dataset name
  - Optional: Character count or validation messages
  - Embedding model selector (enabled for new dataset)
- **Visual Cues**: 
  - Active text field
  - Name should be descriptive for future reference
- **Note**: Skip this step if using existing dataset

**Step 5: Select Embedding Model**
- **User Action**: Choose embedding model from dropdown (if creating new dataset; otherwise auto-selected)
- **System Response**: Selected model is displayed
- **UI Elements Visible**: 
  - Embedding model dropdown with list of available models
  - Model names and types
  - Currently selected model highlighted
- **Visual Cues**: Selected model appears in field
- **Note**: Embedding model must match if adding to existing dataset

**Step 6: Upload Documents**
- **User Action**: Click "Upload Files" button or drag files into upload area
- **System Response**: File selection dialog opens OR files are accepted via drag-drop
- **UI Elements Visible**: 
  - File upload area (may be a dropzone with dashed border)
  - "Choose Files" or "Upload Files" button
  - Supported file types indicator (PDF, DOCX, TXT, CSV, ZIP)
  - List of uploaded files appears on right side as files are added
- **Visual Cues**: 
  - Dropzone may highlight when files are dragged over it
  - Upload icon (paperclip or cloud upload)

**Step 7: Select Files from Computer**
- **User Action**: In file browser, navigate to and select one or more document files, then click "Open"
- **System Response**: 
  - File browser closes
  - Files begin uploading and extracting
  - File table appears showing upload progress
- **UI Elements Visible**: 
  - File table on right side with columns: Filename, Status, Size, Actions
  - Each file shows progress (uploading → extracting text → ready)
  - Progress indicators or status icons for each file
  - File count: "X files uploaded"
- **Visual Cues**: 
  - Animated spinners during upload/extraction
  - Checkmarks when files are ready
  - File size displayed
  - Status changes from "Uploading" → "Extracting" → "Ready"

**Step 8: Wait for Text Extraction**
- **User Action**: Watch progress as system extracts text from uploaded files
- **System Response**: 
  - Each file processed automatically
  - PDF text extracted
  - DOCX converted to text
  - ZIP files expanded and each file within processed
  - Text length calculated
- **UI Elements Visible**: 
  - Status column updates for each file
  - Time estimates may appear
  - Progress indicators
  - Error messages if any file fails
- **Visual Cues**: 
  - Animated progress indicators
  - Status icons: loading spinner → checkmark (success) or X (error)
  - Color coding: blue/gray (processing), green (success), red (error)

**Step 9: Review Chunk Settings (Basic)**
- **User Action**: Review or adjust the chunk size and overlap settings shown
- **System Response**: Settings are displayed with current values
- **UI Elements Visible**: 
  - "Chunk Settings" section
  - Slider for chunk size (e.g., 500-3000 characters)
  - Checkbox for "Allow Overlap"
  - Slider for overlap size (if enabled, e.g., 0-500 characters)
  - Current value displayed next to sliders
  - "Show Advanced Settings" button or toggle
- **Visual Cues**: 
  - Sliders show current value
  - Range indicators show min/max
  - Overlap controls disabled/grayed if overlap checkbox unchecked

**Step 10: Optional - View Advanced Chunk Preview**
- **User Action**: Click "Show Advanced Settings" or toggle to see per-file chunk preview
- **System Response**: Interface expands to show advanced chunk configuration
- **UI Elements Visible**: 
  - Advanced settings panel expands
  - File tabs showing each uploaded file
  - For selected file:
    - Chunk preview area showing how file will be split
    - Each chunk displayed in numbered boxes (Chunk #1, Chunk #2, etc.)
    - Character count for each chunk
    - Overlap visualization (if enabled)
  - More detailed chunk size and overlap sliders
  - Real-time preview updates as settings change
- **Visual Cues**: 
  - Expandable section with smooth animation
  - Chunks clearly separated in preview
  - Chunk numbers and sizes visible
  - Can click between file tabs to preview each
- **Note**: See configure-advanced-chunks.md for detailed flow on this feature

**Step 11: Adjust Chunk Parameters (if needed)**
- **User Action**: Optionally adjust chunk size or overlap by moving sliders
- **System Response**: 
  - Slider values update in real-time
  - Preview (if in advanced mode) updates to show new chunking
  - Chunk count changes based on new settings
- **UI Elements Visible**: 
  - Sliders at new positions
  - Updated chunk previews
  - New chunk counts per file
- **Visual Cues**: 
  - Smooth slider movement
  - Instant preview updates (with brief delay for calculations)
  - Visual feedback when settings change

**Step 12: Optional - Schedule Job**
- **User Action**: If wanting to run job later, click schedule job picker (calendar icon)
- **System Response**: Date/time picker appears
- **UI Elements Visible**: 
  - Calendar picker interface
  - Time selection
  - "Schedule" and "Cancel" buttons
- **Visual Cues**: Calendar overlay
- **Note**: See schedule-job.md for detailed flow; skip this step to run immediately

**Step 13: Review Configuration Summary**
- **User Action**: Review all settings before starting
- **System Response**: Summary information visible
- **UI Elements Visible**: 
  - Dataset name (new or existing)
  - Embedding model name
  - Number of files uploaded
  - Total file size
  - Chunk settings summary
  - Schedule time (if scheduled)
  - "Start Blockify" or "Create Job" button (prominent, often blue)
- **Visual Cues**: 
  - Summary information clearly laid out
  - Button enabled if all required fields complete
  - Button disabled/grayed if missing requirements

**Step 14: Start Blockify Job**
- **User Action**: Click "Start Blockify" or "Blockify Documents" button
- **System Response**: 
  - Job is created
  - Files are uploaded to job directory
  - System begins processing
  - User is redirected to job details page
- **UI Elements Visible**: 
  - Brief loading indicator
  - Transition animation
  - Job details dashboard loads
- **Visual Cues**: 
  - Loading spinner briefly
  - Smooth page transition
  - Success confirmation may flash

**Step 15: Job Details Page Loads**
- **User Action**: Observe the job details dashboard
- **System Response**: Comprehensive job monitoring interface displays
- **UI Elements Visible**: 
  - Page header with job name
  - Breadcrumb navigation (Home > Blockify > Job Details)
  - Job status badge (Processing, Active, etc.)
  - Progress timeline showing stages:
    1. Text Extraction
    2. Blockify Processing (AI structuring)
    3. Embedding Generation
    4. Dataset Creation
  - Progress bar showing overall completion percentage
  - Estimated time remaining
  - File processing status table
  - Metrics cards showing statistics
  - Real-time charts (if data available)
- **Visual Cues**: 
  - Animated progress indicators
  - Color-coded status badges
  - Live-updating statistics
  - Progress bar filling

**Step 16: Monitor Processing Progress**
- **User Action**: Watch as job progresses through stages (can navigate away and return later)
- **System Response**: 
  - Page updates in real-time (or near real-time)
  - Progress bar advances
  - Metrics update (e.g., "15 of 50 chunks processed")
  - Charts populate with performance data
  - Estimated time remaining updates
- **UI Elements Visible**: 
  - Progress percentage (e.g., "35% Complete")
  - Current stage indicator (e.g., "Processing: Blockify Stage")
  - Rate indicator (e.g., "Processing 2.5 chunks/minute")
  - File status table showing which files are complete
  - Active processing indicators
- **Visual Cues**: 
  - Animated progress bars
  - Live-updating numbers
  - Pulsing status indicators on active items
  - Color changes as stages complete

**Step 17: Processing Completes**
- **User Action**: Wait for all stages to complete (may take minutes to hours)
- **System Response**: 
  - All four stages reach 100%
  - Job status changes to "Completed"
  - Dataset is created and available
  - Final statistics are displayed
- **UI Elements Visible**: 
  - Status badge shows "Completed" in green
  - Progress timeline shows all stages complete (green checkmarks)
  - Final metrics: Total items created, total processing time
  - "View Dataset" button
  - "Download Report" button
  - "Close" or "Return to Jobs" button
- **Visual Cues**: 
  - Green color scheme for completed status
  - Checkmark icons
  - Celebration or completion animation may appear
  - No more progress indicators animating

**Final Step: Job Complete - Dataset Ready**
- **Success Indicator**: 
  - Job status shows "Completed"
  - 100% progress across all stages
  - Dataset appears in datasets list
  - Can view dataset contents
  - Dataset can be activated for chat queries
- **System State Change**: 
  - New dataset created in system (or existing dataset updated)
  - Document files stored in job directory
  - Structured blocks stored in database
  - Embeddings generated and stored
  - Dataset available for AI conversations
  - Job appears in completed jobs list
- **Next Possible Actions**: 
  - View the created dataset (click "View Dataset" button)
  - Download processing report
  - Activate dataset for chat queries (in Settings or Datasets page)
  - Start new chat using this dataset
  - Create another blockify job with different documents
  - View detailed analytics on job details page

---

## Alternative Paths & Strategies

### Strategy A: Add to Existing Dataset
**When to use**: User wants to expand an existing dataset with new documents rather than create a new one

**Steps**:
1. Navigate to Blockify page, select Blockify mode
2. In dataset configuration, select existing dataset from dropdown (not "Create New")
3. Embedding model auto-selects from dataset (cannot change)
4. Upload new document files
5. Configure chunk settings
6. Start job
7. New documents are added to existing dataset, expanding it

### Strategy B: Schedule for Later Processing
**When to use**: User wants to set up job but run it during off-hours or at specific time

**Steps**:
1. Complete normal setup (steps 1-12)
2. Click schedule job picker
3. Select future date and time
4. Confirm schedule
5. Click "Create Job" (button may say "Schedule Job")
6. Job is created but won't start until scheduled time
7. User can close application; job will run when time arrives if app is open

### Strategy C: Test with Single File First
**When to use**: User wants to verify settings before processing entire document collection

**Steps**:
1. Start blockify job setup
2. Upload only one representative file
3. Use advanced preview to see how it will be chunked
4. Adjust settings until chunking looks good
5. Note the settings used
6. Cancel or complete this test job
7. Start new job with all files using proven settings

### Strategy D: Upload ZIP of Documents
**When to use**: User has many files organized in a ZIP archive

**Steps**:
1. Navigate to blockify setup
2. Select ZIP file instead of individual documents
3. System automatically extracts ZIP
4. Each file within ZIP appears separately in file list
5. All files processed individually
6. Can expand ZIP entry to see contained files
7. Continue with normal configuration

---

## Error States & Recovery

### Error 1: No Blockify Model Available
**Cause**: No blockify model has been uploaded  
**User Experience**: 
- Error banner appears: "Blockify model required"
- Cannot proceed with blockify job
- May be redirected to settings or given upload option

**Recovery Steps**:
1. Navigate to Settings > Chat AI Models or Models tab
2. Upload a blockify-capable model (typically Llama-based models)
3. Wait for model to load
4. Return to Blockify page and try again

### Error 2: No Embedding Model Available
**Cause**: No embedding model configured (required for creating searchable dataset)  
**User Experience**: 
- Error message: "Embedding model required"
- Cannot select embedding model in dropdown
- Cannot proceed to final step

**Recovery Steps**:
1. Navigate to Settings
2. Upload an embedding model (e.g., Jina Embeddings)
3. Select it as active embedding model if needed
4. Return to blockify job setup
5. Embedding model should now be selectable

### Error 3: File Upload/Extraction Fails
**Cause**: File is corrupted, incompatible format, or system error during extraction  
**User Experience**: 
- File shows error status in file table (red X icon)
- Error message next to filename: "Extraction failed" or "Unsupported format"
- File cannot be processed

**Recovery Steps**:
1. Click "Retry" button next to failed file (if available)
2. If retry fails, click "Remove" to delete failed file
3. Verify file is not corrupted (try opening in native application)
4. Convert file to compatible format if needed
5. Re-upload corrected file
6. Continue with remaining files

### Error 4: ZIP File Too Large or Corrupted
**Cause**: ZIP archive exceeds size limits or has corruption  
**User Experience**: 
- Error message: "Failed to extract ZIP" or "File too large"
- ZIP contents may not appear in file list

**Recovery Steps**:
1. Remove failed ZIP file
2. Extract ZIP manually on your computer
3. Upload individual files instead of ZIP
4. Or split ZIP into smaller archives and upload separately
5. Or fix ZIP corruption using file repair tools

### Error 5: Insufficient Disk Space
**Cause**: Not enough space to store processed results  
**User Experience**: 
- Error during job creation or processing
- Message: "Insufficient disk space" or similar
- Job may fail to start or stop mid-processing

**Recovery Steps**:
1. Free up disk space by deleting unnecessary files
2. Delete old completed jobs if no longer needed
3. Remove unused datasets or models
4. Consider processing fewer files at once
5. Try creating job again after freeing space

### Error 6: Invalid Dataset Name
**Cause**: Dataset name contains invalid characters or already exists  
**User Experience**: 
- Error message below dataset name field: "Invalid characters" or "Name already exists"
- Cannot proceed to next step
- Field may have red border

**Recovery Steps**:
1. Edit dataset name to remove special characters
2. Use alphanumeric characters, spaces, hyphens, underscores
3. Make name unique if conflict exists
4. Common fix: remove / \ : * ? " < > | characters

### Error 7: Job Creation Fails
**Cause**: Backend error creating job record or initializing job directory  
**User Experience**: 
- Error message after clicking "Start Blockify"
- User not redirected to job details
- Job does not appear in jobs list

**Recovery Steps**:
1. Check console for error details
2. Verify all required fields are completed
3. Try clicking "Start Blockify" again
4. If persists, refresh page and restart setup
5. Check system logs or restart application

---

## Pain Points & Friction

**Identified Issues**:

1. **Unclear Processing Time Expectations**
   - **Impact**: Users don't know if job will take 10 minutes or 10 hours
   - **Frequency**: Every new job
   - **Potential Improvement**: 
     - Estimate processing time based on file sizes before starting
     - Show comparison: "Similar jobs took X minutes"
     - Break down estimated time by stage

2. **Cannot Preview Blockify Results Before Processing**
   - **Impact**: Users commit to long processing without knowing if results will be useful
   - **Frequency**: First-time users and new document types
   - **Potential Improvement**: 
     - Add "Test on Sample" option to preview results on small section
     - Show example blockify output format
     - Provide sample results from similar documents

3. **Chunk Settings Require Understanding of Technical Details**
   - **Impact**: Users don't know what chunk size or overlap values to use
   - **Frequency**: Every new job, especially for first-time users
   - **Potential Improvement**: 
     - Provide "Recommended" presets based on document types
     - Explain what each setting does in simpler terms
     - Add tooltips with guidance

4. **No Guidance on Dataset Naming**
   - **Impact**: Users may create poorly named datasets, hard to identify later
   - **Frequency**: Every new dataset creation
   - **Potential Improvement**: 
     - Suggest naming conventions
     - Show examples of good dataset names
     - Auto-suggest name based on uploaded files

5. **Cannot Pause or Resume Processing**
   - **Impact**: If user needs to stop processing, must cancel entire job and start over
   - **Frequency**: Long jobs that need interruption
   - **Potential Improvement**: 
     - Add pause/resume functionality
     - Save progress for later continuation
     - Allow job to continue after application restart

6. **Limited File Format Support Indication**
   - **Impact**: Users may upload unsupported formats without realizing
   - **Frequency**: Users with diverse file types
   - **Potential Improvement**: 
     - Clearly list supported formats in upload area
     - Validate format before upload
     - Suggest conversion tools for unsupported formats

7. **Multi-Step Process Feels Long**
   - **Impact**: Users may feel fatigued by configuration steps
   - **Frequency**: Every job creation
   - **Potential Improvement**: 
     - Add "Quick Start" option with defaults
     - Remember previous settings for next job
     - Reduce required steps where possible

---

## Design Considerations

**Following Contextual Design Principles**:

1. **Automation Opportunities**: 
   - Auto-select embedding model if only one available
   - Auto-suggest dataset name based on file names or content
   - Auto-detect optimal chunk size based on document structure
   - Auto-retry failed files without user intervention
   - Auto-start job if scheduled time arrives

2. **Simplification Opportunities**: 
   - Provide preset configurations for common document types
   - Combine dataset selection and naming into single step
   - Hide advanced settings by default
   - Use intelligent defaults that work for most cases
   - Eliminate intermediate confirmation steps

3. **Transition Smoothness**: 
   - Clear progression through setup steps
   - Smooth animation between steps
   - Natural flow from setup to monitoring
   - Easy to return to previous steps
   - Seamless transition to job details page

4. **User Trust**: 
   - Clear progress indicators at every stage
   - Transparent file processing status
   - Visible chunk previews build confidence
   - Real-time processing updates
   - Explicit success confirmation when complete

5. **Cognitive Load**: 
   - Don't require users to understand technical details of AI processing
   - Progressive disclosure (basic settings first, advanced optional)
   - Clear labels and descriptions for all options
   - Visual previews reduce uncertainty
   - Sensible defaults minimize decisions needed

---

## Related Flows

- [Create Basic Chunking Job](./create-chunking-job.md) - Simpler alternative without AI processing
- [Upload Files for Processing](./upload-files-to-job.md) - Detailed file upload flow
- [Configure Advanced Chunk Settings with Preview](./configure-advanced-chunks.md) - Detailed chunk configuration
- [View Job Details Dashboard](../06-job-management/view-job-details.md) - Monitor processing
- [Upload Embedding Model](../03-model-management/embedding-model-upload.md) - Add required model
- [Activate/Deactivate Dataset](../04-dataset-management/corpus-activation.md) - Use created dataset

---

## Technical References

**Knowledge Base Sections**:
- src/pages/blockify.js - Main blockify page
- src/components/blockify-corpus/new-job-screen.js - Job creation interface
- src/components/blockify-corpus/file-upload-section.js - File upload handling
- src/components/blockify-corpus/advanced-chunk-settings.js - Chunk configuration
- src/handlers/upload/upload-handler.js - File processing
- src/engines/blockify.js - AI processing engine

**Key Components**:
- Multi-step job creation wizard
- File upload with extraction
- Chunk settings with live preview
- Job monitoring dashboard with real-time updates

---

## Version History

| Date | Version | Author | Changes |
|------|---------|--------|---------|
| 2025-10-04 | 1.1 | [Iternal Technologies](https://iternal.ai/airgapai) | Initial comprehensive documentation |

---

## Notes

**Important Considerations**:
- Blockify processing uses AI to structure documents, which takes significantly longer than simple chunking
- Processing time scales with document size and complexity: roughly 30-60 seconds per 1000 characters
- The application must remain running during processing (or job will pause and resume when reopened)
- Results are stored permanently; datasets can be reused across conversations
- Chunk size affects both processing time and search quality (larger chunks = fewer chunks = faster but less precise)
- Blockify models require significant RAM (8GB+ recommended)

**Best Practices**:
- Start with smaller document collections to test settings
- Use meaningful dataset names that describe the content
- Review chunk previews before starting large jobs
- Schedule long jobs during times when computer won't be needed
- Keep related documents in the same dataset for better context
- Consider document structure when setting chunk size (e.g., PDFs with sections benefit from larger chunks)

**Common User Questions**:
- "How long will this take?" - Varies greatly; small documents (10 pages) may take 5-10 minutes, large collections can take hours
- "Can I use my computer while processing?" - Yes, but expect slower performance; avoid closing the application
- "What's the difference between Blockify and Chunk Only?" - Blockify uses AI to create structured blocks; Chunk Only simply splits text mechanically
- "Can I add more documents later?" - Yes, select the existing dataset and upload additional files
- "What if processing fails?" - You can retry the job; progress may be preserved depending on failure stage

