# Upload New Dataset

## Overview
**Flow ID**: `corpus-upload`  
**Category**: Dataset/Corpus Management  
**Estimated Duration**: 2-10 minutes (depending on file size)  
**User Role**: All Users  
**Complexity**: Simple  

**Purpose**: This flow allows users to upload a pre-processed dataset file (in JSONL format) to the application. These datasets contain structured information that can be queried during AI conversations, enabling the AI to provide answers based on your specific documents and data rather than just its general knowledge.

---

## Trigger

**What initiates this flow:**
- [x] User manually initiates


**Specific trigger**: User wants to add a new dataset for AI-powered querying, typically because:
- They have a pre-processed dataset file ready to use
- They want to add knowledge to the AI system
- They've received a dataset from another source
- They want to import previously exported data
- They're testing the dataset query feature

---

## Prerequisites

**Before starting, users must have:**
- [x] Application installed and running
- [x] Dataset file in JSONL format (each line is a JSON object with "text" and "vector" fields)
- [x] Embedding model available (dataset must have been created with the same embedding model)
- [x] Sufficient disk space for the dataset file
- [x] Knowledge of which embedding model was used to create the dataset

---

## User Intent Analysis

### Primary Intent
Import a structured dataset file into the application so it can be used for AI-powered question answering and information retrieval during conversations.

### Secondary Intents
- Make specific knowledge available to the AI
- Enable dataset query features
- Build a library of queryable datasets
- Restore previously exported datasets
- Share datasets between instances or users

### Subintents
- Ensure dataset is compatible with the application
- Associate dataset with correct embedding model
- Make dataset easily identifiable for future use
- Verify successful upload

---

## Step-by-Step Flow

### Main Path (Happy Path)

**Step 1: Navigate to Settings or Datasets**
- **User Action**: Click "Settings" in navigation, OR click "Datasets" if available as separate navigation item
- **System Response**: Settings page or Datasets page loads
- **UI Elements Visible**: 
  - Navigation menu with selected item highlighted
  - Page content area
  - If Settings: Multiple tabs across top
  - If Datasets: Dataset list view
- **Visual Cues**: Active navigation item highlighted

**Step 2: Access Dataset Upload Area**
- **User Action**: 
  - If in Settings: Look for dataset-related tab or section
  - If in Datasets page: Look for "Upload Dataset" or "Add Dataset" button
- **System Response**: Upload interface becomes available
- **UI Elements Visible**: 
  - "Upload Dataset" or "Add Dataset" button (typically prominent, may be blue)
  - Possibly: List of existing datasets shown
  - Instructions or helper text
- **Visual Cues**: Upload button stands out with color or icon

**Step 3: Initiate Dataset Upload**
- **User Action**: Click "Upload Dataset" or "Add Dataset" button
- **System Response**: Upload modal or form appears
- **UI Elements Visible**: 
  - Modal dialog overlaying current page
  - Title: "Upload Dataset" or similar
  - File upload area/button
  - Text input for "Dataset Name"
  - Dropdown or selector for "Embedding Model"
  - "Cancel" and "Upload" buttons
  - Close button (X) in corner
- **Visual Cues**: 
  - Modal centered on screen
  - Background slightly dimmed
  - Clear form structure

**Step 4: Select Dataset File**
- **User Action**: Click "Choose File" or file upload button
- **System Response**: Operating system file browser opens
- **UI Elements Visible**: 
  - Native file browser window
  - File navigation interface
  - File type filter (may show .jsonl files)
- **Visual Cues**: Standard OS file browser appearance

**Step 5: Navigate to and Select File**
- **User Action**: Browse to dataset file location, select the .jsonl file, click "Open"
- **System Response**: 
  - File browser closes
  - Modal reappears
  - Selected filename displayed
  - Dataset name may auto-populate from filename
- **UI Elements Visible**: 
  - Selected filename shown in upload area
  - Dataset name field populated (or ready for input)
  - Embedding model dropdown active
  - File size may be displayed
- **Visual Cues**: 
  - Filename visible confirms selection
  - Form appears complete or nearly complete

**Step 6: Enter or Confirm Dataset Name**
- **User Action**: Review auto-populated name or type a custom dataset name
- **System Response**: Text appears as typed
- **UI Elements Visible**: 
  - Text input field with dataset name
  - Cursor active in field if editing
  - Character count or validation (if applicable)
- **Visual Cues**: 
  - Active text field when clicked
  - Name should be descriptive

**Step 7: Select Embedding Model**
- **User Action**: Click embedding model dropdown and select the model that was used to create this dataset
- **System Response**: Dropdown expands showing available embedding models
- **UI Elements Visible**: 
  - Dropdown list of embedding models
  - Model names (e.g., "Jina Embeddings", "BGE-Small")
  - Currently selected model highlighted
- **Visual Cues**: 
  - Dropdown opens smoothly
  - Selected model appears in field when closed
- **Note**: Critical to select the correct model; mismatched models won't work properly

**Step 8: Confirm and Upload**
- **User Action**: Click "Upload" or "Save" button
- **System Response**: 
  - Upload begins
  - Progress indicator appears
  - File transfers to application
- **UI Elements Visible**: 
  - Progress bar (animated, filling left to right)
  - Percentage indicator (e.g., "Uploading... 35%")
  - Status text: "Uploading dataset..."
  - Cancel button may be disabled during upload
- **Visual Cues**: 
  - Animated progress bar
  - Percentage increases
  - May show upload speed or time remaining

**Step 9: Wait for Upload to Complete**
- **User Action**: Wait while file uploads (time varies by file size)
- **System Response**: 
  - Progress continues advancing
  - System validates file format
  - Dataset is registered in database
- **UI Elements Visible**: 
  - Continuing progress updates
  - Status may change to "Processing..." after upload completes
- **Visual Cues**: 
  - Smooth progress animation
  - System is working

**Step 10: Upload Completes Successfully**
- **User Action**: No action required
- **System Response**: 
  - Progress reaches 100%
  - Success message appears
  - Modal automatically closes OR shows success state with "Done" button
  - Returns to dataset list or settings page
- **UI Elements Visible**: 
  - Success message (green, with checkmark): "Dataset uploaded successfully!"
  - Dataset now appears in datasets list
  - Dataset entry shows: Name, embedding model, size, date
- **Visual Cues**: 
  - Green color indicates success
  - Checkmark icon
  - Smooth transition back to main view

**Step 11: Verify Dataset in List**
- **User Action**: Look for newly uploaded dataset in the list
- **System Response**: Dataset list displays with new entry
- **UI Elements Visible**: 
  - Dataset list or table showing all datasets
  - New dataset entry with:
    - Dataset name
    - Embedding model name
    - File size
    - Upload date/time
    - Status indicator (may show "Ready" or "Inactive")
    - Action buttons (Activate, View, Download, Delete)
- **Visual Cues**: 
  - New dataset may be highlighted or positioned at top
  - Clear dataset information displayed

**Final Step: Dataset Available for Use**
- **Success Indicator**: 
  - Dataset appears in datasets list
  - No error messages
  - Dataset can be activated
  - Dataset shows correct embedding model
- **System State Change**: 
  - Dataset file stored in application's data directory
  - Dataset registered in database
  - Dataset available for selection in chat settings
  - Dataset can be activated for use in conversations
- **Next Possible Actions**: 
  - Activate this dataset for use in chat (see corpus-activation.md)
  - View dataset contents to verify data
  - Upload additional datasets
  - Return to chat and enable dataset query
  - Export or manage existing datasets

---

## Alternative Paths & Strategies

### Strategy A: Drag and Drop Upload
**When to use**: If modal supports drag-and-drop file selection

**Steps**:
1. Open upload modal (Steps 1-3)
2. Instead of clicking "Choose File", open file browser separately
3. Drag dataset file from file browser to upload modal
4. Drop file in designated area
5. Filename appears, continue from Step 6

### Strategy B: Upload from Datasets List Page
**When to use**: If dedicated Datasets page exists with direct upload

**Steps**:
1. Navigate directly to Datasets page (not through Settings)
2. Click "Upload" or "+" button in datasets view
3. Upload modal or inline form appears
4. Continue with Steps 4-11

### Strategy C: Replace Existing Dataset
**When to use**: User wants to update an existing dataset with new version

**Steps**:
1. Navigate to dataset list
2. Find existing dataset to replace
3. Click "Delete" or "Remove" on old dataset
4. Confirm deletion
5. Follow main path to upload new version with same name

### Strategy D: Batch Upload Multiple Datasets
**When to use**: User has several dataset files to upload

**Steps**:
1. Upload first dataset (full main path)
2. When modal closes, immediately click "Upload Dataset" again
3. Select second dataset file
4. Repeat for each dataset
5. All datasets appear in list

**QA Note**: Current interface may require separate uploads. True batch upload not confirmed in knowledge base.

---

## Error States & Recovery

### Error 1: Invalid File Format
**Cause**: File is not in JSONL format or has incorrect structure  
**User Experience**: 
- Error message after upload: "Invalid file format" or "File must be JSONL"
- Upload fails
- May indicate specific format issue

**Recovery Steps**:
1. Verify file is .jsonl format
2. Open file in text editor to check structure
3. Each line should be valid JSON with "text" and "vector" fields
4. Vectors should be arrays of numbers
5. Fix file format or regenerate from source
6. Try uploading again

### Error 2: Embedding Model Not Available
**Cause**: Selected embedding model doesn't exist or isn't loaded  
**User Experience**: 
- Error message: "Embedding model not found" or similar
- Cannot complete upload
- Dropdown may show no models

**Recovery Steps**:
1. Cancel upload
2. Navigate to Settings > Models
3. Upload the embedding model that was used to create this dataset
4. Return to dataset upload
5. Select newly uploaded embedding model
6. Complete upload

### Error 3: Embedding Model Mismatch
**Cause**: Dataset created with different embedding model than selected  
**User Experience**: 
- Upload may succeed but dataset won't work properly
- Search results will be poor or nonsensical
- May not show error immediately (discovered during use)

**Recovery Steps**:
1. Delete incorrectly associated dataset
2. Determine which embedding model was used to create dataset (check documentation)
3. Upload correct embedding model if not available
4. Re-upload dataset with correct embedding model selected

**QA Note**: System may not validate embedding model compatibility at upload time. User discovers issue during use.

### Error 4: Insufficient Disk Space
**Cause**: Not enough free disk space for dataset file  
**User Experience**: 
- Error during upload: "Insufficient disk space" or "Upload failed"
- Progress may stop partway
- Upload does not complete

**Recovery Steps**:
1. Free up disk space (delete old files, datasets, or models)
2. Check dataset file size before uploading
3. Ensure adequate free space (at least 2x file size recommended)
4. Try upload again after freeing space

### Error 5: Dataset Name Already Exists
**Cause**: Another dataset with the same name already exists  
**User Experience**: 
- Error message: "Dataset name already exists" or "Name must be unique"
- Cannot save
- Upload process stops

**Recovery Steps**:
1. Change dataset name to something unique
2. Add version number or date (e.g., "TechDocs-v2" or "TechDocs-2025-01")
3. Or delete/rename existing dataset with conflicting name
4. Complete upload with unique name

### Error 6: File Too Large
**Cause**: Dataset file exceeds maximum size limit  
**User Experience**: 
- Error message: "File too large" or "Exceeds maximum size"
- Upload rejected before starting or fails partway
- May indicate size limit

**Recovery Steps**:
1. Check file size and system limits
2. Split dataset into smaller chunks if possible
3. Remove less important entries from dataset
4. Or upgrade system resources if datasets are legitimately large

**QA Note**: Practical limit depends on system RAM and disk space, not hard-coded limit.

### Error 7: Corrupted File
**Cause**: File is damaged or incomplete  
**User Experience**: 
- Error during processing: "File corrupted" or "Invalid data"
- Upload may complete but validation fails
- Cannot use dataset

**Recovery Steps**:
1. Verify file integrity (check file size matches expected)
2. Re-download or re-export file from source
3. Try uploading new copy
4. If file consistently fails, may need to regenerate from original data

---

## Pain Points & Friction

**Identified Issues**:

1. **No File Validation Before Upload**
   - **Impact**: Users may upload large files only to discover format is wrong after long wait
   - **Frequency**: First-time users, users with datasets from various sources
   - **Potential Improvement**: 
     - Validate file format immediately after selection (before upload starts)
     - Show file preview or structure check
     - Provide clear format requirements in UI

2. **Embedding Model Selection Not Clear**
   - **Impact**: Users may not understand importance of selecting correct model, leading to broken datasets
   - **Frequency**: All uploads, especially for users receiving datasets from others
   - **Potential Improvement**: 
     - Add prominent explanation of why correct model matters
     - Auto-detect embedding model from dataset metadata if possible
     - Show warning about mismatch consequences

3. **No Dataset Preview**
   - **Impact**: Users can't verify dataset contents before uploading
   - **Frequency**: Every upload
   - **Potential Improvement**: 
     - Show sample entries from file after selection
     - Display entry count, average text length, vector dimensions
     - Allow canceling after preview if not what expected

4. **Unclear Dataset Naming Best Practices**
   - **Impact**: Users create non-descriptive names, hard to identify later
   - **Frequency**: Every upload
   - **Potential Improvement**: 
     - Suggest naming conventions
     - Show examples of good names
     - Auto-suggest name based on file analysis

5. **No Progress for Large Files**
   - **Impact**: Large dataset uploads may take minutes with minimal feedback
   - **Frequency**: Large datasets (>100MB)
   - **Potential Improvement**: 
     - Show detailed progress (MB uploaded, upload speed)
     - Estimate time remaining
     - Show current stage (uploading vs. processing vs. validating)

6. **Cannot Edit Dataset After Upload**
   - **Impact**: If wrong embedding model selected, must delete and re-upload entire dataset
   - **Frequency**: When users make selection mistakes
   - **Potential Improvement**: 
     - Allow editing dataset metadata (name, embedding model)
     - Add validation step before finalizing
     - Show confirmation with all details before upload

---

## Design Considerations

**Following Contextual Design Principles**:

1. **Automation Opportunities**: 
   - Auto-detect embedding model from dataset metadata if included
   - Auto-suggest dataset name from file analysis
   - Auto-validate file format before upload starts
   - Auto-activate dataset after successful upload (optional)

2. **Simplification Opportunities**: 
   - Reduce required fields if possible (auto-detect model)
   - Combine name entry with file selection
   - Eliminate confirmation steps if validation is automated
   - Single-click upload if all info auto-detected

3. **Transition Smoothness**: 
   - Smooth modal appearance and dismissal
   - Clear progress indication during upload
   - Natural flow from upload to viewing dataset
   - Easy to upload multiple datasets in succession

4. **User Trust**: 
   - Clear file format requirements stated upfront
   - Transparent validation and processing
   - Success confirmation with verification option
   - Dataset actually works when upload succeeds

5. **Cognitive Load**: 
   - Don't require understanding of technical details (embeddings, vectors)
   - Clear labels and instructions
   - Sensible defaults where possible
   - Minimal required decisions

---

## Related Flows

- [Activate/Deactivate Dataset](./corpus-activation.md) - Make dataset available for chat queries
- [View Dataset Details](./view-dataset-details.md) - Verify uploaded contents
- [Chat with Dataset Query Enabled](../02-chat-interactions/rag-enabled-chat.md) - Use uploaded dataset
- [Create New Blockify Job](../05-blockify-processing/create-blockify-job.md) - Alternative: create dataset from documents
- [Upload Embedding Model](../03-model-management/embedding-model-upload.md) - Add required embedding model

---

## Technical References

**Knowledge Base Sections**:
- src/components/ui/upload-corpus-modal.js - Upload interface
- src/handlers/upload/upload-handler.js - File processing
- src/actions/upload.js - Upload state management
- src/reducers/cruddb-reducer.js - Dataset list updates
- src/localdb/base.js - Dataset storage

**Key Components**:
- Upload modal with file selector
- Embedding model selector
- Progress tracking
- Dataset list with CRUD operations

---

## Version History

| Date | Version | Author | Changes |
|------|---------|--------|---------|
| 2025-10-04 | 1.1 | [Iternal Technologies](https://iternal.ai/airgapai) | Initial comprehensive documentation |

---

## Notes

**Important Considerations**:
- Dataset file must be in JSONL format (newline-delimited JSON)
- Each line must have "text" and "vector" fields
- Vector dimensions must match the embedding model used
- Embedding model must be the SAME one used to create the dataset originally
- File is copied to application directory; original can be safely deleted after upload
- Large datasets (>500MB) may take several minutes to upload and process

**JSONL Format Example**:
```
{"text": "Information about topic A", "vector": [0.123, 0.456, 0.789, ...]}
{"text": "Information about topic B", "vector": [0.234, 0.567, 0.891, ...]}
```

**Best Practices**:
- Use descriptive dataset names that indicate content (e.g., "CompanyPolicy2025", "TechnicalDocs-ProductX")
- Document which embedding model was used when creating datasets
- Keep dataset files backed up externally
- Test small sample datasets before uploading very large ones
- Organize datasets by topic or domain for easier selection

**Common User Questions**:
- "Where do I get dataset files?" - Create them using Blockify jobs or import from external sources
- "What format should the file be?" - JSONL (JSON Lines) with text and vector fields
- "How do I know which embedding model to use?" - Must match the model used to create the dataset
- "Can I edit a dataset after uploading?" - No, must delete and re-upload; edit the file externally first
- "How large can datasets be?" - Limited by disk space and RAM; very large datasets (GB+) may be slow to search

