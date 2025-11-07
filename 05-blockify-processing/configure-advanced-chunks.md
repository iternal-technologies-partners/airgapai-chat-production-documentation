# Configure Advanced Chunk Settings with Preview

## Overview
**Flow ID**: `configure-advanced-chunks`  
**Category**: Blockify Processing  
**Estimated Duration**: 3-10 minutes  
**User Role**: All Users  
**Complexity**: Moderate  

**Purpose**: Access detailed chunk preview showing exactly how each uploaded file will be split based on current settings. Allows fine-tuning chunk size and overlap while seeing real-time preview of results for each file.

---

## Trigger

**What initiates this flow:**
- [x] User manually initiates

**Specific trigger**: User wants to see precisely how files will be chunked before processing, typically because:
- Want to verify chunk boundaries make sense
- Optimizing settings for specific document structure
- Files have special formatting requiring customization
- Want confidence settings are correct before long processing

---

## Prerequisites

**Before starting, users must have:**
- [x] Job creation screen open with files uploaded
- [x] Text extracted from uploaded files
- [x] Basic chunk settings configured (or using defaults)

---

## User Intent Analysis

### Primary Intent
Preview exact chunking results for each file to verify settings produce good chunk boundaries and appropriate chunk sizes.

### Secondary Intents
- Optimize chunk settings with visual feedback
- Understand how different files will be processed
- Identify potential chunking issues before processing
- Fine-tune for specific document structures

### Subintents
- See chunk boundaries for each file
- Count chunks per file
- Verify no information split awkwardly
- Ensure chunk sizes consistent

---

## Step-by-Step Flow

### Main Path

**Step 1: Access Advanced Preview**
- **User Action**: On job creation screen, click "Show Advanced Settings" or "Preview Chunks" button
- **System Response**: Interface expands to show advanced chunk preview
- **UI Elements Visible**: 
  - Expanded advanced settings panel
  - Left side: Enhanced chunk settings sliders
  - Right side: File preview area with tabs
  - File tabs showing each uploaded file
  - Current file's chunks displayed
- **Visual Cues**: 
  - Smooth expansion animation
  - Panel takes over significant screen space
  - Clear division between settings and preview

**Step 2: Review Interface Layout**
- **User Action**: Observe advanced interface structure
- **System Response**: Full advanced interface visible
- **UI Elements Visible**: 
  - **Left Panel - Settings**:
    - Chunk size slider
    - Allow overlap checkbox
    - Overlap size slider
    - Current values displayed
    - Real-time update indicators
  - **Right Panel - Preview**:
    - File tabs at top (one per uploaded file)
    - Active file tab highlighted
    - Chunk preview area below tabs
    - Individual chunks displayed as cards
- **Visual Cues**: 
  - Two-panel layout
  - File tabs horizontally scrollable if many files
  - Clean, organized structure

**Step 3: Select File to Preview**
- **User Action**: Click on a file tab to see its chunk preview
- **System Response**: 
  - Selected tab highlights
  - Preview area updates to show that file's chunks
  - Chunk count for file displayed in tab
- **UI Elements Visible**: 
  - Active file tab with highlight/underline
  - File name in tab
  - Chunk count: "(15 chunks)"
  - Chunk cards for selected file below

**Step 4: Review Chunk Preview**
- **User Action**: Scroll through chunks to see how file is divided
- **System Response**: All chunks for file displayed
- **UI Elements Visible**: 
  - Series of chunk cards, each showing:
    - **Header**: "Chunk #1 (892 characters)"
    - **Content**: Actual text that will be in this chunk
    - Character count per chunk
  - Chunks numbered sequentially: #1, #2, #3, etc.
  - If overlap enabled: Visual indication of overlapping text (may be highlighted)
  - Scrollable area if many chunks

**Step 5: Assess Chunk Quality**
- **User Action**: Check if chunk boundaries make sense
  - Are chunks breaking at natural points?
  - Is important information kept together?
  - Are chunk sizes reasonable?
- **System Response**: Static display of chunks
- **UI Elements Visible**: Full chunk text visible for assessment

**Step 6: Adjust Settings While Viewing Preview**
- **User Action**: Move chunk size or overlap sliders to optimize
- **System Response**: 
  - Preview updates immediately (or after brief delay)
  - Chunk cards regenerate with new settings
  - Chunk count updates
  - All file tabs update with new counts
- **UI Elements Visible**: 
  - Updated chunk previews
  - New chunk counts per file
  - Real-time recalculation
  - May see brief "Recalculating..." indicator
- **Visual Cues**: 
  - Smooth preview updates
  - Numbers change dynamically

**Step 7: Preview Multiple Files**
- **User Action**: Click through different file tabs to verify chunking for each file
- **System Response**: Each file shows its specific chunk breakdown
- **UI Elements Visible**: 
  - Different chunk counts per file (files vary in size)
  - Chunk previews specific to each file's content
  - Can compare chunking across files

**Step 8: Finalize Settings**
- **User Action**: Once satisfied with preview, close advanced settings or proceed with job
- **System Response**: Settings confirmed
- **UI Elements Visible**: 
  - May have "Apply" or "Done" button
  - Or simply proceed to job creation
- **Visual Cues**: Settings locked in

**Final Step: Advanced Settings Configured**
- **Success Indicator**: 
  - Verified chunking looks good for all files
  - Settings optimized based on preview
  - Confident in configuration
- **System State Change**: 
  - Chunk settings finalized
  - Ready for job processing with verified configuration
- **Next Possible Actions**: 
  - Start job processing
  - Return to basic settings view
  - Upload additional files
  - Make final setting adjustments

---

## Alternative Paths & Strategies

### Strategy A: Test Different Settings for Each File
**When to use**: Files have different optimal chunk sizes

**Steps**:
1. Select first file tab
2. Adjust settings to optimize for this file
3. Note settings that work well
4. Select next file tab
5. Observe how same settings work for different file
6. Find compromise settings that work for all files

**QA Note**: Cannot set per-file chunk sizes; must find settings working for all files.

### Strategy B: Focus on Problematic File**
**When to use**: One file chunks poorly with current settings

**Steps**:
1. Review all file previews
2. Identify file with bad chunking
3. Adjust settings to fix that file specifically
4. Verify other files still acceptable
5. Balance competing needs

### Strategy C: Quick Check and Proceed**
**When to use**: Trust defaults, just want quick verification

**Steps**:
1. Open advanced preview
2. Glance at first file's chunks
3. If looks reasonable, proceed without detailed review
4. Close preview and start job
5. Saves time if comfortable with defaults

---

## Error States & Recovery

### Error 1: Preview Doesn't Update
**Cause**: Caching issue or calculation error  
**User Experience**: 
- Adjust sliders but preview stays same
- Chunk counts don't update

**Recovery Steps**:
1. Click different file tab and back
2. Close and reopen advanced settings
3. Refresh page
4. Preview should recalculate

**QA Note**: Real-time updates should work. If fails, indicates calculation or caching bug.

### Error 2: Preview Calculation Times Out
**Cause**: Very large files or many chunks  
**User Experience**: 
- "Calculating..." indicator continues long time
- Preview never appears
- May show error or empty preview

**Recovery Steps**:
1. Increase chunk size to reduce chunk count
2. Wait longer (may just be slow)
3. Try previewing smaller file first
4. If specific file consistently fails, may need to split file

### Error 3: Out of Memory During Preview
**Cause**: Too many chunks or large files overwhelming browser  
**User Experience**: 
- Browser becomes slow or unresponsive
- Preview laggy or frozen
- May see memory warnings

**Recovery Steps**:
1. Increase chunk size to reduce total chunks
2. Close other browser tabs
3. Refresh page
4. Preview fewer files at once
5. Use basic settings without preview for very large sets

---

## Pain Points & Friction

**Identified Issues**:

1. **Preview Can Be Slow for Large Files**
   - **Impact**: Updates laggy when adjusting settings for files with hundreds of chunks
   - **Frequency**: Large documents or small chunk sizes
   - **Potential Improvement**: 
     - Virtualized rendering (only show first N chunks)
     - "Calculating..." indicator more prominent
     - Preview subset of chunks instead of all
     - Optimize preview generation performance

2. **Cannot Set Different Chunks Per File**
   - **Impact**: Must compromise on settings that work for all files
   - **Frequency**: Mixed document types in single job
   - **Potential Improvement**: 
     - Per-file chunk configuration
     - Detect optimal settings per file automatically
     - Allow file-specific overrides

3. **Overlap Visualization Not Clear**
   - **Impact**: Difficult to see where text overlaps between chunks
   - **Frequency**: When using overlap feature
   - **Potential Improvement**: 
     - Highlight overlapping text in preview
     - Show overlap indicators between chunks
     - Color-code or bracket overlapping regions

4. **No Indication of "Good" vs "Bad" Chunking**
   - **Impact**: Users uncertain if chunk boundaries are acceptable
   - **Frequency**: First-time users, unfamiliar document types
   - **Potential Improvement**: 
     - Automated quality assessment
     - Warnings for problematic chunks (too small, splits mid-sentence)
     - Recommendations: "Chunk 5 breaks mid-paragraph; consider larger chunks"

5. **Advanced Mode Not Discoverable**
   - **Impact**: Users may never find preview feature
   - **Frequency**: Users who don't explore thoroughly
   - **Potential Improvement**: 
     - Make "Show Advanced Settings" more prominent
     - Tutorial or tooltip highlighting feature
     - Auto-suggest preview for first job

6. **Cannot Save Settings for Future Jobs**
   - **Impact**: Must reconfigure for each new job
   - **Frequency**: Users with consistent document types
   - **Potential Improvement**: 
     - Save settings as preset
     - Remember last-used settings
     - Named configurations for different document types

---

## Design Considerations

**Following Contextual Design Principles**:

1. **Automation Opportunities**: 
   - Auto-detect optimal chunk size per file
   - Auto-highlight problem areas in preview
   - Auto-suggest adjustments for improvement
   - Cache preview calculations for performance

2. **Simplification Opportunities**: 
   - Show preview for current settings only (not all possible settings)
   - Limit preview to first 10-20 chunks if file has hundreds
   - Provide "Trust defaults" option to skip preview
   - Progressive disclosure: basic preview first, detailed on demand

3. **Transition Smoothness**: 
   - Smooth expansion to advanced mode
   - Real-time preview updates without jarring reloads
   - Easy toggle between basic and advanced
   - Natural flow from preview to job execution

4. **User Trust**: 
   - Seeing actual chunks builds confidence
   - Real-time updates show settings actually work
   - Can verify before committing to processing
   - Preview accurately represents final results

5. **Cognitive Load**: 
   - Visual preview reduces need to imagine results
   - Can see impact of changes immediately
   - Don't need to understand algorithms
   - Learn through experimentation with instant feedback

---

## Related Flows

- [Configure Basic Chunk Settings](./configure-basic-chunks.md) - Simpler settings interface
- [Upload Files for Processing](./upload-files-to-job.md) - Files needed for preview
- [Create New Blockify Job](./create-blockify-job.md) - Full job creation workflow
- [Create Basic Chunking Job](./create-chunking-job.md) - Alternative processing mode

---

## Technical References

**Knowledge Base Sections**:
- src/components/blockify-corpus/advanced-chunk-settings.js - Advanced preview component
- src/components/blockify-corpus/layout-components.js - Preview UI elements
- Chunk calculation utilities
- Caching system for preview performance

**Key Components**:
- Two-panel advanced interface
- File tab navigation
- Real-time chunk preview
- Chunk calculation with caching
- Responsive preview updates

---

## Version History

| Date | Version | Author | Changes |
|------|---------|--------|---------|
| 2025-10-04 | 1.1 | [Iternal Technologies](https://iternal.ai/airgapai) | Initial comprehensive documentation |

---

## Notes

**Important Considerations**:
- Preview shows exact chunks that will be created
- Settings changes update preview in real-time (brief delay for calculations)
- Preview caches chunks per setting combination for performance
- Can preview all uploaded files individually
- Large files (100+ pages) may have hundreds of chunks; preview may be slow
- Preview is optional; can proceed with basic settings if confident

**Advanced Preview Benefits**:
- See exact chunk boundaries before committing to processing
- Identify documents that chunk poorly
- Optimize settings with visual feedback
- Build confidence in configuration
- Learn how chunk size affects different document types

**When to Use Advanced Preview**:
- First time using blockify with new document types
- Documents have special structure (tables, lists, formatted sections)
- Want to optimize for best search results
- Processing many documents (worth time to get settings right)
- Experimenting with chunk parameters

**When to Skip Advanced Preview**:
- Using proven settings from previous jobs
- Documents are simple, plain text
- Time-constrained
- Comfortable with defaults

**Best Practices for Using Preview**:
- Review at least 2-3 files to see variation
- Look for chunks that break mid-sentence or mid-paragraph
- Adjust chunk size if chunks too small (< 300 characters) or too large (> 2500 characters consistently)
- Enable overlap if seeing important context split across chunks
- Aim for chunks that feel like complete "thoughts" or "topics"
- Don't over-optimize; good enough is better than perfect

**Common User Questions**:
- "Do I need to preview?" - No, optional; but recommended for first jobs or important documents
- "Will final results match preview exactly?" - Yes, preview shows actual chunking algorithm
- "Why does preview take time to update?" - Recalculating chunks for every setting change requires processing
- "Can I preview without uploading files?" - No, need actual file content to show chunks
- "What if preview shows bad chunking?" - Adjust settings until chunks look better

