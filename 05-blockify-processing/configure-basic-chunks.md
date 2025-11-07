# Configure Basic Chunk Settings

## Overview
**Flow ID**: `configure-basic-chunks`  
**Category**: Blockify Processing  
**Estimated Duration**: 1-3 minutes  
**User Role**: All Users  
**Complexity**: Simple  

**Purpose**: Adjust chunk size and overlap settings during job creation to control how documents are split into pieces. Settings affect search precision, processing speed, and result quality.

---

## Trigger

**What initiates this flow:**
- [x] User manually initiates

**Specific trigger**: User creating blockify or chunking job and needs to configure how documents will be divided.

---

## Prerequisites

**Before starting, users must have:**
- [x] Job creation screen open
- [x] Files uploaded to job
- [x] Understanding that chunk size affects search quality and processing

---

## User Intent Analysis

### Primary Intent
Set optimal chunk size and overlap to balance search precision, processing speed, and context preservation.

### Secondary Intents
- Optimize for document structure
- Balance speed vs. quality
- Ensure adequate context in each chunk

---

## Step-by-Step Flow

### Main Path

**Step 1: Locate Chunk Settings**
- **User Action**: On job creation screen, find chunk settings section (typically after file upload)
- **System Response**: Chunk configuration controls displayed
- **UI Elements Visible**: 
  - "Chunk Settings" section header
  - **Chunk Size slider**: Range varies by mode
    - Blockify mode: 500-3000 characters (based on model context)
    - Chunk-only mode: 500-5000 characters
  - Current value displayed (e.g., "1000 characters")
  - **Allow Overlap checkbox**
  - **Overlap Size slider** (appears if checkbox enabled)
  - Range: 0-500 characters
  - Preview text explaining settings
  - "Show Advanced Settings" link/button

**Step 2: Review Current Settings**
- **User Action**: Note default chunk size (typically 1000 characters)
- **System Response**: Default values shown
- **UI Elements Visible**: 
  - Slider at default position
  - Value: "1000"
  - Overlap unchecked by default, or checked with default 200

**Step 3: Adjust Chunk Size**
- **User Action**: Drag chunk size slider to desired value
- **System Response**: 
  - Slider moves
  - Value updates in real-time
  - May snap to increments (e.g., rounds to nearest 100)
  - Chunk count estimate may update
- **UI Elements Visible**: 
  - Slider at new position
  - Updated value displayed
  - Estimated chunk count: "~45 chunks" or similar

**Step 4: Enable/Disable Overlap**
- **User Action**: Click "Allow Overlap" checkbox to toggle
- **System Response**: 
  - Checkbox checks/unchecks
  - If checked: Overlap size slider appears
  - If unchecked: Overlap slider hidden
- **UI Elements Visible**: 
  - Checkbox state changes
  - Overlap controls appear/disappear conditionally

**Step 5: Adjust Overlap (if enabled)**
- **User Action**: Drag overlap size slider
- **System Response**: 
  - Value updates
  - Overlap amount set
- **UI Elements Visible**: 
  - Overlap slider at selected position
  - Value: e.g., "200 characters"
  - Explanation: "Each chunk will overlap with previous by X characters"

**Step 6: Review Settings Summary**
- **User Action**: Review final configuration
- **System Response**: Settings displayed
- **UI Elements Visible**: 
  - Chunk size: "1500 characters"
  - Overlap: "Enabled, 250 characters" or "Disabled"
  - Estimated chunks for uploaded files

**Final Step: Chunk Settings Configured**
- **Success Indicator**: 
  - Settings at desired values
  - Can proceed with job creation
  - Settings will be used for processing
- **System State Change**: 
  - Job configuration includes chunk parameters
  - Processing will use these settings
- **Next Possible Actions**: 
  - View advanced preview (see configure-advanced-chunks.md)
  - Start job processing
  - Upload more files
  - Adjust other job settings

---

## Alternative Paths & Strategies

### Strategy A: Use Default Settings
**When to use**: Unsure what values to use

**Steps**:
1. Keep default chunk size (1000)
2. Keep default overlap (200 if enabled, disabled if not)
3. Proceed without adjusting
4. Defaults work for most documents

### Strategy B: Maximize Chunk Size
**When to use**: Want fewer, larger chunks for speed

**Steps**:
1. Slide chunk size to maximum
2. Disable overlap
3. Results in fewer chunks
4. Faster processing, less granular search

### Strategy C: Minimize Chunk Size
**When to use**: Want very granular search precision

**Steps**:
1. Slide chunk size to smaller value (500-700)
2. Enable overlap with moderate value
3. Results in many small chunks
4. Slower processing, more precise search

---

## Error States & Recovery

### Error 1: Invalid Chunk Size
**Cause**: Slider set to value outside valid range  
**User Experience**: 
- Value rejected or constrained
- Slider snaps to nearest valid value

**Recovery Steps**:
1. Use value within slider range
2. System prevents invalid values

**QA Note**: Slider UI prevents invalid values. This error cannot occur through normal interaction.

### Error 2: Overlap Larger Than Chunk
**Cause**: Overlap size set greater than chunk size  
**User Experience**: 
- May show warning or validation error
- Or automatically constrains overlap

**Recovery Steps**:
1. Reduce overlap size
2. Or increase chunk size
3. Overlap must be smaller than chunk

**QA Note**: System should validate and constrain automatically.

---

## Pain Points & Friction

**Identified Issues**:

1. **No Guidance on Optimal Values**
   - **Impact**: Users unsure what chunk size to use
   - **Frequency**: Every new job, especially first-time users
   - **Potential Improvement**: 
     - Recommendations based on document type
     - Presets: "Small chunks (precise)", "Medium (balanced)", "Large (fast)"
     - Explain trade-offs clearly
     - Show examples of chunk sizes

2. **No Real-Time Preview in Basic Mode**
   - **Impact**: Can't see how settings affect chunking without advanced mode
   - **Frequency**: Users not discovering advanced preview
   - **Potential Improvement**: 
     - Show sample chunk in basic mode
     - Preview toggle more prominent
     - Inline preview without switching modes

3. **Technical Terms (Characters, Overlap)**
   - **Impact**: Non-technical users may not understand concepts
   - **Frequency**: First-time users
   - **Potential Improvement**: 
     - Simpler language: "small/medium/large" instead of character counts
     - Visual representations of overlap concept
     - Examples in everyday terms

4. **Chunk Size Limits Not Explained**
   - **Impact**: Users don't know why maximum values differ by mode
   - **Frequency**: Users switching between blockify and chunk-only
   - **Potential Improvement**: 
     - Tooltip explaining why limit exists
     - Show model context limit for blockify mode
     - Explain technical constraints

---

## Design Considerations

**Following Contextual Design Principles**:

1. **Automation Opportunities**: 
   - Auto-suggest chunk size based on document analysis
   - Auto-calculate optimal overlap
   - Auto-adjust based on file types (PDFs vs. TXT)

2. **Simplification Opportunities**: 
   - Three presets instead of sliders: Small/Medium/Large
   - Hide overlap as advanced option
   - Smart defaults that work for 80% of cases

3. **Transition Smoothness**: 
   - Slider adjustments instant
   - Smooth value updates
   - No page reloads needed

4. **User Trust**: 
   - Preview available (advanced mode) to verify settings
   - Estimates show impact of changes
   - Can adjust after seeing preview

5. **Cognitive Load**: 
   - Don't require understanding of optimal values
   - Visual sliders easier than number input
   - Defaults work without adjustment
   - Help text explains each setting

---

## Related Flows

- [Configure Advanced Chunk Settings with Preview](./configure-advanced-chunks.md) - Detailed preview mode
- [Create New Blockify Job](./create-blockify-job.md) - Parent workflow
- [Create Basic Chunking Job](./create-chunking-job.md) - Alternative job type
- [Upload Files for Processing](./upload-files-to-job.md) - Preceding step

---

## Technical References

**Knowledge Base Sections**:
- src/components/blockify-corpus/new-job-screen.js - Chunk settings UI
- src/constants/blockify.js - Chunk size limits and defaults
- src/components/blockify-corpus/advanced-chunk-settings.js - Advanced preview

**Key Components**:
- Chunk size and overlap sliders
- Real-time value display
- Mode-specific limits
- Advanced preview system

---

## Version History

| Date | Version | Author | Changes |
|------|---------|--------|---------|
| 2025-10-04 | 1.1 | [Iternal Technologies](https://iternal.ai/airgapai) | Initial comprehensive documentation |

---

## Notes

**Chunk Size Guidelines**:
- **Small (500-700 characters)**: Very precise search, many chunks, slower processing
- **Medium (1000-1500 characters)**: Balanced, recommended for most documents
- **Large (2000-3000+ characters)**: Faster processing, less granular, good for well-structured docs

**Overlap Explained**:
When enabled, each chunk includes some text from the previous chunk. This preserves context across chunk boundaries and prevents information from being split awkwardly.

**Example**: With 1000-character chunks and 200-character overlap:
- Chunk 1: Characters 1-1000
- Chunk 2: Characters 801-1800 (overlaps 200 with Chunk 1)
- Chunk 3: Characters 1601-2600 (overlaps 200 with Chunk 2)

**Mode Differences**:
- **Blockify mode**: Chunk size limited by blockify model's context window (typically max 3000)
- **Chunk-only mode**: Higher limits possible (up to 5000) since no model processing

**Best Practices**:
- Start with defaults (1000 chunk, 200 overlap if enabled)
- Use advanced preview to verify chunking looks good
- Larger chunks for narrative documents (books, articles)
- Smaller chunks for reference material (documentation, FAQs)
- Enable overlap to preserve context across boundaries
- Disable overlap for faster processing if context breaks acceptable

**Common User Questions**:
- "What chunk size should I use?" - 1000-1500 is good starting point for most documents
- "Should I enable overlap?" - Yes, recommended for better context (200-250 characters)
- "Does larger chunk size mean faster?" - Yes, fewer chunks = faster processing
- "Will small chunks give better search?" - More precise but may fragment context
- "Can I change settings after job starts?" - No, must create new job with different settings

