# Upload Large Language Model

## Overview
**Flow ID**: `llm-model-upload`  
**Category**: Model Management  
**Estimated Duration**: 5-30 minutes (depending on file size)  
**User Role**: All Users  
**Complexity**: Simple  

**Purpose**: This flow allows users to add a new AI language model to the application. Models are required to enable chat functionality. The model file is uploaded from your computer to the application and becomes available for use in conversations.

---

## Trigger

**What initiates this flow:**
- [x] User manually initiates


**Specific trigger**: User needs to add a new language model to use for AI conversations, either because:
- This is their first time using the application and no models are available
- They want to add an additional or alternative model to their collection
- They are replacing an existing model with an updated version

---

## Prerequisites

**Before starting, users must have:**
- [x] Application installed and running
- [x] A compatible AI model file saved on their computer (formats like .gguf or other supported formats)
- [x] Sufficient disk space to store the model (models typically range from 2GB to 50GB+)
- [x] Knowledge of where the model file is located on their computer

---

## User Intent Analysis

### Primary Intent
Upload and make available a new AI language model for conducting chat conversations.

### Secondary Intents
- Build a library of different models with varying capabilities
- Test different models to find one that best suits their needs
- Ensure offline AI capability by having models locally available
- Prepare the system for benchmarking different models

### Subintents
- Verify the model file is compatible before upload
- Ensure the model name is clearly identifiable for future selection
- Confirm the model type is correctly categorized

---

## Step-by-Step Flow

### Main Path

**Step 1: Navigate to Settings**
- **User Action**: From any page in the application, click the "Settings" menu item in the navigation
- **System Response**: The Settings page loads and displays
- **UI Elements Visible**: 
  - Navigation menu with "Settings" highlighted
  - Settings page content area
  - Multiple tabs across the top of the settings area
- **Visual Cues**: Settings icon (gear symbol) appears in navigation, Settings tab is visually distinguished when active

**Step 2: Access Chat AI Models Tab**
- **User Action**: Click on the "Chat AI Models" tab at the top of the Settings page
- **System Response**: The Chat AI Models section displays, showing any existing models in a table or list format
- **UI Elements Visible**: 
  - "Chat AI Models" tab (now highlighted/active)
  - List or table of existing models (if any have been uploaded)
  - "Add Model" button (typically prominent, may be colored blue)
  - Model information columns: Name, Type, Path, Actions
- **Visual Cues**: Active tab is visually distinct (underlined or highlighted), Add Model button stands out with color

**Step 3: Initiate Model Upload**
- **User Action**: Click the "Add Model" button
- **System Response**: A modal dialog (overlay window) appears on top of the current page
- **UI Elements Visible**: 
  - Modal window with title "Upload Model" or similar
  - File upload area/button
  - Text input field for Model Name
  - Dropdown or selection field for Model Type
  - "Cancel" and "Save" buttons at the bottom
  - Close button (X) in the upper corner
- **Visual Cues**: Page behind the modal may be slightly dimmed, modal is centered and prominent

**Step 4: Select Model File**
- **User Action**: Click the "Choose File" or file upload button/area in the modal
- **System Response**: Operating system's file browser dialog opens
- **UI Elements Visible**: 
  - Native file browser window (appearance depends on operating system)
  - File navigation interface
  - File type filters (may show only compatible model formats)
- **Visual Cues**: Standard operating system file browser appearance

**Step 5: Navigate to and Select File**
- **User Action**: Browse through folders to locate the model file, then click on the desired file and click "Open" or equivalent
- **System Response**: 
  - File browser closes
  - Modal dialog reappears
  - Selected filename now appears in the file upload area
  - Model Name field auto-populates based on the filename
  - Model Type field may auto-populate to "Large Language Model"
- **UI Elements Visible**: 
  - Selected filename displayed (possibly with full path or just the filename)
  - Model Name field filled with extracted name
  - Model Type field showing "Large Language Model"
  - Save button (may become enabled if it was disabled)
- **Visual Cues**: File selection area shows the selected file, fields are populated, visual indication that the form is complete

**Step 6: Review and Adjust Model Information**
- **User Action**: Review the auto-populated Model Name and Model Type; edit the Model Name if desired (Type typically stays as-is)
- **System Response**: Text updates in real-time as user types
- **UI Elements Visible**: 
  - Editable text field for Model Name (cursor appears when clicked)
  - Model Type field (may be read-only or selectable)
  - Character count or field validation indicators (if applicable)
- **Visual Cues**: Active text field is highlighted when clicked, cursor blinking indicates edit mode

**Step 7: Confirm and Save**
- **User Action**: Click the "Save" button at the bottom of the modal
- **System Response**: 
  - Modal content changes to show upload progress
  - Progress bar appears and begins filling
  - Percentage or status text may display (e.g., "Uploading... 15%")
- **UI Elements Visible**: 
  - Progress bar (animated, filling from left to right)
  - Percentage text (updates as upload progresses)
  - Status message (e.g., "Uploading model...")
  - Cancel or Close button may become disabled during upload
- **Visual Cues**: Progress bar animation, percentage increasing, may show file size information

**Step 8: Wait for Upload Completion**
- **User Action**: Wait while the file uploads (no interaction required; user should not close the application)
- **System Response**: 
  - Progress bar continues advancing
  - Percentage updates regularly
  - May show upload speed or estimated time remaining
- **UI Elements Visible**: 
  - Continuously updating progress indicator
  - Current status information
- **Visual Cues**: Animated progress bar provides visual feedback that the system is working

**Step 9: Upload Completes Successfully**
- **User Action**: No action required
- **System Response**: 
  - Progress reaches 100%
  - Success message displays (e.g., "Model uploaded successfully!")
  - Modal automatically closes after a brief moment (1-2 seconds) OR requires user to click "Done"
  - User returns to the Settings page, Chat AI Models tab
- **UI Elements Visible**: 
  - Success message (may be green with checkmark icon)
  - Settings page with updated model list
  - Newly uploaded model now appears in the models table
- **Visual Cues**: Green color and checkmark indicate success, smooth transition back to main view

**Step 10: Verify Model in List**
- **User Action**: Look at the models list to confirm the new model appears
- **System Response**: Model list displays with the new model included
- **UI Elements Visible**: 
  - Table or list showing all models
  - New model entry with Name, Type (Large Language Model), Path, and action buttons
  - Model may have a status indicator showing it's ready to use
- **Visual Cues**: New model may be highlighted or positioned at the top of the list

**Final Step: Model Ready for Use**
- **Success Indicator**: 
  - Model appears in the models list
  - Model can be selected as the active chat model
  - No error messages are displayed
- **System State Change**: 
  - Model file is now stored locally in the application's data directory
  - Model is registered in the application's database
  - Model is available for selection in chat settings
- **Next Possible Actions**: 
  - Select this model as the active chat model
  - Upload additional models
  - Start a new chat using this model (if it's been set as active)
  - Run benchmarks on this model to test performance

---

## Alternative Paths & Strategies

### Strategy A: Drag and Drop Upload
**When to use**: If the application supports drag-and-drop and the user finds it more convenient than clicking

**Steps**:
1. Open the Settings page and navigate to Chat AI Models tab
2. Click "Add Model" to open the upload modal
3. Open file browser in a separate window to locate the model file
4. Drag the model file from the file browser and drop it into the file upload area of the modal
5. Model Name and Type auto-populate
6. Click "Save" to begin upload
7. Wait for completion (same as main path from Step 8)

### Strategy B: Replace Existing Model
**When to use**: User wants to update an existing model with a new version

**Steps**:
1. Navigate to Settings > Chat AI Models
2. Locate the existing model in the list
3. Click "Delete" or "Remove" button on the existing model
4. Confirm deletion if prompted
5. Follow main path steps 3-10 to upload the new version

### Strategy C: Upload During Onboarding
**When to use**: First-time users during initial application setup

**Steps**:
1. Application launches onboarding wizard
2. Onboarding step prompts for model upload
3. Embedded upload interface appears (similar to modal)
4. Follow main path steps 4-9 within onboarding context
5. Onboarding wizard advances to next step automatically

---

## Error States & Recovery

### Error 1: Incompatible File Format
**Cause**: User selected a file that is not a supported model format  
**User Experience**: 
- Error message appears after selecting file or during upload
- Message states: "Incompatible file format" or "This file type is not supported"
- Upload does not proceed

**Recovery Steps**:
1. Read the error message carefully
2. Click "OK" or close the error message
3. Verify you have the correct model file (should be .gguf or other supported format)
4. Click "Choose File" again and select the correct file
5. If error persists, check model file documentation to confirm format compatibility

### Error 2: Insufficient Disk Space
**Cause**: Not enough free space on the device to store the model  
**User Experience**: 
- Error message appears during upload, possibly when progress reaches a certain point
- Message states: "Insufficient disk space" or similar
- Upload stops and may roll back

**Recovery Steps**:
1. Close the upload modal
2. Free up disk space by deleting unnecessary files or moving them to external storage
3. Return to Settings and restart the upload process
4. Consider uploading a smaller model if disk space remains limited

### Error 3: Upload Interrupted
**Cause**: Network disconnection, application crash, or user accidentally closed window  
**User Experience**: 
- Upload progress stops advancing
- Error message may appear: "Upload failed" or "Connection lost"
- Modal may close unexpectedly

**Recovery Steps**:
1. Check if the model appears in the models list (partial uploads are typically removed automatically)
2. Verify your computer is functioning normally (no crashes or freezes)
3. Restart the upload process from Step 3 of the main path
4. Ensure you don't close the application window during upload

### Error 4: File Not Found
**Cause**: User moved or deleted the model file after selecting it but before upload completed  
**User Experience**: 
- Error message: "File not found" or "Cannot access file"
- Upload fails to start or stops immediately

**Recovery Steps**:
1. Close the error message
2. Locate the model file in your computer's file system
3. Ensure the file has not been moved or deleted
4. Restart the upload process and select the file from its current location

### Error 5: Model Name Already Exists
**Cause**: A model with the same name already exists in the system  
**User Experience**: 
- Error message appears when trying to save: "Model name already exists" or similar
- Upload does not proceed

**Recovery Steps**:
1. Read the error message
2. Edit the Model Name field to use a different, unique name (e.g., add a version number or date)
3. Click "Save" again
4. Upload should proceed normally with the new name

---

## Pain Points & Friction

**Identified Issues**:

1. **Long Upload Times for Large Models**
   - **Impact**: Users must wait 10-30 minutes or more for large models; if they close the application, upload fails
   - **Frequency**: Every time a large model is uploaded
   - **Potential Improvement**: 
     - Add background upload capability so users can continue working
     - Add pause/resume functionality for uploads
     - Display estimated time remaining prominently

2. **No File Validation Before Upload**
   - **Impact**: Users might wait through a long upload only to discover the file is incompatible
   - **Frequency**: Occurs when users are unfamiliar with compatible formats
   - **Potential Improvement**: 
     - Validate file format immediately after selection, before upload begins
     - Display supported formats clearly in the file selection dialog
     - Show format requirements prominently on the upload modal

3. **Unclear Model Name Significance**
   - **Impact**: Users may not understand that the model name is how they'll identify it later when selecting which model to use
   - **Frequency**: Common for first-time users
   - **Potential Improvement**: 
     - Add helper text explaining that this name will be used throughout the application
     - Provide suggestions for naming conventions (e.g., include model size, capabilities)
     - Show preview of where this name will appear

4. **No Progress During File Scan/Validation**
   - **Impact**: After upload completes, there may be a delay while the system processes the model with no feedback
   - **Frequency**: Occurs with every upload
   - **Potential Improvement**: 
     - Add "Processing model..." status after upload bar reaches 100%
     - Show validation steps as they complete

5. **Cannot Cancel Mid-Upload**
   - **Impact**: If user selects wrong file or changes their mind, they must wait for upload to complete
   - **Frequency**: Occasional user error
   - **Potential Improvement**: 
     - Add functional "Cancel" button that stops upload and cleans up partial files
     - Confirm cancellation with user to prevent accidental cancels

---

## Design Considerations

**Following Contextual Design Principles**:

1. **Automation Opportunities**: 
   - Auto-detect model type from file metadata or filename patterns
   - Auto-suggest optimal model names based on file properties
   - Auto-validate file format before upload begins
   - Auto-cleanup failed uploads without user intervention

2. **Simplification Opportunities**: 
   - Reduce required fields if possible (Model Type could be completely automatic)
   - Consider one-step upload if drag-and-drop is enabled
   - Eliminate confirmation dialogs where system can safely assume user intent

3. **Transition Smoothness**: 
   - Clear path to next action (selecting this model as active) should be indicated
   - Smooth transition back to model list without jarring jumps
   - Maintain context if user navigates away and returns during upload

4. **User Trust**: 
   - Clear progress indication builds confidence that upload is working
   - Success confirmation reassures user the operation completed
   - Model appearing in list provides concrete verification
   - File size and upload speed transparency helps set expectations

5. **Cognitive Load**: 
   - Minimal required information (just file selection and optional name editing)
   - Auto-population reduces memory burden
   - Clear labels and instructions reduce confusion
   - Status messages explain what's happening at each stage

---

## Related Flows

- [Select Active Chat Model](./select-llm-model.md) - Choose this model for use in conversations
- [Run Full Benchmark Suite](../08-benchmarking/run-full-benchmark.md) - Test this model's performance
- [View Model Information](./view-model-info.md) - View details about the uploaded model
- [Delete a Model](./delete-model.md) - Remove this model if no longer needed
- [Upload Embedding Model](./embedding-model-upload.md) - Similar process for different model type

---

## Technical References

**Knowledge Base Sections**:
- src/pages/settings.js - Settings page container
- src/components/ui/upload-model-modal.js - Upload modal interface
- src/handlers/upload/upload-handler.js - File upload processing
- src/actions/upload.js - Upload state management
- src/reducers/cruddb-reducer.js - Model list state updates

**Key Components**:
- Upload modal with file selector and progress tracking
- Model list table with CRUD operations
- File validation and storage system

---

## Version History

| Date | Version | Author | Changes |
|------|---------|--------|---------|
| 2025-10-04 | 1.1 | [Iternal Technologies](https://iternal.ai/airgapai) | Initial documentation with comprehensive detail |

---

## Notes

**Important Considerations**:
- Model files can be very large (5-50GB+); ensure adequate disk space and stable connection
- Once uploaded, the model file is copied to the application's data directory; the original file can be safely deleted or moved
- The application must remain open and running during the entire upload process
- Multiple models can be uploaded, but only one can be active for chat at a time
- Model upload does not automatically select the model as active; this is a separate step

**Common User Questions**:
- "Where should I get model files?" - Models must be obtained from external sources; the application does not provide model downloads
- "How do I know if a model is compatible?" - Check the model documentation; AirgapAI typically supports GGUF and other quantized formats
- "Can I use the application while uploading?" - Yes, you can navigate to other pages, but don't close the application
- "What happens to the original file?" - It remains in its original location; the application creates its own copy

