# View Model Information

## Overview
**Flow ID**: `view-model-info`  
**Category**: Model Management  
**Estimated Duration**: 30 seconds  
**User Role**: All Users  
**Complexity**: Simple  

**Purpose**: View detailed information about an uploaded model including its name, type, file path, capabilities, and configuration. Helps users understand model specifications and verify correct model is being used.

---

## Trigger

**What initiates this flow:**
- [x] User manually initiates

**Specific trigger**: User wants to view model details to verify specifications, understand capabilities, or troubleshoot issues.

---

## Prerequisites

**Before starting, users must have:**
- [x] At least one model uploaded
- [x] Access to Settings page

---

## User Intent Analysis

### Primary Intent
View comprehensive information about a model to understand its specifications and capabilities.

### Secondary Intents
- Verify correct model uploaded
- Check model configuration
- Understand model limitations
- Troubleshoot issues

---

## Step-by-Step Flow

### Main Path

**Step 1: Navigate to Models List**
- **User Action**: Go to Settings > Chat AI Models or Models tab
- **System Response**: Models list displays

**Step 2: Locate Model**
- **User Action**: Find model in list
- **UI Elements Visible**: 
  - Model list/table showing:
    - Model names
    - Types (LLM, Embeddings, Blockify)
    - Paths
    - Status indicators

**Step 3: View Model Information**
- **User Action**: Click on model name or "View" button if available
- **System Response**: Model information displays (may be inline card or modal)
- **UI Elements Visible**: 
  - Model details card/modal showing:
    - **Model Name**: Full name
    - **Model Type**: LLM, Embeddings, or Blockify
    - **File Path**: Where model is stored
    - **Max Tokens**: Context window size (for LLMs)
    - **File Size**: Model size in GB
    - **Upload Date**: When added
    - **Status**: Active/Inactive/Ready
    - Possibly: Memory requirements, capabilities, version

**Step 4: Review Information**
- **User Action**: Read through model details
- **System Response**: Information displayed statically

**Final Step: Model Information Viewed**
- **Success Indicator**: 
  - Understood model specifications
  - Verified model details
  - Can make informed decisions
- **Next Possible Actions**: 
  - Select model as active
  - Run benchmark on model
  - Delete model if not needed
  - Return to models list

---

## Error States & Recovery

**QA Note**: Viewing information is read-only operation with no error states beyond model not existing.

---

## Pain Points & Friction

**Identified Issues**:

1. **Limited Information Shown**
   - **Impact**: May not show all relevant specifications
   - **Potential Improvement**: More comprehensive details, performance data

---

## Design Considerations

**Following Contextual Design Principles**:

1. **Simplification Opportunities**: Show only essential info by default
2. **User Trust**: Accurate, complete information

---

## Related Flows

- [Upload Large Language Model](./llm-model-upload.md) - How models are added
- [Select Active Chat Model](./select-llm-model.md) - Using model information to choose

---

## Technical References

**Knowledge Base Sections**:
- src/components/ui/model-selection.js - Model info display
- src/pages/settings.js - Models list

---

## Version History

| Date | Version | Author | Changes |
|------|---------|--------|---------|
| 2025-10-04 | 1.1 | [Iternal Technologies](https://iternal.ai/airgapai) | Initial documentation |

---

## Notes

**Best Practices**:
- Verify model specifications match expectations
- Check path to confirm model file location
- Review before running benchmarks

**Common User Questions**:
- "Where is my model stored?" - Path shown in model info
- "How do I check model size?" - Shown in file size field
- "What do these specifications mean?" - Consult model documentation

