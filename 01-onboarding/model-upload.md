# Upload Model During Onboarding

## Overview
**Flow ID**: `onboarding-model-upload`  
**Category**: Onboarding & Initial Setup  
**Estimated Duration**: 5-15 minutes (plus upload time)  
**User Role**: All Users (first time)  
**Complexity**: Moderate  

**Purpose**: During the onboarding wizard, users are guided to upload their first AI language model, which is essential for using chat features. This embedded upload experience is simplified and explained within the setup flow.

---

## Trigger

**What initiates this flow:**
- [ ] User manually initiates
- [x] System event (reaches model upload step in onboarding wizard)

**Specific trigger**: User proceeds through onboarding wizard and reaches the model upload step (typically Step 1).

---

## Prerequisites

**Before starting, users must have:**
- [x] Onboarding wizard active
- [x] AI model file available on computer
- [x] Sufficient disk space for model
- [x] Understanding that model is required for chat

---

## User Intent Analysis

### Primary Intent
Upload first AI model as part of initial setup to enable core chat functionality.

### Secondary Intents
- Understand why model is needed
- Successfully complete essential onboarding step
- Prepare application for immediate use

### Subintents
- Follow guided process correctly
- Verify model uploads successfully
- Understand model's role in application

---

## Step-by-Step Flow

### Main Path (Happy Path)

**Step 1: Model Upload Step Appears**
- **User Action**: Arrive at model upload step in onboarding
- **System Response**: Model upload interface displays
- **UI Elements Visible**: 
  - Step header: "Upload Your AI Model" or "Step 1: Add Language Model"
  - Progress indicator: "Step 1 of 4" or similar
  - Explanation text: "You need an AI language model to chat. Upload your model file to get started."
  - File upload area (dropzone or button)
  - "Choose File" button
  - "I don't have a model yet" help link or text
  - "Skip this step" button (less prominent)
  - "Next" button (likely disabled until upload completes)
- **Visual Cues**: 
  - Clear step identification
  - Explanatory text in friendly tone
  - Upload area prominent

**Step 2: Read Explanation**
- **User Action**: Read why model is needed and what to upload
- **System Response**: Information helps user understand requirement
- **UI Elements Visible**: 
  - Explanation text about models
  - Supported file formats listed
  - May include link to documentation or help

**Step 3: Select Model File**
- **User Action**: Click "Choose File" button
- **System Response**: File browser opens
- **UI Elements Visible**: 
  - Operating system file browser
  - File type filter (may show .gguf and other supported formats)

**Step 4: Navigate to Model File**
- **User Action**: Browse to model file location, select file, click "Open"
- **System Response**: 
  - File browser closes
  - Filename appears in upload area
  - Model name auto-populates
  - Upload begins automatically or "Upload" button appears
- **UI Elements Visible**: 
  - Selected filename displayed
  - Model name field (auto-filled, editable)
  - Model type: "Large Language Model" (auto-set)
  - Progress bar (if upload started)
  - OR "Upload" button to initiate

**Step 5: Upload Progress**
- **User Action**: Wait for upload (5-30 minutes depending on model size)
- **System Response**: 
  - Progress bar advances
  - Percentage updates
  - Upload status displayed
- **UI Elements Visible**: 
  - Progress bar (0-100%)
  - Percentage: "35%" or similar
  - Upload speed (possibly)
  - Estimated time remaining (possibly)
  - Model size and upload progress (e.g., "2.5 GB of 7.2 GB")
- **Visual Cues**: 
  - Animated progress bar
  - Numbers increasing
  - May show file size uploaded

**Step 6: Upload Completes**
- **User Action**: No action required
- **System Response**: 
  - Progress reaches 100%
  - Success message appears
  - Checkmark or success icon shown
  - "Next" button becomes enabled
- **UI Elements Visible**: 
  - Success message: "Model uploaded successfully!"
  - Green checkmark icon
  - Model name confirmed
  - "Next" button now clickable (blue/active)
- **Visual Cues**: 
  - Green success color
  - Checkmark animation
  - Enabled next button

**Step 7: Proceed to Next Step**
- **User Action**: Click "Next" button
- **System Response**: 
  - Onboarding advances to next step
  - Model upload step marked complete
- **UI Elements Visible**: 
  - Next onboarding step loads
  - Progress indicator updates: "Step 2 of 4"
- **Visual Cues**: Smooth step transition

**Final Step: Model Uploaded via Onboarding**
- **Success Indicator**: 
  - Model uploaded and registered
  - Can proceed with onboarding
  - Model will be available after onboarding completes
- **System State Change**: 
  - Model file stored in application
  - Model registered in database
  - Model will load when onboarding completes
  - Ready for use in conversations
- **Next Possible Actions**: 
  - Continue to next onboarding step
  - Complete remaining onboarding
  - Use model after onboarding finishes

---

## Alternative Paths & Strategies

### Strategy A: Skip Model Upload
**When to use**: Don't have model file yet or want to upload later

**Steps**:
1. On model upload step, click "Skip this step"
2. Warning may appear: "You need a model to chat"
3. Confirm skip
4. Proceed to next step
5. Must upload model manually later to use chat

### Strategy B: Get Model First
**When to use**: Realize you need model file but don't have it

**Steps**:
1. See model upload step
2. Click "I don't have a model yet" help link
3. Instructions appear for obtaining models
4. Exit application or pause onboarding
5. Obtain model file
6. Return to onboarding and upload

### Strategy C: Upload Model, Skip Other Steps
**When to use**: Only want to complete essential configuration

**Steps**:
1. Complete model upload step
2. Skip all subsequent steps
3. Exit onboarding with model configured
4. Minimum viable setup complete

---

## Error States & Recovery

### Error 1: Wrong File Type Selected
**Cause**: User selects non-model file  
**User Experience**: 
- Error: "Invalid file type" or "Not a model file"
- Upload doesn't proceed or fails

**Recovery Steps**:
1. Read error message
2. Click "Choose File" again
3. Select correct model file (typically .gguf or similar)
4. Verify file is actually an AI model
5. Try again with correct file

### Error 2: Upload Interrupted
**Cause**: Closed application, lost connection, or error during upload  
**User Experience**: 
- Upload progress stops
- Error message may appear
- Model not available

**Recovery Steps**:
1. Restart onboarding or application
2. May resume at model upload step
3. Select file and upload again
4. Ensure stable conditions (don't close app during upload)

### Error 3: Insufficient Disk Space
**Cause**: Not enough free space for large model  
**User Experience**: 
- Error during upload: "Insufficient disk space"
- Upload fails partway

**Recovery Steps**:
1. Free up disk space (delete unnecessary files)
2. Consider uploading smaller model
3. Try again after freeing space
4. Or skip and upload later when space available

### Error 4: Model File Corrupted
**Cause**: Model file is damaged  
**User Experience**: 
- Upload completes but validation fails
- Error: "Invalid model file" or "Corrupted file"

**Recovery Steps**:
1. Re-download model file from source
2. Verify file integrity (check file size, hash if available)
3. Upload fresh copy
4. If issue persists, try different model

---

## Pain Points & Friction

**Identified Issues**:

1. **No Guidance on Where to Get Models**
   - **Impact**: Users don't know where to obtain model files
   - **Frequency**: First-time users without models
   - **Potential Improvement**: 
     - Prominent link to model sources
     - Explanation of compatible model types
     - Recommendations for beginner-friendly models

2. **Long Upload During Setup**
   - **Impact**: Onboarding feels slow due to 10-30 minute upload
   - **Frequency**: Every first-time setup
   - **Potential Improvement**: 
     - Allow continuing onboarding while upload proceeds
     - Upload in background
     - Skip and upload later option more prominent

3. **Cannot Preview Model Capabilities**
   - **Impact**: Don't know if model suits their needs before uploading
   - **Frequency**: Users with multiple model options
   - **Potential Improvement**: 
     - Model comparison information
     - Capability descriptions
     - Size/speed/quality trade-off explanations

4. **Single Model Only**
   - **Impact**: Can only upload one model during onboarding
   - **Frequency**: Users wanting to test multiple models
   - **Potential Improvement**: 
     - Allow multiple model uploads
     - OR make it clear more can be added later
     - Quick-add additional models at end

---

## Design Considerations

**Following Contextual Design Principles**:

1. **Automation Opportunities**: 
   - Auto-detect model type from filename
   - Auto-suggest model name
   - Auto-validate file before upload starts

2. **Simplification Opportunities**: 
   - Streamlined upload (fewer confirmations)
   - Clear explanation of requirements
   - Help links for common issues

3. **Transition Smoothness**: 
   - Natural flow in onboarding sequence
   - Clear progress through upload stages
   - Smooth advancement to next step

4. **User Trust**: 
   - Clear progress indication during long upload
   - Success confirmation before proceeding
   - Can verify model later

5. **Cognitive Load**: 
   - Focused on single task (upload model)
   - Clear instructions
   - Minimal required information

---

## Related Flows

- [First-Time Application Setup](./initial-setup.md) - Parent onboarding flow
- [Upload Large Language Model](../03-model-management/llm-model-upload.md) - Standalone upload (similar process)
- [Select Chat Style During Onboarding](./chat-style-selection.md) - Next step typically

---

## Technical References

**Knowledge Base Sections**:
- src/components/onboarding/index.js - Onboarding coordinator
- src/components/onboarding/upload-card.js - Upload interface in onboarding
- src/handlers/upload/upload-handler.js - Upload processing
- src/localdb/onboarding.js - Onboarding progress tracking

**Key Components**:
- Embedded upload interface within wizard
- Progress tracking integrated with onboarding steps
- Step completion validation

---

## Version History

| Date | Version | Author | Changes |
|------|---------|--------|---------|
| 2025-10-04 | 1.1 | [Iternal Technologies](https://iternal.ai/airgapai) | Initial comprehensive documentation |

---

## Notes

**Important Considerations**:
- Model upload is typically the first and most important onboarding step
- Cannot use chat features without a model
- Large models (10+ GB) will take significant time to upload
- Application must remain open during upload
- Upload progress is part of onboarding progress
- Completing upload doesn't automatically select model (may need to select in settings)

**Recommended First Models**:
- Medium-sized models (7-8B parameters): Good balance for most hardware
- Smaller models (3B parameters): Faster, lower resource usage
- Larger models (13B+ parameters): Better quality but require more powerful hardware

**Best Practices**:
- Have model file ready before starting onboarding
- Ensure stable environment for upload (plugged in, not on battery)
- Don't close application during upload
- Verify upload completes successfully before proceeding
- Test model with simple chat after onboarding

**Common User Questions**:
- "Where do I get a model file?" - External sources; application doesn't provide downloads
- "What model should I upload first?" - Medium-sized (7-8B) recommended for most users
- "Can I skip and upload later?" - Yes, but can't use chat until model uploaded
- "How long will upload take?" - Depends on file size; 5-30 minutes typical
- "Can I upload more models later?" - Yes, through Settings page

