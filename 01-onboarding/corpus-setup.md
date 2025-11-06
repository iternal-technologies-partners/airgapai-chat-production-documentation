# Setup Dataset During Onboarding

## Overview
**Flow ID**: `onboarding-corpus-setup`  
**Category**: Onboarding & Initial Setup  
**Estimated Duration**: 5-10 minutes (plus processing time if creating)  
**User Role**: All Users (first time)  
**Complexity**: Moderate  

**Purpose**: Optional onboarding step that helps users upload or create their first dataset for AI-powered document querying. Can upload existing dataset file or start blockify job to create one from documents. This step introduces dataset query features.

---

## Trigger

**What initiates this flow:**
- [ ] User manually initiates
- [x] System event (reaches dataset setup step in onboarding)

**Specific trigger**: Onboarding wizard advances to optional dataset setup step (typically Step 3 or 4).

---

## Prerequisites

**Before starting, users must have:**
- [x] Onboarding wizard active
- [x] Embedding model available (or will upload during this step)
- [x] Optionally: Dataset file or documents to process
- [x] Understanding that this step is optional

---

## User Intent Analysis

### Primary Intent
Optionally configure dataset features during initial setup to enable AI conversations grounded in specific documents.

### Secondary Intents
- Understand dataset query capabilities
- Set up knowledge base early
- Enable advanced features from start

### Subintents
- Learn what datasets are for
- Decide if feature is needed immediately
- Complete setup if relevant to use case

---

## Step-by-Step Flow

### Main Path A - Skip Dataset Setup (Most Common)

**Step 1: Dataset Setup Step Appears**
- **User Action**: Arrive at dataset setup step
- **System Response**: Dataset introduction displays
- **UI Elements Visible**: 
  - Step header: "Add Knowledge Base (Optional)" or "Step 3: Datasets"
  - Progress: "Step 3 of 4"
  - Explanation text describing dataset features
  - Two primary options:
    - "Upload Existing Dataset" button
    - "Create from Documents" button
  - **"Skip for Now" button** (prominent secondary option)
  - "Next" button
- **Visual Cues**: 
  - "Optional" clearly marked
  - Skip option prominent

**Step 2: Decide to Skip**
- **User Action**: Click "Skip for Now" or "Next" without configuring
- **System Response**: 
  - Onboarding advances to next step or completion
  - Dataset setup skipped
  - No dataset configured
- **UI Elements Visible**: Next step or completion screen loads

**Final Step: Skipped Dataset Setup**
- **Success Indicator**: Advanced past dataset step
- **System State Change**: Dataset feature not configured; can add later
- **Next Actions**: Complete onboarding, configure datasets manually later if needed

---

## Main Path B - Upload Existing Dataset

**Step 1: Choose Upload Option**
- **User Action**: Click "Upload Existing Dataset" button
- **System Response**: Upload interface appears within onboarding
- **UI Elements Visible**: 
  - File upload controls
  - Dataset name field
  - Embedding model selector
  - Upload button

**Step 2-5: Follow Upload Process**
- **User Action**: Complete dataset upload (see corpus-upload.md for detailed steps)
- **System Response**: Dataset uploads and registers
- **Note**: Simplified upload interface within onboarding context

**Step 6: Upload Completes**
- **User Action**: Wait for completion
- **System Response**: 
  - Success message
  - Dataset registered
  - "Next" button enabled

**Step 7: Proceed**
- **User Action**: Click "Next"
- **System Response**: Advance to next onboarding step

**Final Step: Dataset Uploaded via Onboarding**
- **Success Indicator**: Dataset available in application
- **System State Change**: Dataset ready for use
- **Next Actions**: Complete onboarding, use dataset in chats

---

## Main Path C - Create Dataset from Documents

**Step 1: Choose Create Option**
- **User Action**: Click "Create from Documents" button
- **System Response**: Simplified blockify job interface appears
- **UI Elements Visible**: 
  - Document upload area
  - Basic configuration options
  - Simplified from full blockify interface
  - Explanation of what will happen

**Step 2-4: Upload Documents**
- **User Action**: Upload documents for processing
- **System Response**: Files upload and extract text
- **Note**: Simplified file upload within onboarding

**Step 5: Start Processing**
- **User Action**: Click "Start Processing" or "Create Dataset"
- **System Response**: 
  - Job starts in background
  - Onboarding may advance while job processes
  - Status indicator for job shown

**Step 6: Complete Onboarding While Job Processes**
- **User Action**: Click "Next" to finish onboarding
- **System Response**: 
  - Onboarding completes
  - Job continues in background
  - Can monitor via job status badge

**Final Step: Dataset Job Started**
- **Success Indicator**: Job processing in background
- **System State Change**: Blockify job created and running
- **Next Actions**: Monitor job, use dataset when complete

---

## Alternative Paths & Strategies

### Strategy A: Skip and Configure Later
**When to use**: Not ready to set up datasets yet

**Steps**:
1. Click "Skip for Now"
2. Complete rest of onboarding
3. Add datasets later via Settings or Blockify page

### Strategy B: Upload Multiple Datasets
**When to use**: Have several datasets ready

**Steps**:
1. Upload first dataset
2. Click "Add Another" if option available
3. Upload additional datasets
4. OR skip and add more later manually

---

## Error States & Recovery

### Error 1: No Embedding Model for Dataset
**Cause**: Embedding model not uploaded yet  
**User Experience**: 
- Error: "Embedding model required"
- Cannot upload or create dataset

**Recovery Steps**:
1. Skip dataset step for now
2. Complete onboarding
3. Upload embedding model in settings
4. Then add dataset manually

### Error 2: Upload Fails
**Cause**: File error or system issue  
**User Experience**: 
- Upload error message
- Dataset not added

**Recovery Steps**:
1. Try again
2. Or skip and upload later
3. Don't let this block onboarding completion

---

## Pain Points & Friction

**Identified Issues**:

1. **Optional Step May Confuse Priority**
   - **Impact**: Users unsure if they should complete it
   - **Potential Improvement**: 
     - Explain when datasets are useful
     - "Recommended for: ..." labels
     - Show use cases clearly

2. **Simplified Interface May Miss Features**
   - **Impact**: Limited options compared to full dataset workflow
   - **Potential Improvement**: Link to full workflow for advanced users

---

## Design Considerations

**Following Contextual Design Principles**:

1. **Automation Opportunities**: Skip by default for beginners
2. **Simplification Opportunities**: Clear optional status
3. **User Trust**: Can skip without consequences
4. **Cognitive Load**: Don't force complex decision early

---

## Related Flows

- [First-Time Application Setup](./initial-setup.md) - Parent onboarding
- [Upload New Dataset](../04-dataset-management/corpus-upload.md) - Full upload flow
- [Create New Blockify Job](../05-blockify-processing/create-blockify-job.md) - Full creation flow

---

## Technical References

**Knowledge Base Sections**:
- src/components/onboarding/index.js - Onboarding steps
- src/components/onboarding/upload-card.js - Dataset upload in onboarding

---

## Version History

| Date | Version | Author | Changes |
|------|---------|--------|---------|
| 2025-10-04 | 1.1 | [Iternal Technologies](https://iternal.ai/airgapai) | Initial comprehensive documentation |

---

## Notes

**Important Considerations**:
- Dataset setup is completely optional
- Can be done anytime after onboarding
- Datasets not needed for basic chat
- Only needed for document-based querying

**Best Practices**:
- Skip during onboarding unless datasets ready
- Focus on completing basic setup first
- Add datasets after understanding chat basics
- Use full dataset workflow later for better control

**Common User Questions**:
- "Do I need a dataset?" - No, optional; only for document querying
- "Can I add later?" - Yes, anytime via Settings or Blockify
- "Should I skip?" - Yes if not ready; easy to add later
- "What's the difference between upload and create?" - Upload: existing file; Create: process documents with AI

