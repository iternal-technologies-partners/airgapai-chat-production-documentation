# Create Basic Chunking Job

## Overview
**Flow ID**: `create-chunking-job`  
**Category**: Blockify Processing  
**Estimated Duration**: 5-15 minutes (setup); processing faster than blockify  
**User Role**: All Users  
**Complexity**: Complex  

**Purpose**: Create job that splits documents into basic chunks without AI structuring. Faster and simpler than blockify mode, suitable when documents don't need AI-enhanced structure or when speed is priority over sophisticated organization.

---

## Trigger

**What initiates this flow:**
- [x] User manually initiates

**Specific trigger**: User wants searchable dataset from documents but doesn't need AI-powered structuring.

---

## Prerequisites

**Before starting, users must have:**
- [x] Application running
- [x] Embedding model uploaded (for dataset creation)
- [x] Document files ready to upload
- [x] Understanding that chunking is mechanical splitting (not AI-enhanced)

---

## User Intent Analysis

### Primary Intent
Process documents into simple, evenly-sized chunks for dataset creation without AI structuring, prioritizing speed over sophisticated organization.

### Secondary Intents
- Create dataset faster than blockify mode
- Avoid blockify model requirements
- Process documents when structure isn't critical
- Save computational resources

---

## Step-by-Step Flow

### Main Path (Happy Path)

**Step 1: Navigate to Blockify Page**
- **User Action**: Click "Blockify" in navigation
- **System Response**: Blockify page loads with mode selection
- **UI Elements Visible**: 
  - Two mode options: "Blockify" and "Chunk Only"
  - Description for each mode
- **Visual Cues**: Clear mode choices

**Step 2: Select Chunk Only Mode**
- **User Action**: Click "Chunk Only" option
- **System Response**: Basic chunking job creation interface loads
- **UI Elements Visible**: 
  - "Chunk Only Mode" header
  - Job configuration form
  - Simpler interface than blockify (no blockify model selection)
  - Dataset configuration section
  - File upload area
  - Chunk settings
- **Visual Cues**: "Chunk Only" mode indicated in header

**Step 3: Configure Target Dataset**
- **User Action**: Select existing dataset or "Create New Dataset"
- **System Response**: Form updates
- **UI Elements Visible**: 
  - Dataset dropdown
  - If new: Dataset name field appears
  - Embedding model selector
- **Visual Cues**: Fields appear based on selection

**Step 4: Upload Files**
- **User Action**: Upload document files via choose files or drag-drop
- **System Response**: 
  - Files upload
  - Text extraction occurs
  - Files appear in table with status
- **UI Elements Visible**: 
  - File table with extraction progress
  - Status updates per file
  - Character counts

**Step 5: Configure Chunk Settings**
- **User Action**: Adjust chunk size and overlap using sliders
- **System Response**: 
  - Slider values update
  - Chunk count estimates update
- **UI Elements Visible**: 
  - Chunk size slider (e.g., 500-5000 characters)
  - Allow overlap checkbox
  - Overlap size slider (if enabled)
  - Current values displayed
  - Chunk count preview (if available)
- **Visual Cues**: Slider positions show current settings

**Step 6: Optional - Preview Chunks**
- **User Action**: Click "Show Advanced Settings" to see chunk preview
- **System Response**: Preview expands showing how files will be chunked
- **UI Elements Visible**: 
  - File tabs
  - Chunk previews for selected file
  - Each chunk numbered and showing text content

**Step 7: Start Chunking Job**
- **User Action**: Review configuration, click "Start Chunking" or "Create Job"
- **System Response**: 
  - Job created
  - Files uploaded to job
  - Redirect to job details
  - Processing begins
- **UI Elements Visible**: 
  - Loading briefly
  - Job details dashboard loads
  - Processing starts

**Step 8: Monitor Processing**
- **User Action**: Watch job progress
- **System Response**: 
  - Four-stage process (same as blockify):
    1. Text extraction (if not already done)
    2. Chunking (mechanical splitting - very fast)
    3. Embedding generation
    4. Dataset creation
  - Progress bar advances
  - Metrics update
- **UI Elements Visible**: 
  - Progress timeline
  - Metrics cards
  - Status updates
- **Visual Cues**: Progress animations

**Final Step: Chunking Job Complete**
- **Success Indicator**: 
  - Job status: "Completed"
  - 100% progress
  - Dataset created
  - Can view and use dataset
- **System State Change**: 
  - Dataset available with basic chunks
  - Each chunk formatted as simple text blocks
  - Ready for search queries
- **Next Possible Actions**: 
  - Activate and use dataset
  - View dataset contents
  - Create more chunking jobs

---

## Alternative Paths & Strategies

### Strategy A: Quick Chunking for Testing
**When to use**: Testing dataset feature with simple data

**Steps**:
1. Select Chunk Only mode
2. Upload single small document
3. Use default chunk settings
4. Process immediately
5. Fast completion for testing

---

## Error States & Recovery

**Error states similar to Create Blockify Job but without blockify-specific errors**:

### Error 1: No Embedding Model
**Cause**: Embedding model not available  
**User Experience**: Error message
**Recovery Steps**: Upload embedding model first

### Error 2: File Extraction Fails
**Cause**: Incompatible or corrupted file  
**Recovery Steps**: Remove failed file, upload compatible version

---

## Pain Points & Friction

**Identified Issues**:

1. **Less Structured Than Blockify**
   - **Impact**: Results lack names, questions, and structure
   - **Frequency**: All chunking jobs
   - **Potential Improvement**: Explain trade-off clearly

2. **Same Interface Complexity as Blockify**
   - **Impact**: Expected simpler interface for simpler mode
   - **Potential Improvement**: Streamlined chunk-only workflow

---

## Design Considerations

**Following Contextual Design Principles**:

1. **Automation Opportunities**: Auto-suggest chunk size based on file type
2. **Simplification Opportunities**: Wizard for chunk-only mode
3. **User Trust**: Clear expectations about output format

---

## Related Flows

- [Create New Blockify Job](./create-blockify-job.md) - Alternative with AI structuring
- [Upload Files for Processing](./upload-files-to-job.md) - File upload details
- [Configure Basic Chunk Settings](./configure-basic-chunks.md) - Settings detail

---

## Technical References

**Knowledge Base Sections**:
- src/components/blockify-corpus/new-job-screen.js - Mode selection
- src/components/jobs/utils/basic-chunking.js - Chunking execution
- src/components/jobs/job-manager.js - Job processing

---

## Version History

| Date | Version | Author | Changes |
|------|---------|--------|---------|
| 2025-10-04 | 1.1 | [Iternal Technologies](https://iternal.ai/airgapai) | Initial comprehensive documentation |

---

## Notes

**Chunk Only vs. Blockify Comparison**:
- **Chunk Only**: Fast, mechanical splitting; simple text blocks
- **Blockify**: Slow, AI-powered; structured with names, questions, answers

**When to Use Chunk Only**:
- Speed is more important than structure
- Documents are already well-organized
- Don't have blockify model
- Testing dataset features
- Simple Q&A documents

**When to Use Blockify**:
- Need semantic structure
- Complex documents benefit from AI organization
- Quality more important than speed
- Want named, categorized information blocks

**Best Practices**:
- Use larger chunks for chunk-only (less overhead)
- Enable overlap for better context continuity
- Test chunk size with sample before processing large sets

**Common User Questions**:
- "Which should I choose?" - Blockify for quality, chunk-only for speed
- "Can I convert chunk-only to blockify later?" - No, must reprocess
- "Is chunk-only searchable?" - Yes, works with dataset queries
- "How much faster is it?" - 10-50x faster (no AI processing per chunk)

