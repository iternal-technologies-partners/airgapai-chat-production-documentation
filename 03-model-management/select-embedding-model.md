# Select Active Embedding Model

## Overview
**Flow ID**: `select-embedding-model`  
**Category**: Model Management  
**Estimated Duration**: 1-2 minutes  
**User Role**: All Users  
**Complexity**: Simple  

**Purpose**: Choose which embedding model will be used for converting text into vectors for semantic search. This model is used when creating datasets, querying datasets during chat, and processing documents.

---

## Trigger

**What initiates this flow:**
- [x] User manually initiates

**Specific trigger**: User needs to select or change embedding model, typically because:
- Setting up dataset features for first time
- Switching between different embedding models
- Just uploaded new embedding model
- Creating dataset that requires specific embedding model

---

## Prerequisites

**Before starting, users must have:**
- [x] Application running
- [x] At least one embedding model uploaded
- [x] Access to Settings page

---

## User Intent Analysis

### Primary Intent
Set which embedding model will be used for semantic search and dataset operations.

### Secondary Intents
- Optimize search quality vs. speed
- Match embedding model to dataset requirements
- Test different embedding approaches

---

## Step-by-Step Flow

### Main Path

**Step 1: Navigate to Settings**
- **User Action**: Click "Settings" in navigation
- **System Response**: Settings page loads

**Step 2: Find Embedding Model Setting**
- **User Action**: Look for embedding model configuration (may be in Chat Options, Admin Overrides, or dedicated Embeddings tab)
- **System Response**: Setting area displays
- **UI Elements Visible**: 
  - Embedding model selector or dropdown
  - Currently selected model shown
  - List of available embedding models
- **Visual Cues**: Dropdown or selector interface

**Step 3: Open Embedding Model Dropdown**
- **User Action**: Click embedding model dropdown
- **System Response**: List of available embedding models appears
- **UI Elements Visible**: 
  - Dropdown list showing:
    - Model names (e.g., "Jina Embeddings", "BGE-Small")
    - Model types (all show "Embeddings")
    - Current selection marked
  - May show model details (dimensions, size)

**Step 4: Select Different Model**
- **User Action**: Click on desired embedding model
- **System Response**: 
  - Dropdown closes
  - Selected model becomes active
  - Model may begin loading
- **UI Elements Visible**: 
  - Selected model name in dropdown
  - Loading indicator if model needs initialization
  - Save button (if not auto-save)

**Step 5: Model Loads (if needed)**
- **User Action**: Wait for embedding model to initialize (typically 10-30 seconds)
- **System Response**: 
  - Model loads into background worker
  - Progress indicated
- **UI Elements Visible**: 
  - Loading status
  - "Initializing embedding model..."

**Step 6: Selection Completes**
- **User Action**: Verify selection successful
- **System Response**: 
  - Model ready
  - Success indication
  - Settings saved
- **UI Elements Visible**: 
  - Selected model shown
  - Ready status indicator
  - Can proceed with dataset operations

**Final Step: Embedding Model Selected**
- **Success Indicator**: 
  - New model active
  - Ready for dataset operations
  - Settings persisted
- **System State Change**: 
  - New embedding model active
  - Future dataset creations use this model
  - Dataset queries use this model
- **Next Possible Actions**: 
  - Create dataset using this model
  - Upload or activate dataset
  - Use dataset query in chat

---

## Error States & Recovery

### Error 1: No Embedding Models Available
**Cause**: None uploaded yet  
**User Experience**: 
- Dropdown empty or shows "No models"
- Cannot select

**Recovery Steps**:
1. Upload embedding model first
2. Return and select

### Error 2: Model Loading Fails
**Cause**: Insufficient memory or file error  
**User Experience**: 
- Error during loading
- Model won't activate

**Recovery Steps**:
1. Try different embedding model
2. Check system resources
3. Restart application

---

## Pain Points & Friction

**Identified Issues**:

1. **Unclear Difference Between Embedding Models**
   - **Impact**: Don't know which to choose
   - **Potential Improvement**: 
     - Model descriptions
     - Comparison chart
     - Recommendations

2. **No Indication Which Datasets Use Which Model**
   - **Impact**: Changing model may break existing datasets
   - **Potential Improvement**: 
     - Show dataset compatibility
     - Warn before changing
     - List datasets using each model

---

## Design Considerations

**Following Contextual Design Principles**:

1. **Automation Opportunities**: Auto-select if only one available
2. **Simplification Opportunities**: Default to recommended model
3. **User Trust**: Clear indication of active model

---

## Related Flows

- [Upload Embedding Model](./embedding-model-upload.md) - Add models to select
- [Upload New Dataset](../04-dataset-management/corpus-upload.md) - Uses embedding model
- [Create New Blockify Job](../05-blockify-processing/create-blockify-job.md) - Requires embedding model

---

## Technical References

**Knowledge Base Sections**:
- src/components/ui/model-selection.js - Model selector
- src/engines/embedding.js - Embedding model
- src/actions/embedding.js - Model selection actions

---

## Version History

| Date | Version | Author | Changes |
|------|---------|--------|---------|
| 2025-10-04 | 1.1 | [Iternal Technologies](https://iternal.ai/airgapai) | Initial documentation |

---

## Notes

**Embedding Model Purpose**:
Converts text to numerical vectors for semantic similarity search. Required for:
- Creating searchable datasets
- Querying datasets during chat
- Blockify job completion

**Best Practices**:
- Choose model before creating datasets
- Use same model for all related datasets
- Smaller models faster, larger may have better accuracy
- Keep model consistent once datasets created

**Common User Questions**:
- "Which embedding model is best?" - Jina or BGE models recommended for general use
- "Can I change models later?" - Yes, but doesn't affect existing datasets
- "Do I need this if I don't use datasets?" - No, only for dataset features
- "What happens if I change models?" - New datasets use new model; existing unchanged

