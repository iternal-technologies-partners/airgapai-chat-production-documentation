# Delete a Model

## Overview
**Flow ID**: `delete-model`  
**Category**: Model Management  
**Estimated Duration**: 30 seconds  
**User Role**: All Users  
**Complexity**: Simple  

**Purpose**: Permanently remove an AI model from the application to free up disk space or clean up unused models.

---

## Trigger

**What initiates this flow:**
- [x] User manually initiates

**Specific trigger**: User wants to remove model, typically because:
- Model no longer needed
- Freeing disk space
- Removing duplicate or outdated model
- Cleaning up after testing

---

## Prerequisites

**Before starting, users must have:**
- [x] At least one model uploaded
- [x] Model is not currently active/in use (recommended)

---

## User Intent Analysis

### Primary Intent
Remove unwanted model to free space or organize model library.

### Secondary Intents
- Manage disk space
- Remove outdated models
- Clean up test models

---

## Step-by-Step Flow

### Main Path

**Step 1: Navigate to Models List**
- **User Action**: Settings > Chat AI Models or Models tab
- **System Response**: Models list displays

**Step 2: Locate Model to Delete**
- **User Action**: Find target model in list
- **UI Elements Visible**: 
  - Model list with delete buttons/icons
  - Each model has trash icon or "Delete" button

**Step 3: Click Delete**
- **User Action**: Click delete icon/button for target model
- **System Response**: Confirmation dialog appears
- **UI Elements Visible**: 
  - Confirmation modal
  - Warning: "Are you sure? This cannot be undone"
  - Model name shown
  - "Cancel" and "Delete" buttons

**Step 4: Confirm Deletion**
- **User Action**: Click "Delete" or "Confirm"
- **System Response**: 
  - Model deleted
  - File removed from disk
  - Model removed from database
  - Model disappears from list
- **UI Elements Visible**: 
  - Brief success message
  - Updated models list without deleted model

**Final Step: Model Deleted**
- **Success Indicator**: 
  - Model no longer in list
  - Disk space freed
  - Cannot select deleted model
- **System State Change**: 
  - Model file deleted
  - Database record removed
  - If was active model, may need to select replacement
- **Next Possible Actions**: 
  - Select different model if deleted was active
  - Upload replacement model
  - Continue with remaining models

---

## Error States & Recovery

### Error 1: Cannot Delete Active Model
**Cause**: Model currently in use  
**User Experience**: 
- Error: "Cannot delete active model" or "Model in use"
- Deletion blocked

**Recovery Steps**:
1. Select different model as active first
2. Then delete
3. Or deactivate model if option exists

### Error 2: Deletion Fails
**Cause**: File system permissions or locks  
**User Experience**: 
- Error message
- Model remains in list

**Recovery Steps**:
1. Try again
2. Restart application
3. Verify file permissions

---

## Pain Points & Friction

**Identified Issues**:

1. **No Undo**
   - **Impact**: Permanent deletion; must re-upload if mistake
   - **Potential Improvement**: Trash/recycle bin, or move to inactive state instead

---

## Design Considerations

**Following Contextual Design Principles**:

1. **User Trust**: Confirmation prevents accidents
2. **Cognitive Load**: Simple delete action

---

## Related Flows

- [Upload Large Language Model](./llm-model-upload.md) - Add replacement if needed
- [Select Active Chat Model](./select-llm-model.md) - Choose replacement

---

## Technical References

**Knowledge Base Sections**:
- src/pages/settings.js - Model management
- src/localdb/base.js - Model deletion

---

## Version History

| Date | Version | Author | Changes |
|------|---------|--------|---------|
| 2025-10-04 | 1.1 | [Iternal Technologies](https://iternal.ai/airgapai) | Initial documentation |

---

## Notes

**Important Considerations**:
- Deletion is permanent
- Frees disk space (models are large)
- Cannot delete last model if it's in use
- Should select replacement before deleting active model

**Best Practices**:
- Verify model not needed before deleting
- Keep backup copy externally if model is rare
- Select replacement first if deleting active model

**Common User Questions**:
- "Can I recover deleted model?" - No, must re-upload
- "Will this break my chats?" - Historical chats preserved, but can't continue with deleted model
- "How much space will I free?" - Model size shown in list (typically 2-50GB)

