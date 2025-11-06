# Select Embedding Model for Job

## Overview
**Flow ID**: `select-embedding-for-job`  
**Category**: Blockify Processing  
**Estimated Duration**: 1 minute  
**User Role**: All Users  
**Complexity**: Simple  

**Purpose**: Choose which embedding model will be used to generate vector representations of processed chunks. Required for creating searchable dataset. Model selection depends on whether creating new dataset or adding to existing one.

---

## Trigger

**What initiates this flow:**
- [x] User manually initiates

**Specific trigger**: During job creation, must select embedding model for final dataset creation.

---

## Prerequisites

**Before starting, users must have:**
- [x] At least one embedding model uploaded
- [x] Job creation form open
- [x] Dataset destination selected (new or existing)

---

## User Intent Analysis

### Primary Intent
Select appropriate embedding model for generating vectors that enable semantic search of processed documents.

### Secondary Intents
- Match model to dataset requirements
- Optimize search quality vs. speed
- Ensure consistency with existing datasets

---

## Step-by-Step Flow

### Main Path A - New Dataset (Happy Path)

**Step 1: Locate Embedding Model Selector**
- **User Action**: On job creation form with "Create New Dataset" selected, find embedding model dropdown
- **System Response**: Dropdown is active and available
- **UI Elements Visible**: 
  - Label: "Embedding Model"
  - Dropdown selector
  - May show currently selected model or "Select model..."
  - List of available embedding models

**Step 2: Open Dropdown**
- **User Action**: Click embedding model dropdown
- **System Response**: List of models appears
- **UI Elements Visible**: 
  - Dropdown list showing:
    - Model names (e.g., "Jina Embeddings", "BGE-Small")
    - Model types (all show "Embeddings")
    - Current selection highlighted if any

**Step 3: Select Embedding Model**
- **User Action**: Click desired embedding model
- **System Response**: 
  - Dropdown closes
  - Selected model appears in field
  - This model will be used for all items in new dataset
- **UI Elements Visible**: 
  - Selected model name in dropdown
  - Model confirmed for use

**Final Step: Embedding Model Selected for New Dataset**
- **Success Indicator**: Model selected and shown
- **System State Change**: Job will use this model for embedding generation
- **Next Actions**: Continue job creation (upload files, set chunks, start)

---

## Alternative Path B - Existing Dataset

**Step 1: View Locked Model**
- **User Action**: When existing dataset selected as target, observe embedding model field
- **System Response**: Embedding model field is disabled/locked
- **UI Elements Visible**: 
  - Embedding model field showing dataset's existing model
  - Field grayed out or marked as read-only
  - Cannot change selection
  - Tooltip or note: "Model locked to dataset's embedding model"

**Step 2: Verify Model Matches Needs**
- **User Action**: Confirm dataset's embedding model is acceptable
- **System Response**: Model name displayed but not editable
- **UI Elements Visible**: Read-only model name

**Final Step: Locked to Dataset's Model**
- **Success Indicator**: Understand model is predetermined by dataset choice
- **System State Change**: Job will use dataset's embedding model
- **Next Actions**: Continue job creation with locked model

---

## Error States & Recovery

### Error 1: No Embedding Models Available
**Cause**: No embedding models uploaded  
**User Experience**: 
- Dropdown empty or shows "No models available"
- Error message: "Embedding model required"
- Cannot proceed with job

**Recovery Steps**:
1. Navigate to Settings
2. Upload embedding model (see embedding-model-upload.md)
3. Return to job creation
4. Model should now be selectable

### Error 2: Wrong Model Selected
**Cause**: User selects model then realizes it's incompatible  
**User Experience**: 
- Job creates with wrong model
- Dataset searches may not work optimally

**Recovery Steps**:
1. Before starting job: Select different model from dropdown
2. After job started: Cannot change; must cancel and recreate job
3. Prevention: Verify model selection before clicking "Start"

**QA Note**: No validation error for wrong model; user judgment call on which is "right."

---

## Pain Points & Friction

**Identified Issues**:

1. **Cannot Change Model for Existing Dataset**
   - **Impact**: Locked in once dataset created
   - **Frequency**: When adding to existing datasets
   - **Potential Improvement**: Explain why upfront, technical documentation

2. **No Guidance on Model Selection**
   - **Impact**: Users unsure which embedding model to use
   - **Frequency**: Users with multiple embedding models
   - **Potential Improvement**: 
     - Recommendations: "Best for general use", "Fastest", "Most accurate"
     - Model comparison information
     - Explain differences between models

3. **Auto-Selection Inconsistent**
   - **Impact**: Sometimes auto-selects first model, sometimes doesn't
   - **Frequency**: New dataset creation
   - **Potential Improvement**: 
     - Always auto-select if only one model
     - Remember last-used model as default

---

## Design Considerations

**Following Contextual Design Principles**:

1. **Automation Opportunities**: 
   - Auto-select if only one embedding model available
   - Remember last-used model as default
   - Recommend model based on dataset size/type

2. **Simplification Opportunities**: 
   - Hide selection if only one model exists
   - Smart defaults
   - Clear "recommended" badge on preferred model

3. **User Trust**: 
   - Clear indication which model will be used
   - Locked state prevents accidental changes for existing datasets
   - Transparent about model's role

4. **Cognitive Load**: 
   - Simple dropdown selection
   - Don't require deep understanding of embeddings
   - Clear when choice is available vs. locked

---

## Related Flows

- [Select Target Dataset for Job](./select-corpus-for-job.md) - Determines if model is selectable
- [Upload Embedding Model](../03-model-management/embedding-model-upload.md) - Add models to choose from
- [Create New Blockify Job](./create-blockify-job.md) - Parent workflow
- [Select Active Embedding Model](../03-model-management/select-embedding-model.md) - Global embedding selection

---

## Technical References

**Knowledge Base Sections**:
- src/components/blockify-corpus/new-job-screen.js - Embedding model selector
- src/components/ui/model-selection.js - Model selection component

---

## Version History

| Date | Version | Author | Changes |
|------|---------|--------|---------|
| 2025-10-04 | 1.1 | [Iternal Technologies](https://iternal.ai/airgapai) | Initial documentation |

---

## Notes

**Important Considerations**:
- Embedding model is permanent for each dataset
- Cannot change model after dataset created
- Must use same model when adding to existing dataset
- All items in dataset must use same embedding model for search to work

**Model Selection Scenarios**:
- **New Dataset**: Can choose any available embedding model
- **Existing Dataset**: Automatically uses dataset's model (cannot change)
- **No Models Available**: Must upload embedding model first

**Why Model Cannot Change**:
Embedding models create specific vector representations. Different models create different vectors, so all items in dataset must use same model for semantic search to work correctly.

**Best Practices**:
- Choose embedding model carefully for new datasets (permanent)
- Use consistent model across related datasets if possible
- Document which model used with dataset for future reference
- If unsure, use recommended general-purpose model (e.g., Jina)

**Common User Questions**:
- "Which embedding model should I choose?" - Jina or BGE models good for general use
- "Can I change model later?" - No, permanent for dataset
- "What if I picked wrong model?" - Must create new dataset with correct model
- "Why is model locked for existing dataset?" - Must match for semantic search consistency
- "Do different models give different search results?" - Yes, significantly different

