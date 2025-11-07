# Select Target Dataset for Job

## Overview
**Flow ID**: `select-corpus-for-job`  
**Category**: Blockify Processing  
**Estimated Duration**: 1 minute  
**User Role**: All Users  
**Complexity**: Simple  

**Purpose**: Choose whether to create new dataset or add to existing dataset when creating blockify/chunking job. Determines where processed results will be stored.

---

## Trigger

**What initiates this flow:**
- [x] User manually initiates

**Specific trigger**: During job creation, user must specify target dataset for processed items.

---

## Prerequisites

**Before starting, users must have:**
- [x] Job creation screen open
- [x] Understanding of dataset purpose

---

## User Intent Analysis

### Primary Intent
Select appropriate dataset destination for job results - either creating new dataset or expanding existing one.

### Secondary Intents
- Organize results appropriately
- Keep related content together
- Create separate datasets for different topics

---

## Step-by-Step Flow

### Main Path - Create New Dataset

**Step 1: Locate Dataset Selector**
- **User Action**: On job creation form, find "Target Dataset" or "Select Dataset" dropdown
- **System Response**: Dropdown control visible
- **UI Elements Visible**: 
  - Label: "Target Dataset" or "Destination Dataset"
  - Dropdown showing current selection (default: "Create New Dataset")
  - List includes:
    - **"Create New Dataset"** (at top)
    - Any existing datasets below

**Step 2: Keep "Create New" Selected**
- **User Action**: Keep default "Create New Dataset" selection or explicitly select it
- **System Response**: 
  - Form shows fields for new dataset
- **UI Elements Visible**: 
  - "Dataset Name" text input field appears
  - Embedding model selector appears
  - Both fields required and enabled

**Step 3: Name New Dataset**
- **User Action**: Type descriptive name for new dataset
- **System Response**: Text appears as typed
- **UI Elements Visible**: 
  - Text input with dataset name
  - Validation may show if name already exists

**Step 4: Select Embedding Model for New Dataset**
- **User Action**: Choose embedding model from dropdown
- **System Response**: Model selected
- **UI Elements Visible**: 
  - Embedding model dropdown
  - Selected model shown
- **Note**: This embedding model will be permanently associated with this dataset

**Final Step: New Dataset Selected**
- **Success Indicator**: 
  - New dataset will be created from job results
  - Dataset name and model configured
- **System State Change**: Job configured to create new dataset
- **Next Possible Actions**: Continue job creation workflow

---

## Alternative Path - Add to Existing Dataset

**Step 1: Select Existing Dataset**
- **User Action**: Click dataset dropdown, select existing dataset from list
- **System Response**: 
  - Selection updates
  - Form adjusts for existing dataset
- **UI Elements Visible**: 
  - Selected existing dataset name shown
  - Dataset name field disappears (read-only, shows selected name)
  - Embedding model field shows dataset's model (locked/disabled)
  - Cannot change embedding model (must match dataset)

**Step 2: Verify Correct Dataset**
- **User Action**: Confirm correct dataset selected
- **System Response**: Dataset details shown
- **UI Elements Visible**: 
  - Dataset name (read-only)
  - Embedding model (locked to dataset's model)
  - Possibly: Current item count shown

**Final Step: Existing Dataset Selected**
- **Success Indicator**: 
  - Job will add to existing dataset
  - Embedding model matches
- **System State Change**: Job configured to expand existing dataset
- **Next Actions**: Continue job creation

---

## Error States & Recovery

### Error 1: Dataset Name Already Exists
**Cause**: Typed name matches existing dataset  
**User Experience**: 
- Error: "Dataset name already exists"
- Cannot proceed

**Recovery Steps**:
1. Choose different unique name
2. Or select existing dataset to add to it instead

### Error 2: No Embedding Model Selected
**Cause**: Forgot to select embedding model for new dataset  
**User Experience**: 
- Cannot proceed
- Field may have validation error indicator

**Recovery Steps**:
1. Select embedding model from dropdown
2. Required field; must complete

**QA Note**: Form validation should prevent proceeding without required fields.

---

## Pain Points & Friction

**Identified Issues**:

1. **Cannot Change Embedding Model for Existing Dataset**
   - **Impact**: Locked to dataset's original model
   - **Frequency**: When wanting to use different model
   - **Potential Improvement**: Explain why model must match

2. **No Preview of Existing Dataset Contents**
   - **Impact**: Can't verify adding to correct dataset
   - **Potential Improvement**: 
     - Show dataset summary (item count, recent items)
     - Quick preview button

---

## Design Considerations

**Following Contextual Design Principles**:

1. **Automation Opportunities**: Auto-suggest dataset name from files
2. **Simplification Opportunities**: Smart defaults
3. **User Trust**: Clear indication of new vs. existing

---

## Related Flows

- [Create New Blockify Job](./create-blockify-job.md) - Parent workflow
- [Upload New Dataset](../04-dataset-management/corpus-upload.md) - Alternative creation method
- [View Dataset List](../04-dataset-management/view-dataset-list.md) - See existing datasets

---

## Technical References

**Knowledge Base Sections**:
- src/components/blockify-corpus/new-job-screen.js - Dataset selection UI
- src/constants/datasets.js - CREATE_NEW_CORPUS_ID constant

---

## Version History

| Date | Version | Author | Changes |
|------|---------|--------|---------|
| 2025-10-04 | 1.1 | [Iternal Technologies](https://iternal.ai/airgapai) | Initial documentation |

---

## Notes

**Important Considerations**:
- Can create new dataset or add to existing, not both in single job
- Embedding model for dataset is permanent (cannot change after creation)
- Adding to existing dataset increases its size
- New dataset name must be unique

**Best Practices**:
- Create new datasets for distinct topics
- Add to existing for related content
- Use clear, descriptive dataset names
- Verify embedding model before finalizing

**Common User Questions**:
- "Can I add to multiple datasets?" - No, one target per job
- "Can I change my mind after job starts?" - No, must cancel and recreate job
- "What if I select wrong dataset?" - Cannot change during processing; verify before starting
- "Can I split job results across datasets?" - No, all results go to one dataset

