# Upload Embedding Model

## Overview
**Flow ID**: `embedding-model-upload`  
**Category**: Model Management  
**Estimated Duration**: 5-15 minutes  
**User Role**: All Users  
**Complexity**: Simple  

**Purpose**: Upload an embedding model that converts text into numerical vectors for semantic search. Required for dataset query functionality and creating searchable datasets from documents.

---

## Trigger

**What initiates this flow:**
- [x] User manually initiates

**Specific trigger**: User needs embedding model for dataset features, typically because:
- Want to use dataset query in conversations
- Creating blockify job that requires embeddings
- System prompts for missing embedding model

---

## Prerequisites

**Before starting, users must have:**
- [x] Application running
- [x] Embedding model file (compatible format)
- [x] Sufficient disk space (1-5GB typically)

---

## User Intent Analysis

### Primary Intent
Add embedding model to enable dataset search and document processing capabilities.

### Secondary Intents
- Enable RAG (dataset query) features
- Prepare for blockify jobs
- Test different embedding models

---

## Step-by-Step Flow

### Main Path

**Step 1: Navigate to Settings**
- **User Action**: Click "Settings" in navigation
- **System Response**: Settings page loads
- **UI Elements Visible**: Settings tabs including "Embedding Models" or similar

**Step 2: Access Embedding Models Section**
- **User Action**: Click "Embedding Models" tab
- **System Response**: Embedding models list displays
- **UI Elements Visible**: 
  - List of existing embedding models (if any)
  - "Add Model" or "Upload Model" button
  - Model details: name, type, path

**Step 3: Click Add Model**
- **User Action**: Click "Add Model" button
- **System Response**: Upload modal appears
- **UI Elements Visible**: 
  - Upload modal with file selector
  - Model name field
  - Model type (auto: "Embeddings")
  - Save/Cancel buttons

**Step 4: Select Model File**
- **User Action**: Click "Choose File", navigate to model file, select, click "Open"
- **System Response**: 
  - Filename appears
  - Model name auto-populates
  - Model type auto-set to "Embeddings"

**Step 5: Confirm and Upload**
- **User Action**: Review name and type, click "Save"
- **System Response**: 
  - Upload begins
  - Progress bar shows advancement
  - May take 5-15 minutes for large models

**Step 6: Upload Completes**
- **User Action**: Wait for upload to finish
- **System Response**: 
  - Success message
  - Modal closes
  - Model appears in list
- **UI Elements Visible**: New embedding model in models list

**Final Step: Embedding Model Available**
- **Success Indicator**: 
  - Model in list
  - Can be selected for datasets
  - Can be used for blockify jobs
- **System State Change**: 
  - Embedding model stored
  - Available for selection
  - Can create embeddings
- **Next Possible Actions**: 
  - Select as active embedding model
  - Create dataset or blockify job
  - Upload additional models

---

## Error States & Recovery

### Error 1: Incompatible Format
**Cause**: File not compatible embedding model format  
**User Experience**: 
- Error: "Incompatible format" or "Not an embedding model"
- Upload fails

**Recovery Steps**:
1. Verify file is embedding model (not LLM)
2. Check compatible formats
3. Obtain correct model file
4. Retry upload

### Error 2: Model Loading Fails
**Cause**: Corrupted file or insufficient resources  
**User Experience**: 
- Upload succeeds but model won't load for use
- Error when trying to use model

**Recovery Steps**:
1. Delete model
2. Re-download model file
3. Verify file integrity
4. Re-upload

---

## Pain Points & Friction

**Identified Issues**:

1. **Similar to LLM Upload Process**
   - **Impact**: Users may confuse embedding and LLM models
   - **Improvement**: Clear distinction in UI, explanations of purpose

2. **No Guidance on Which Model to Use**
   - **Impact**: Users uncertain which embedding model to choose
   - **Improvement**: Recommendations, comparisons, purpose explanation

---

## Design Considerations

**Following Contextual Design Principles**:

1. **Automation Opportunities**: Auto-detect embedding vs LLM model type
2. **Simplification Opportunities**: Same interface as LLM upload
3. **User Trust**: Clear success confirmation
4. **Cognitive Load**: Minimal required knowledge

---

## Related Flows

- [Upload Large Language Model](./llm-model-upload.md) - Similar process
- [Select Active Embedding Model](./select-embedding-model.md) - Use uploaded model
- [Upload New Dataset](../04-dataset-management/corpus-upload.md) - Requires embedding model
- [Create New Blockify Job](../05-blockify-processing/create-blockify-job.md) - Requires embedding model

---

## Technical References

**Knowledge Base Sections**:
- src/components/ui/upload-model-modal.js - Upload interface
- src/handlers/upload/upload-handler.js - File processing
- src/engines/embedding.js - Embedding model usage

---

## Version History

| Date | Version | Author | Changes |
|------|---------|--------|---------|
| 2025-10-04 | 1.1 | [Iternal Technologies](https://iternal.ai/airgapai) | Initial comprehensive documentation |

---

## Notes

**What Are Embedding Models**:
Embedding models convert text into numerical vectors (arrays of numbers) that capture semantic meaning. Required for dataset search functionality.

**Common Embedding Models**:
- Jina Embeddings (general purpose)
- BGE models (high quality)
- MiniLM models (fast, smaller)

**Best Practices**:
- Upload embedding model before creating datasets
- Use same embedding model for all datasets if possible
- Smaller embedding models process faster
- Larger models may provide better search quality

**Common User Questions**:
- "What's the difference from chat models?" - Embeddings for search, LLMs for conversation
- "Do I need this if I don't use datasets?" - No, only needed for dataset query features
- "Can I use multiple embedding models?" - Yes, different datasets can use different models
- "Which embedding model is best?" - Depends on language and accuracy needs; start with Jina

