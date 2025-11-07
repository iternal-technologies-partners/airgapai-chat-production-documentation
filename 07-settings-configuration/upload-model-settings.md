# Upload Model from Settings Page

## Overview
**Flow ID**: `upload-model-settings`  
**Category**: Settings & Configuration  
**Estimated Duration**: 5-30 minutes  
**User Role**: All Users  
**Complexity**: Simple  

**Purpose**: Upload AI models (language or embedding models) directly from Settings page through dedicated model management interface. This is the standard location for adding new models outside of onboarding.

---

## Trigger

**What initiates this flow:**
- [x] User manually initiates

**Specific trigger**: User needs to add new model after initial setup, from Settings page context.

---

## User Intent Analysis

### Primary Intent
Add new AI model to application through Settings interface (standard upload location).

### Secondary Intents
- Expand model library
- Test new models
- Replace outdated models
- Enable new capabilities

---

## Step-by-Step Flow

### Main Path

**Step 1: Navigate to Settings**
- **User Action**: Click "Settings" in navigation
- **System Response**: Settings page loads

**Step 2: Select Model Type Tab**
- **User Action**: Click "Chat AI Models" tab for language models OR "Embedding Models" tab for embedding models
- **System Response**: Corresponding models list displays
- **UI Elements Visible**: 
  - Active tab highlighted
  - List of existing models (if any)
  - "Add Model" or "Upload Model" button prominent

**Step 3: Click Add Model**
- **User Action**: Click "Add Model" button
- **System Response**: Upload modal appears
- **UI Elements Visible**: 
  - Upload modal
  - File selector
  - Model name field
  - Model type dropdown (may be pre-set based on tab)
  - Save/Cancel buttons

**Step 4-8: Complete Upload Process**
- **User Action**: Follow standard model upload process (see llm-model-upload.md or embedding-model-upload.md)
- **System Response**: Model uploads and becomes available
- **Note**: Process identical to model upload flows but accessed via Settings

**Final Step: Model Uploaded from Settings**
- **Success Indicator**: 
  - Model appears in appropriate models list
  - Available for selection and use
- **System State Change**: Model added to system
- **Next Possible Actions**: 
  - Select model as active
  - Run benchmarks
  - Use in conversations or jobs

---

## Alternative Paths & Strategies

### Strategy A: Upload Multiple Models Sequentially
**When to use**: Adding several models at once

**Steps**:
1. Upload first model
2. When modal closes, immediately click "Add Model" again
3. Upload next model
4. Repeat until all models uploaded

---

## Error States & Recovery

**Note**: Error states identical to standard model upload flows (see llm-model-upload.md, embedding-model-upload.md).

---

## Design Considerations

**Following Contextual Design Principles**:

1. **Simplification Opportunities**: Single interface for all model uploads
2. **User Trust**: Familiar process from onboarding

---

## Related Flows

- [Upload Large Language Model](../03-model-management/llm-model-upload.md) - Detailed LLM upload process
- [Upload Embedding Model](../03-model-management/embedding-model-upload.md) - Detailed embedding upload
- [Navigate Between Settings Tabs](./navigate-settings-tabs.md) - Access different model tabs

---

## Technical References

**Knowledge Base Sections**:
- src/pages/settings.js - Settings page with model management
- src/components/ui/upload-model-modal.js - Upload modal

---

## Version History

| Date | Version | Author | Changes |
|------|---------|--------|---------|
| 2025-10-04 | 1.1 | [Iternal Technologies](https://iternal.ai/airgapai) | Initial documentation |

---

## Notes

**Important Considerations**:
- This is the standard location for model uploads (outside onboarding)
- Process identical to onboarding model upload
- Can upload language models, embedding models, or blockify models
- Tab selection determines default model type

**Difference from Onboarding Upload**:
- Accessed manually via Settings (not wizard)
- No step progression indicators
- No default template or configuration
- Standalone operation

**Best Practices**:
- Upload models from Settings for all post-setup additions
- Use appropriate tab for model type
- Verify model before uploading if possible

**Common User Questions**:
- "Is this the same as onboarding upload?" - Yes, same process, different access point
- "Where should I upload models?" - Settings is standard location for normal operations
- "Can I upload while benchmark running?" - Not recommended; may interfere

