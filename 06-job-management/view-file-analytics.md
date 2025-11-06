# View Individual File Analytics

## Overview
**Flow ID**: `view-file-analytics`  
**Category**: Job Management  
**Estimated Duration**: 2-5 minutes  
**User Role**: All Users  
**Complexity**: Moderate  

**Purpose**: Drill down into specific file within job to see detailed analytics, charts, and processing statistics unique to that file. Useful for comparing file processing performance or troubleshooting specific file issues.

---

## Trigger

**What initiates this flow:**
- [x] User manually initiates

**Specific trigger**: User wants file-specific details rather than job-wide aggregates.

---

## User Intent Analysis

### Primary Intent
Analyze individual file's processing performance and results separately from other files in job.

### Secondary Intents
- Compare files within job
- Identify problematic files
- Understand processing variations
- Optimize future file preparations

---

## Step-by-Step Flow

### Main Path (Happy Path)

**Step 1: Open Job Details**
- **User Action**: Navigate to job details dashboard
- **System Response**: Job dashboard displays with aggregate view

**Step 2: Locate File Selector**
- **User Action**: Find file chooser dropdown (typically in analytics section)
- **System Response**: Selector visible
- **UI Elements Visible**: 
  - File selector dropdown
  - Currently shows: "All Files" (default)
  - Dropdown arrow indicating can select

**Step 3: Open File Dropdown**
- **User Action**: Click file selector dropdown
- **System Response**: List of files in job appears
- **UI Elements Visible**: 
  - "All Files" option at top
  - Individual file entries below:
    - Filename
    - File size
    - Status icon (checkmark if complete)
    - Text length indicator

**Step 4: Select Specific File**
- **User Action**: Click on specific file name
- **System Response**: 
  - View updates to show file-specific data
  - Charts recalculate for this file only
  - Metrics update
  - Available charts may change
- **UI Elements Visible**: 
  - Selected filename in dropdown
  - Progress arc shows file-specific progress
  - Charts switch to per-file data
  - Metrics specific to file

**Step 5: Review File-Specific Progress**
- **User Action**: Examine progress arc for this file
- **System Response**: Arc shows file's processing stages
- **UI Elements Visible**: 
  - Four-layer arc:
    - Text Extraction: 100% (complete)
    - Blockification: X% complete
    - Embeddings: Y% complete
    - Overall: Z% complete
  - Hover shows tooltips with exact counts

**Step 6: View File-Specific Charts**
- **User Action**: Browse through chart types
- **System Response**: Charts show file-specific data
- **UI Elements Visible**: 
  - Chart selector showing per-file chart options:
    - Progress (arc chart)
    - Tokens Per Second (line chart of processing speed per chunk)
    - E2E Latency (processing time per chunk)
    - Throughput (rate over time)
    - Unique Items Per Chunk (how many items each chunk generated)
  - Active chart displays file-specific data

**Step 7: Analyze Patterns**
- **User Action**: Interpret charts to understand file behavior
- **System Response**: Data visualized
- **Observations Possible**:
  - Which chunks processed faster/slower
  - Consistency of processing speed
  - Items distribution across chunks
  - Performance trends

**Step 8: Switch to Different File**
- **User Action**: Select another file from dropdown to compare
- **System Response**: 
  - View switches to new file
  - Charts update with that file's data
  - Can compare mentally or by switching back and forth

**Final Step: File Analytics Reviewed**
- **Success Indicator**: 
  - Understood individual file performance
  - Compared files if desired
  - Identified any file-specific issues
- **System State Change**: User has granular understanding of job
- **Next Possible Actions**: 
  - View different files
  - Return to "All Files" view for aggregate
  - View IdeaBlocks for specific file
  - Download file-specific report

---

## Alternative Paths & Strategies

### Strategy A: Compare Two Specific Files
**When to use**: Want to understand why files performed differently

**Steps**:
1. Select first file
2. Note key metrics (processing rate, latency)
3. Select second file
4. Compare metrics
5. Identify differences

### Strategy B: Find Slowest File
**When to use**: Troubleshooting slow job

**Steps**:
1. Switch through each file
2. Note processing rates
3. Identify slowest
4. Examine why (size, complexity, content type)

---

## Error States & Recovery

### Error 1: File Data Not Available
**Cause**: File hasn't been processed yet or data missing  
**User Experience**: 
- Charts show empty or no data
- Message: "No data available for this file"

**Recovery Steps**:
1. Check file status (may not be processed yet)
2. Wait if job still running
3. Return to "All Files" view

**QA Note**: Expected for unprocessed files. Not error if job still running.

---

## Pain Points & Friction

**Identified Issues**:

1. **Cannot Compare Side-by-Side**
   - **Impact**: Must switch between files to compare
   - **Potential Improvement**: Split-screen comparison view

2. **No File Ranking or Sorting**
   - **Impact**: Must manually check all to find fastest/slowest
   - **Potential Improvement**: 
     - Sort files by processing time
     - Highlight outliers

---

## Design Considerations

**Following Contextual Design Principles**:

1. **Simplification Opportunities**: Show most important files first
2. **User Trust**: Accurate per-file data
3. **Cognitive Load**: Clear file-specific vs. aggregate distinction

---

## Related Flows

- [View Job Details Dashboard](./view-job-details.md) - Parent dashboard
- [View Job Performance Charts](./view-job-charts.md) - Chart exploration

---

## Technical References

**Knowledge Base Sections**:
- src/components/jobs/blockify-job-processing-screen/index.js - File selection logic
- src/components/jobs/blockify-job-processing-screen/ui/file-chooser.js - File selector

---

## Version History

| Date | Version | Author | Changes |
|------|---------|--------|---------|
| 2025-10-04 | 1.1 | [Iternal Technologies](https://iternal.ai/airgapai) | Initial documentation |

---

## Notes

**Per-File Charts Available**:
- Progress Arc: Multi-layer progress visualization
- Tokens Per Second: Processing speed across chunks
- E2E Latency: Time per chunk
- Throughput: Processing rate over time
- Items Per Chunk: Distribution of created items

**Best Practices**:
- Use file-specific view for troubleshooting
- Compare files to understand performance patterns
- Identify problematic files for special handling in future

**Common User Questions**:
- "Why are some files faster?" - Varies by size, complexity, content structure
- "Can I process files separately?" - No, all files in job processed together
- "Which charts are most useful?" - Depends on goal; Progress for overview, Latency for troubleshooting

