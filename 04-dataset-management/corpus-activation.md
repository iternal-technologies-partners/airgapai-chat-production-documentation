# Activate/Deactivate Dataset

## Overview
**Flow ID**: `corpus-activation`  
**Category**: Dataset/Corpus Management  
**Estimated Duration**: 30 seconds  
**User Role**: All Users  
**Complexity**: Simple  

**Purpose**: This flow enables users to activate or deactivate a dataset for use in AI conversations. Only one dataset can be active at a time. The active dataset is the one that will be queried when the dataset query feature is enabled in chat conversations, providing context-specific information from your documents.

---

## Trigger

**What initiates this flow:**
- [x] User manually initiates


**Specific trigger**: User wants to change which dataset is used for AI queries, typically because:
- They need to query a different set of documents
- They're starting work on a different project or topic
- They want to test different datasets
- They're switching between multiple knowledge bases

---

## Prerequisites

**Before starting, users must have:**
- [x] Application installed and running
- [x] At least one dataset uploaded
- [x] Access to Settings or Datasets page

---

## User Intent Analysis

### Primary Intent
Select which dataset will be queried during AI conversations when the dataset query feature is enabled, ensuring the AI references the appropriate knowledge base for the current task.

### Secondary Intents
- Switch between different knowledge domains
- Control which information is accessible to AI
- Disable dataset queries entirely if not needed
- Organize work by activating relevant datasets

### Subintents
- Ensure only appropriate data is queried
- Avoid cross-contamination between different datasets
- Optimize query performance by limiting to one dataset

---

## Step-by-Step Flow

### Main Path - Activate a Dataset

**Step 1: Navigate to Settings or Datasets**
- **User Action**: Click "Settings" in navigation OR "Datasets" if available
- **System Response**: Page loads showing configuration options
- **UI Elements Visible**: 
  - Settings tabs or Datasets list
  - Available datasets displayed
- **Visual Cues**: Active page highlighted in navigation

**Step 2: Locate Dataset Selection**
- **User Action**: Find the dataset selection area
  - In Settings: Look for "Active Dataset" dropdown or similar
  - In Datasets page: Look at dataset list with activation controls
- **System Response**: Dataset options displayed
- **UI Elements Visible**: 
  - **If Settings**: Dropdown showing current active dataset
  - **If Datasets page**: List of datasets with status indicators
  - Currently active dataset marked (checkmark, "ACTIVE" badge, or highlight)
  - Inactive datasets shown differently
- **Visual Cues**: 
  - Active dataset has green badge or checkmark
  - Inactive datasets grayed out or neutral color

**Step 3: Select Dataset to Activate**
- **User Action**: 
  - **If Settings**: Click dropdown and select different dataset
  - **If Datasets page**: Click "Activate" button on desired dataset
- **System Response**: 
  - Selection registered
  - Active dataset switches immediately
  - Previous active dataset becomes inactive
- **UI Elements Visible**: 
  - New dataset marked as "ACTIVE"
  - Previous active dataset shows "INACTIVE"
  - Status indicators update
- **Visual Cues**: 
  - Color change (green for active)
  - Badge updates
  - Smooth transition

**Final Step - Dataset Activated**
- **Success Indicator**: 
  - Selected dataset shows "ACTIVE" status
  - Only one dataset active at a time
  - Previous active dataset now inactive
  - Can use dataset in chat immediately
- **System State Change**: 
  - Active dataset setting updated in database
  - New dataset will be used for all future queries
  - Chat interface uses this dataset when dataset query enabled
  - Setting persists across sessions
- **Next Possible Actions**: 
  - Return to chat and use dataset query feature
  - Verify dataset contents before using
  - Adjust chat settings if needed
  - Switch to different dataset later

---

## Alternative Path - Deactivate Dataset (Disable All)

**Step 1: Access Dataset Settings**
- **User Action**: Navigate to Settings or Datasets page
- **System Response**: Dataset options displayed
- **UI Elements Visible**: Currently active dataset visible

**Step 2: Deactivate Current Dataset**
- **User Action**: 
  - **If Settings**: Select "None" or "No Dataset" from dropdown
  - **If Datasets page**: Click "Deactivate" on active dataset
- **System Response**: 
  - Active dataset becomes inactive
  - No dataset is now active
- **UI Elements Visible**: 
  - All datasets show "INACTIVE"
  - No green active indicators
  - Dropdown shows "None" or "No Dataset"
- **Visual Cues**: 
  - All datasets gray or neutral
  - No active badges

**Final Step - No Active Dataset**
- **Success Indicator**: 
  - No dataset marked active
  - Dataset query feature won't work in chat (or will show error)
- **System State Change**: 
  - No active dataset in settings
  - Chat dataset queries disabled or will return errors
- **Next Possible Actions**: 
  - Activate a dataset when needed
  - Use chat without dataset queries
  - Upload new dataset and activate it

---

## Alternative Path - Switch via Chat Interface

**Step 1: Access Chat Dataset Selector**
- **User Action**: In chat interface, click on dataset toggle/selector
- **System Response**: Dataset selector expands
- **UI Elements Visible**: 
  - Collapsible dataset control (100px collapsed, 235px expanded)
  - Dropdown showing available datasets
  - Current selection highlighted

**Step 2: Select Different Dataset**
- **User Action**: Click on different dataset in dropdown
- **System Response**: 
  - Dataset selection updates immediately
  - New dataset becomes active
  - Previous dataset deactivates
- **UI Elements Visible**: 
  - New dataset name shown in selector
  - Dataset toggle remains "ON" (if was enabled)
- **Visual Cues**: Selected dataset appears in control

**Final Step - Dataset Switched**
- **Success Indicator**: 
  - New dataset active
  - Future queries use new dataset
  - Setting saved automatically
- **System State Change**: Same as main path
- **Next Actions**: Continue chat with new dataset

---

## Error States & Recovery

### Error 1: Cannot Find Activation Control
**Cause**: User looking in wrong location  
**User Experience**: 
- Cannot find button or dropdown to activate dataset
- Unsure how to change active dataset

**Recovery Steps**:
1. Check Settings page for "Active Dataset" or "RAG Corpus" setting
2. OR check Datasets page for "Activate" buttons on each dataset
3. OR try chat interface dataset selector
4. Activation control exists in at least one of these locations

**QA Note**: Not an error but navigation confusion. Documentation helps prevent.

### Error 2: Dataset Won't Activate
**Cause**: Missing embedding model or corrupted dataset file  
**User Experience**: 
- Click activate but status doesn't change
- Error message: "Cannot activate dataset" or similar
- Dataset remains inactive

**Recovery Steps**:
1. Verify embedding model for this dataset is uploaded
2. Check if dataset file exists and is not corrupted
3. Try different dataset to see if issue is specific or general
4. Re-upload dataset if corrupted
5. Ensure embedding model matches dataset

### Error 3: Multiple Datasets Appear Active
**Cause**: Display sync issue  
**User Experience**: 
- Two datasets show "ACTIVE" status
- Unclear which is actually being used

**Recovery Steps**:
1. Refresh page
2. Only one should show active after refresh
3. If issue persists, explicitly select desired dataset
4. System enforces single active dataset even if display shows otherwise

**QA Note**: Display bug, not data issue. One is actually active.

---

## Pain Points & Friction

**Identified Issues**:

1. **Unclear Which Dataset Is Currently Active**
   - **Impact**: Users uncertain which dataset they're querying
   - **Frequency**: When switching between datasets frequently
   - **Potential Improvement**: 
     - Show active dataset prominently in chat interface
     - Display active dataset in page header
     - Add confirmation when switching

2. **No Preview of Dataset Contents**
   - **Impact**: Users activate dataset without confirming it's the right one
   - **Frequency**: Users with multiple similar datasets
   - **Potential Improvement**: 
     - Show dataset summary (item count, date, topic keywords)
     - Quick preview option before activating
     - Recent query results shown

3. **Cannot Activate Multiple Datasets**
   - **Impact**: Users wanting to query across multiple knowledge bases simultaneously
   - **Frequency**: Users with related but separate datasets
   - **Potential Improvement**: 
     - Allow multi-dataset activation
     - Create merged/combined dataset views
     - OR explain why single-dataset limitation exists

**QA Note**: Simple feature has minimal error potential. Pain points are feature limitations not bugs.

---

## Design Considerations

**Following Contextual Design Principles**:

1. **Automation Opportunities**: 
   - Auto-activate dataset when created from job
   - Remember last-used dataset per project
   - Auto-suggest dataset based on query content

2. **Simplification Opportunities**: 
   - One-click activation (no confirmation needed)
   - Clear status indicators
   - Automatic deactivation of previous when activating new

3. **Transition Smoothness**: 
   - Instant activation (no loading required)
   - Smooth status updates
   - No interruption to current workflow

4. **User Trust**: 
   - Clear indication of which dataset is active
   - Reliable switching behavior
   - Consistent status across all interface areas

5. **Cognitive Load**: 
   - Simple on/off state
   - Visual indicators are clear
   - No complex configuration needed

---

## Related Flows

- [Upload New Dataset](./corpus-upload.md) - Add datasets to activate
- [View Dataset Details](./view-dataset-details.md) - Verify dataset before activating
- [Chat with Dataset Query Enabled](../02-chat-interactions/rag-enabled-chat.md) - Use activated dataset
- [Create New Blockify Job](../05-blockify-processing/create-blockify-job.md) - Create datasets
- [Select Active Embedding Model](../03-model-management/select-embedding-model.md) - Required for datasets

---

## Technical References

**Knowledge Base Sections**:
- src/pages/settings.js - Settings interface
- src/pages/datasets.js - Dataset list with activation
- src/components/ui/corpus-chooser.js - Chat dataset selector
- src/handlers/index.js - updateUserSettings RPC
- src/localdb/settings.js - Active dataset persistence

**Key Components**:
- Dataset selector dropdown
- Status badges (ACTIVE/INACTIVE)
- Activation/deactivation controls

---

## Version History

| Date | Version | Author | Changes |
|------|---------|--------|---------|
| 2025-10-04 | 1.1 | [Iternal Technologies](https://iternal.ai/airgapai) | Initial comprehensive documentation |

---

## Notes

**Important Considerations**:
- Only one dataset can be active at a time (system limitation)
- Activating a dataset doesn't automatically enable dataset queries in chat (separate toggle)
- Active dataset persists across application restarts
- Switching datasets takes effect immediately, no reload required
- Deactivating all datasets disables dataset query functionality

**Best Practices**:
- Activate the dataset relevant to your current task or project
- Verify dataset contents before activating if unsure
- Name datasets clearly so correct one is obvious to select
- Keep related information in single datasets rather than splitting
- Periodically review which dataset is active to avoid querying wrong information

**Common User Questions**:
- "Can I use multiple datasets at once?" - No, only one can be active at a time
- "Do I need to activate a dataset to see its contents?" - No, can view any dataset; activation only affects chat queries
- "What happens to my chat if I switch datasets mid-conversation?" - Next query uses new dataset; previous messages unchanged
- "Why can't I activate a dataset?" - Check that its embedding model is uploaded and matches

