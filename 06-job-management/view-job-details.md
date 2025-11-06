# View Job Details Dashboard

## Overview
**Flow ID**: `view-job-details`  
**Category**: Job Management  
**Estimated Duration**: 2-10 minutes  
**User Role**: All Users  
**Complexity**: Moderate  

**Purpose**: This flow enables users to access a comprehensive dashboard showing detailed information about a specific processing job, including real-time progress, performance analytics, file-by-file breakdowns, charts, and structured results. This dashboard serves as the central monitoring and analysis interface for document processing jobs.

---

## Trigger

**What initiates this flow:**
- [x] User manually initiates


**Specific trigger**: User wants detailed information about a job, typically because:
- They need to monitor an active job's progress
- They want to analyze completed job results
- They need to troubleshoot a failed or stalled job
- They're verifying processing quality
- They want to view performance metrics or created items

---

## Prerequisites

**Before starting, users must have:**
- [x] Application installed and running
- [x] At least one job created (active, completed, or failed)
- [x] Job ID or access through navigation

---

## User Intent Analysis

### Primary Intent
View comprehensive details about a processing job to understand its status, monitor progress, analyze results, or troubleshoot issues.

### Secondary Intents
- Verify job is progressing normally
- Identify performance bottlenecks
- Review structured output (IdeaBlocks)
- Compare file processing speeds
- Export results or reports
- Make decisions about similar future jobs

### Subintents
- Understand which processing stage job is in
- See file-by-file breakdown
- Access detailed analytics and charts
- Download results or reports

---

## Step-by-Step Flow

### Main Path (Happy Path)

**Step 1: Access Job from Multiple Entry Points**
- **User Action**: Navigate to job details via one of several methods:
  - Click job status badge in bottom-right corner, then click specific job
  - Navigate to Blockify > View Jobs, then click job in table
  - Click breadcrumb or link from dataset viewer if job created that dataset
- **System Response**: Job details page begins loading
- **UI Elements Visible**: 
  - Loading indicator while page initializes
  - Page transition animation
- **Visual Cues**: Page loading state

**Step 2: Job Details Page Loads**
- **User Action**: Wait briefly for page to load (typically instant to 2 seconds)
- **System Response**: Comprehensive job dashboard displays
- **UI Elements Visible**: 
  - **Page Header Section**:
    - Breadcrumb navigation (Home > Blockify > Job Details)
    - Job name/title (large, prominent)
    - Status badge (Processing, Completed, Failed, etc. - color coded)
    - Dataset info card (showing target dataset)
    - Edit notes button (pencil icon)
    - Developer notes subtitle (if any notes exist)
  
  - **Progress Timeline Section**:
    - Horizontal progress bar with four layers/stages
    - Overall completion percentage (large, centered above bar)
    - Estimated time remaining (if job active)
    - Elapsed time
    - Stage breakdown: Text Extraction, Blockification, Embeddings, Dataset Creation
    - Each stage shows completion status
    - Animated striped pattern if processing
    - Action buttons: Retry or Cancel (depending on status)
  
  - **Metrics Cards Section** (4 cards in grid):
    - Files Processed (X of Y complete, percentage)
    - Blockification Progress (chunks processed, average time)
    - IdeaBlocks Created (total count, embedded count)
    - Processing Time (elapsed, rate per minute)
  
  - **Analytics Section**:
    - File selector dropdown (All Files vs. individual files)
    - Chart/IdeaBlocks tabs
    - Chart type selector (Progress, Tokens/Second, Latency, Throughput, Items per Chunk)
    - Large chart display area
    - Download report button

- **Visual Cues**: 
  - Color-coded status badges (green=completed, blue=processing, red=failed)
  - Animated progress indicators for active jobs
  - Real-time updating numbers
  - Professional dashboard layout

**Step 3: Review Overall Progress**
- **User Action**: Look at progress timeline and percentage
- **System Response**: Current state displayed
- **UI Elements Visible**: 
  - Large percentage (e.g., "67% Complete")
  - Progress bar with four colored layers:
    - Gray: Text Extraction
    - Green: Blockification (AI processing)
    - Teal: Embeddings
    - Blue: Overall progress
  - Each layer shows its own completion percentage
  - Striped animation on in-progress layers
  - Hover over layers shows tooltip with details
- **Visual Cues**: 
  - Bar fills from left to right
  - Different colors for each stage
  - Animation indicates active processing

**Step 4: Examine Metrics Cards**
- **User Action**: Review the four metrics cards for quick statistics
- **System Response**: Cards display real-time data
- **UI Elements Visible**: 
  - **Files Processed Card**: "15 / 20 completed, 75%" with file icon
  - **Blockification Progress Card**: "750 / 1000 chunks, 12.5 pages/min" (if applicable)
  - **IdeaBlocks Card**: "2,450 items created, 1,200 embedded" with database icon
  - **Processing Time Card**: Live timer showing elapsed time, processing rate
  - Each card shows icon, title, main value, change/rate, subtitle
- **Visual Cues**: 
  - Grid layout (2x2 or 4 across)
  - Icons distinguish each metric
  - Large numbers for primary values
  - Color-coded change indicators (green positive, red negative)
  - Live updates (numbers change in real-time for active jobs)

**Step 5: Select File for Detailed Analysis (Optional)**
- **User Action**: Click the file selector dropdown to view individual file stats
- **System Response**: Dropdown expands showing file options
- **UI Elements Visible**: 
  - "All Files" option (current default)
  - List of individual files uploaded to this job
  - Each file shows name and status icon
- **Visual Cues**: 
  - Dropdown clearly shows current selection
  - File list with icons

**Step 6: Choose Individual File**
- **User Action**: Select a specific file from dropdown
- **System Response**: 
  - View updates to show file-specific data
  - Charts and metrics recalculate for selected file
  - Available chart types may change
- **UI Elements Visible**: 
  - Selected filename shown in dropdown
  - Progress arc now shows file-specific percentages
  - Charts display file-specific data
  - Metrics specific to selected file
- **Visual Cues**: 
  - Smooth transition to file view
  - Chart data updates

**Step 7: Explore Different Chart Types**
- **User Action**: Click different chart type buttons to view various analytics
- **System Response**: Chart updates to show selected visualization
- **UI Elements Visible**: 
  - Chart selector buttons: Progress, Tokens Per Second, Latency, Throughput, Items Per Chunk
  - Active chart button highlighted
  - Large chart display area showing:
    - **Progress Chart**: Arc/circular chart with four layers
    - **Tokens Per Second**: Line chart showing processing speed over time
    - **E2E Latency**: Chart showing processing time per chunk
    - **Throughput**: Bar or line chart of processing rate
    - **Items Per Chunk**: Chart showing how many items created per chunk
  - Chart title and legend
  - Axes labels and values
- **Visual Cues**: 
  - Active chart button has blue background
  - Charts animate when first displayed
  - Hover on chart elements shows tooltips with exact values

**Step 8: Optional - Switch to IdeaBlocks Tab**
- **User Action**: Click "IdeaBlocks" tab next to "Charts" tab
- **System Response**: View switches from charts to list of created items
- **UI Elements Visible**: 
  - List of all IdeaBlocks created by this job (or for selected file)
  - Each IdeaBlock shows:
    - Block Name
    - Critical Question
    - Trusted Answer
    - Source filename
  - Scrollable list
  - Item count header
  - Search/filter options (if available)
- **Visual Cues**: 
  - IdeaBlocks tab highlighted
  - List view with clear item separation
  - Green-bordered blocks

**Step 9: Scroll Through Results**
- **User Action**: Scroll through IdeaBlocks list or chart details
- **System Response**: Content scrolls smoothly
- **UI Elements Visible**: 
  - Scrollable content area
  - Scrollbar indicating position
  - Items load as scrolled (if large dataset)
- **Visual Cues**: Smooth scrolling, content organized clearly

**Step 10: Optional - Download Report**
- **User Action**: Click "Download Report" or "Export" button
- **System Response**: Report file generates and downloads
- **UI Elements Visible**: 
  - Download button
  - Browser download notification
  - File save dialog
- **Visual Cues**: Download progress
- **Note**: Report may include all metrics, charts data, and results

**Step 11: Optional - Edit Developer Notes**
- **User Action**: Click "Edit Notes" button in header
- **System Response**: Notes modal appears
- **UI Elements Visible**: 
  - Modal with text area for notes
  - Current notes shown (if any exist)
  - Save and Cancel buttons
- **Visual Cues**: Modal overlay
- **Use Case**: Add notes about job configuration or results for future reference

**Step 12: Return to Jobs List or Other Page**
- **User Action**: Click breadcrumb link or navigation menu to go elsewhere
- **System Response**: Navigate to selected page
- **UI Elements Visible**: New page content
- **Visual Cues**: Page transition
- **Note**: Job continues processing if active; can return anytime

**Final Step: Comprehensive Job Understanding**
- **Success Indicator**: 
  - Viewed job status and progress
  - Understood current processing stage
  - Reviewed metrics and analytics
  - Accessed detailed results (if desired)
  - Downloaded report (if needed)
- **System State Change**: 
  - User has full information about job
  - Any notes added are saved
  - Job continues processing (if active)
  - User can make informed decisions about job
- **Next Possible Actions**: 
  - Wait for job to complete if processing
  - Cancel job if needed
  - Retry job if failed
  - View created dataset
  - Create similar jobs with learned insights
  - Export or share results
  - Add notes about findings

---

## Alternative Paths & Strategies

### Strategy A: Quick Status Check
**When to use**: Just need to verify job is running properly

**Steps**:
1. Click job from status badge or jobs list
2. Glance at overall progress percentage
3. Check status badge for errors
4. Return to previous page
5. Total time: 10 seconds

### Strategy B: Deep Analysis of Results
**When to use**: Job complete, need to analyze quality and performance

**Steps**:
1. Open job details for completed job
2. Review all four metrics cards
3. Switch between all chart types
4. Select each file individually to compare performance
5. Switch to IdeaBlocks tab
6. Scroll through all created items to verify quality
7. Download report for documentation
8. Total time: 10-20 minutes

### Strategy C: Troubleshooting Stalled Job
**When to use**: Job seems stuck or progressing slowly

**Steps**:
1. Open job details
2. Check progress percentage - is it increasing?
3. Note current stage and completion
4. Look at processing rate (chunks/minute)
5. Check if engine status shows active processing
6. Review individual file statuses for failures
7. Examine charts for anomalies
8. Decide whether to wait, cancel, or retry

### Strategy D: File-by-File Comparison
**When to use**: Want to understand processing differences between files

**Steps**:
1. Open job details
2. Select first file from dropdown
3. Note metrics and chart patterns
4. Select second file
5. Compare metrics
6. Identify which files process faster/slower
7. Use insights for future jobs

---

## Error States & Recovery

### Error 1: Job Not Found
**Cause**: Invalid job ID or job was deleted  
**User Experience**: 
- Error message: "Job not found" or 404 error
- Empty or error page
- Cannot access job details

**Recovery Steps**:
1. Verify you have correct job ID
2. Check if job appears in jobs list
3. Job may have been deleted
4. Return to jobs list to find correct job

### Error 2: Charts Not Loading
**Cause**: No processing data available yet or chart render error  
**User Experience**: 
- Chart area shows loading spinner continuously
- Empty chart with no data
- Error message in chart area

**Recovery Steps**:
1. If job just started, wait for data to accumulate
2. Refresh page to reload chart data
3. Try switching chart types
4. Check if job has actually processed any chunks

**QA Note**: Charts require processing data. Early in job, charts may be empty by design.

### Error 3: Real-Time Updates Not Working
**Cause**: Update mechanism paused or connection issue  
**User Experience**: 
- Progress percentage doesn't increase
- Metrics don't update
- Page appears frozen at one state

**Recovery Steps**:
1. Refresh page manually
2. Check if job is actually running (status badge)
3. Verify application hasn't crashed
4. Navigate away and back to job details
5. Data should update after refresh

### Error 4: Cannot Download Report
**Cause**: Report generation fails or download blocked  
**User Experience**: 
- Download button doesn't work
- Error message about report generation
- No file downloads

**Recovery Steps**:
1. Try download again
2. Check browser isn't blocking downloads
3. Verify job has data to report
4. Try from jobs list page instead
5. If persists, manually export data from view

---

## Pain Points & Friction

**Identified Issues**:

1. **Information Overload**
   - **Impact**: Too much data presented at once can be overwhelming
   - **Frequency**: First-time viewers, complex jobs
   - **Potential Improvement**: 
     - Progressive disclosure (show summary first, details on request)
     - Guided tour for first view
     - Collapsible sections
     - Focus modes for different use cases

2. **No Explanation of Metrics**
   - **Impact**: Users may not understand what metrics mean or why they matter
   - **Frequency**: Users new to blockify process
   - **Potential Improvement**: 
     - Tooltips explaining each metric
     - Help icons with detailed descriptions
     - Contextual guidance about what's good/bad
     - Comparison to typical values

3. **Charts Require Technical Understanding**
   - **Impact**: Non-technical users may not interpret charts correctly
   - **Frequency**: Users without data analysis experience
   - **Potential Improvement**: 
     - Plain language chart descriptions
     - Insights/interpretations shown with charts
     - Summary bullets instead of just visual data
     - "What this means" explanations

4. **No Quick Access to Common Actions**
   - **Impact**: Must navigate to find retry, cancel, or export options
   - **Frequency**: Users needing to take action based on status
   - **Potential Improvement**: 
     - Prominent action buttons in header
     - Context-aware action recommendations
     - Quick action toolbar

5. **Unclear What's Real-Time vs. Static**
   - **Impact**: Users unsure if they're seeing live data or need to refresh
   - **Frequency**: When monitoring active jobs
   - **Potential Improvement**: 
     - Clear indicators of real-time elements
     - Last updated timestamps
     - Live indicator icons
     - Refresh button if not auto-updating

---

## Design Considerations

**Following Contextual Design Principles**:

1. **Automation Opportunities**: 
   - Auto-navigate to job details after creating job
   - Auto-refresh data without manual page reload
   - Auto-highlight concerning metrics or errors
   - Auto-suggest actions based on job state

2. **Simplification Opportunities**: 
   - Provide summary view for quick checks
   - Hide advanced analytics behind "Show More"
   - Focus on most important metrics by default
   - Progressive disclosure of complexity

3. **Transition Smoothness**: 
   - Smooth navigation from multiple entry points
   - Seamless switching between chart types
   - Natural flow through different sections
   - Easy return to previous context

4. **User Trust**: 
   - Accurate real-time data builds confidence
   - Transparent status information
   - Clear success/failure indicators
   - Verifiable results through IdeaBlocks view

5. **Cognitive Load**: 
   - Don't require understanding of technical processing details
   - Use visual representations (charts) for complex data
   - Clear labels and legends
   - Logical organization of information

---

## Related Flows

- [Create New Blockify Job](../05-blockify-processing/create-blockify-job.md) - Creates jobs to monitor
- [Monitor Job Progress in Real-Time](./monitor-job-progress.md) - Focused progress monitoring
- [View Individual File Analytics](./view-file-analytics.md) - Drill into specific files
- [View Job Performance Charts](./view-job-charts.md) - Detailed chart exploration
- [Cancel a Running Job](./cancel-running-job.md) - Action from job details
- [Retry a Failed Job](./retry-failed-job.md) - Recovery action
- [View Active Jobs Status Badge](./view-job-status-indicator.md) - Entry point to job details

---

## Technical References

**Knowledge Base Sections**:
- src/components/jobs/blockify-job-processing-screen/index.js - Main dashboard component
- src/components/jobs/blockify-job-processing-screen/charts/ - Chart components
- src/components/jobs/blockify-job-processing-screen/ui/ - UI components
- src/components/jobs/blockify-job-processing-screen/utils.js - Progress calculations
- src/handlers/job-fs-storage.js - Job data retrieval

**Key Components**:
- Multi-section dashboard with real-time updates
- Progress timeline with layered visualization
- Metrics cards with live data
- Interactive charts with multiple types
- File selector for granular analysis
- IdeaBlocks viewer

---

## Version History

| Date | Version | Author | Changes |
|------|---------|--------|---------|
| 2025-10-04 | 1.1 | [Iternal Technologies](https://iternal.ai/airgapai) | Initial comprehensive documentation |

---

## Notes

**Important Considerations**:
- Dashboard updates automatically for active jobs (every 2 seconds)
- Completed jobs show final static data
- Large jobs may have extensive data; charts help visualize patterns
- File-level analysis available for detailed investigation
- Developer notes are optional; use for tracking experiments or observations

**Dashboard Sections Explained**:
- **Progress Timeline**: Shows which stage job is in and overall completion
- **Metrics Cards**: Quick-glance statistics for job overview
- **Analytics**: Deep-dive analysis with charts and granular views
- **IdeaBlocks Viewer**: Browse actual structured output

**Four Processing Stages**:
1. **Text Extraction**: Pull text content from uploaded files (PDF, DOCX, etc.)
2. **Blockification**: AI processes text into structured IdeaBlocks (or chunks for basic mode)
3. **Embeddings**: Generate vector representations for semantic search
4. **Dataset Creation**: Compile into searchable dataset file

**Best Practices**:
- Check job details shortly after creation to verify processing started
- Monitor progress periodically for long jobs
- Review completed jobs to understand quality and performance
- Use file-level analysis if some files seem problematic
- Download reports for documentation or comparison
- Add notes about unusual patterns or insights

**Common User Questions**:
- "Why isn't progress updating?" - May need to refresh page; check if job is actually running
- "What do the different colored layers mean?" - Each color is a processing stage
- "Can I speed up processing?" - Not actively; processing speed depends on hardware and model
- "Why are some files faster than others?" - Varies by file size, complexity, and content structure
- "What does the chunksper minute rate mean?" - How fast the AI is processing document chunks

