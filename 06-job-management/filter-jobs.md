# Filter Jobs by Status

## Overview
**Flow ID**: `filter-jobs`  
**Category**: Job Management  
**Estimated Duration**: 30 seconds  
**User Role**: All Users  
**Complexity**: Simple  

**Purpose**: Filter jobs table to show only jobs with specific status (pending, processing, completed, failed, or cancelled). Helps users quickly find jobs in particular states without scanning entire list.

---

## Trigger

**What initiates this flow:**
- [x] User manually initiates

**Specific trigger**: User wants to see jobs of specific type (e.g., only failed jobs to retry, only completed to review).

---

## User Intent Analysis

### Primary Intent
Quickly filter jobs list to show only jobs in desired state for targeted review or action.

### Secondary Intents
- Find failed jobs to retry
- See only active jobs for monitoring
- Review completed jobs
- Identify pending jobs waiting to start

---

## Step-by-Step Flow

### Main Path

**Step 1: Open Jobs Table**
- **User Action**: Navigate to Blockify > View Jobs
- **System Response**: Jobs table displays showing all jobs by default

**Step 2: Locate Status Filter**
- **User Action**: Find status filter dropdown in table header
- **UI Elements Visible**: 
  - "Status:" label
  - Dropdown showing "All" (default)
  - Down arrow indicating dropdown

**Step 3: Open Filter Dropdown**
- **User Action**: Click status filter dropdown
- **System Response**: Dropdown menu expands
- **UI Elements Visible**: 
  - Dropdown options:
    - All (shows everything)
    - Pending
    - Processing
    - Completed
    - Failed
    - Cancelled
  - Current selection highlighted

**Step 4: Select Status**
- **User Action**: Click desired status option
- **System Response**: 
  - Dropdown closes
  - Table immediately filters to show only matching jobs
  - Job count updates
- **UI Elements Visible**: 
  - Selected status shown in dropdown
  - Filtered job list
  - Updated count: e.g., "5 failed jobs" or "Showing 5 jobs"
  - Only jobs with selected status visible

**Step 5: Review Filtered Jobs**
- **User Action**: Scan filtered list
- **System Response**: Table shows only matching jobs
- **UI Elements Visible**: 
  - Subset of jobs matching filter
  - All matching jobs in table
  - Action buttons appropriate for status

**Step 6: Clear Filter (Optional)**
- **User Action**: Select "All" from dropdown
- **System Response**: 
  - Filter clears
  - Full job list shown again

**Final Step: Jobs Filtered Successfully**
- **Success Indicator**: Table shows only desired job status
- **System State Change**: View filtered (display only, data unchanged)
- **Next Possible Actions**: 
  - Act on filtered jobs (retry, view, etc.)
  - Change filter to different status
  - Clear filter to see all

---

## Error States & Recovery

**QA Note**: Simple filter with no error conditions. Filtering is display operation that cannot fail in traditional sense.

---

## Pain Points & Friction

**Identified Issues**:

1. **Single Status Filter Only**
   - **Impact**: Cannot select multiple statuses (e.g., both Failed and Cancelled)
   - **Potential Improvement**: Multi-select filter

2. **Filter Doesn't Persist**
   - **Impact**: Resets when leaving page
   - **Potential Improvement**: Remember filter preference

---

## Design Considerations

**Following Contextual Design Principles**:

1. **Simplification Opportunities**: Simple dropdown works well
2. **User Trust**: Reliable, instant filtering
3. **Cognitive Load**: Familiar filter pattern

---

## Related Flows

- [View All Jobs in Table](./view-jobs-table.md) - Parent flow
- [Retry a Failed Job](./retry-failed-job.md) - Common action after filtering to failed

---

## Technical References

**Knowledge Base Sections**:
- src/components/jobs/blockify-jobs-table/index.js - Filter implementation

---

## Version History

| Date | Version | Author | Changes |
|------|---------|--------|---------|
| 2025-10-04 | 1.1 | [Iternal Technologies](https://iternal.ai/airgapai) | Initial documentation |

---

## Notes

**Best Practices**:
- Filter to "Failed" to find jobs needing retry
- Filter to "Active" for current monitoring
- Use "All" for comprehensive review

**Common User Questions**:
- "Can I select multiple statuses?" - No, one at a time currently
- "Does filter affect data?" - No, only changes what's displayed

