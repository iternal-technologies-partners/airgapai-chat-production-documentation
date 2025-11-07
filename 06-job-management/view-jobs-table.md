# View All Jobs in Table

## Overview
**Flow ID**: `view-jobs-table`  
**Category**: Job Management  
**Estimated Duration**: 1-2 minutes  
**User Role**: All Users  
**Complexity**: Simple  

**Purpose**: View comprehensive list of all processing jobs (past and present) in table format with sorting, filtering, and status information. Provides overview of all document processing activity.

---

## Trigger

**What initiates this flow:**
- [x] User manually initiates

**Specific trigger**: User wants to see all jobs, review history, or find specific job.

---

## Prerequisites

**Before starting, users must have:**
- [x] Application running
- [x] At least one job created (active or historical)

---

## User Intent Analysis

### Primary Intent
View complete list of all jobs to understand processing history, find specific jobs, or monitor multiple active jobs.

### Secondary Intents
- Track job completion status
- Review historical processing
- Find jobs for retry or review
- Understand system usage patterns

---

## Step-by-Step Flow

### Main Path

**Step 1: Navigate to Jobs Table**
- **User Action**: Click "Blockify" in navigation, then click "View Jobs" tab
- **System Response**: Jobs table page loads
- **UI Elements Visible**: 
  - "View Jobs" tab highlighted
  - View switcher: "Active Jobs" / "All Jobs" (toggle buttons)
  - Job count badge showing total
  - Status filter dropdown (All, Pending, Processing, Completed, Failed, Cancelled)
  - Jobs table with columns:
    - Job name
    - Status
    - Files (completed/total)
    - Unique Items
    - Total Time
    - Started
    - Actions

**Step 2: Review Jobs List**
- **User Action**: Scan table to see all jobs
- **System Response**: Jobs displayed in table format
- **UI Elements Visible**: 
  - Each job row showing:
    - Job name and subtitle (dataset name or description)
    - Status badge (color-coded: green=completed, blue=processing, red=failed, gray=cancelled, yellow=pending)
    - File progress: "5 of 10 files complete"
    - Unique items count: "2,450 items"
    - Total time: "15m 32s" or similar
    - Started time: "2 hours ago"
    - Action buttons: View, Retry (if failed), Cancel (if active)
  - Jobs sorted by most recent first
- **Visual Cues**: 
  - Color-coded status badges immediate visual scanning
  - Table layout organized for easy comparison
  - Hover effects on rows

**Step 3: Switch Between Views (Optional)**
- **User Action**: Click "Active Jobs" or "All Jobs" toggle button
- **System Response**: Table filters to show selected view
- **UI Elements Visible**: 
  - **Active Jobs**: Only shows jobs currently running or queued
  - **All Jobs**: Shows complete history including completed
  - Selected view button highlighted
  - Job count updates to reflect filtered list

**Step 4: Navigate to Job Details**
- **User Action**: Click "View" button or click anywhere on job row
- **System Response**: 
  - Navigates to job details dashboard
  - Full job information loads
- **UI Elements Visible**: Job details page (see view-job-details.md)

**Final Step: Jobs Reviewed**
- **Success Indicator**: 
  - Viewed job history
  - Understood status of all jobs
  - Can access details for any job
- **System State Change**: User has awareness of all processing activity
- **Next Possible Actions**: 
  - View details of specific job
  - Retry failed jobs
  - Cancel active jobs
  - Create new job

---

## Alternative Paths & Strategies

### Strategy A: Filter by Status
**When to use**: Looking for jobs in specific state

**Steps**:
1. Open jobs table
2. Click status filter dropdown
3. Select status (e.g., "Completed")
4. Table shows only jobs with that status

### Strategy B: Quick Status Check
**When to use**: Just verifying jobs are running

**Steps**:
1. Open jobs table
2. Click "Active Jobs" view
3. See only currently processing jobs
4. Verify they're progressing
5. Return to other work

---

## Error States & Recovery

### Error 1: Jobs List Empty
**Cause**: No jobs created yet  
**User Experience**: 
- Empty table
- Message: "No jobs found" or "Create your first job"

**Recovery Steps**:
1. This is normal for new users
2. Create first job via Blockify page
3. Table will populate

**QA Note**: Not error - expected for new users.

### Error 2: Jobs List Won't Load
**Cause**: Database or system error  
**User Experience**: 
- Loading indicator continues
- Error message
- Empty or broken table

**Recovery Steps**:
1. Refresh page
2. Check if jobs exist (try creating new one)
3. Restart application if persists

---

## Pain Points & Friction

**Identified Issues**:

1. **No Search Across Jobs**
   - **Impact**: Must scan visually to find specific job
   - **Potential Improvement**: Search by job name, dataset name

2. **Limited Sorting Options**
   - **Impact**: Only sorted by date
   - **Potential Improvement**: 
     - Sort by status, name, duration
     - Custom sort orders

3. **No Bulk Actions**
   - **Impact**: Must handle jobs individually
   - **Potential Improvement**: 
     - Select multiple jobs
     - Bulk retry, delete, or cancel

---

## Design Considerations

**Following Contextual Design Principles**:

1. **Automation Opportunities**: Auto-refresh when jobs update
2. **Simplification Opportunities**: Clear visual status indicators
3. **User Trust**: Accurate job status display

---

## Related Flows

- [View Job Details Dashboard](./view-job-details.md) - Drill into specific job
- [Filter Jobs by Status](./filter-jobs.md) - Detailed filtering
- [Retry a Failed Job](./retry-failed-job.md) - Action from table
- [Cancel a Running Job](./cancel-running-job.md) - Action from table

---

## Technical References

**Knowledge Base Sections**:
- src/components/jobs/blockify-jobs-table/index.js - Jobs table component
- src/components/jobs/blockify-jobs-table/table.js - Table rendering
- src/reducers/jobs.js - Jobs state

---

## Version History

| Date | Version | Author | Changes |
|------|---------|--------|---------|
| 2025-10-04 | 1.1 | [Iternal Technologies](https://iternal.ai/airgapai) | Initial comprehensive documentation |

---

## Notes

**Table Columns Explained**:
- **Job**: Name and dataset/description
- **Status**: Current processing state
- **Files**: How many files processed
- **Unique Items**: Total structured items created
- **Total Time**: Duration from start to finish (or current elapsed)
- **Started**: When job began (relative time: "2 hours ago")
- **Actions**: Available operations (View, Retry, Cancel)

**Status Colors**:
- Green: Completed
- Blue: Processing/Active
- Red: Failed
- Yellow: Pending/Queued
- Gray: Cancelled
- Orange: Paused
- Teal: Scheduled

**Best Practices**:
- Regularly review completed jobs
- Clean up old completed jobs periodically
- Use Active Jobs view for current monitoring
- Use All Jobs for historical reference

**Common User Questions**:
- "Can I delete jobs from this list?" - Yes, typically via job details or actions menu
- "Why are some jobs grayed out?" - Cancelled or paused status
- "Can I sort differently?" - Limited sorting; primarily by date
- "How far back does history go?" - All jobs unless manually deleted

