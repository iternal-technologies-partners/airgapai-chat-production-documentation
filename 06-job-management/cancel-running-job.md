# Cancel a Running Job

## Overview
**Flow ID**: `cancel-running-job`  
**Category**: Job Management  
**Estimated Duration**: 30 seconds  
**User Role**: All Users  
**Complexity**: Simple  

**Purpose**: This flow allows users to stop a currently processing job, terminating all active tasks and preventing further processing. This is useful when users need to reconfigure settings, realize they uploaded wrong files, or need to free up system resources.

---

## Trigger

**What initiates this flow:**
- [x] User manually initiates

**Specific trigger**: User needs to stop an active job, typically because:
- Wrong files were uploaded
- Settings need to be changed
- System resources needed for other tasks
- Job taking too long
- Discovered errors in configuration

---

## Prerequisites

**Before starting, users must have:**
- [x] Job currently running (status: Processing or Active)
- [x] Access to job details or jobs list

---

## User Intent Analysis

### Primary Intent
Immediately stop a running job to prevent further processing and free up system resources.

### Secondary Intents
- Avoid wasting resources on incorrect configuration
- Reconfigure and restart properly
- Free up system for other tasks
- Prevent creation of unwanted dataset

---

## Step-by-Step Flow

### Main Path

**Step 1: Access Running Job**
- **User Action**: Navigate to job details (click status badge, or go to Jobs list and click job)
- **System Response**: Job details page displays
- **UI Elements Visible**: 
  - Job dashboard showing active processing
  - Progress indicators animating
  - Status: "Processing" or "Active"
  - "Cancel Job" button in progress timeline or header
- **Visual Cues**: Animated progress, blue processing indicators

**Step 2: Locate Cancel Button**
- **User Action**: Find "Cancel" or "Cancel Job" button
- **System Response**: Button visible when job is cancellable
- **UI Elements Visible**: 
  - "Cancel Job" button (may be red or warning-styled)
  - Located in progress timeline section or header actions
- **Visual Cues**: Warning color (red/orange) indicates destructive action

**Step 3: Click Cancel**
- **User Action**: Click "Cancel Job" button
- **System Response**: 
  - Confirmation dialog may appear
  - OR job cancels immediately
- **UI Elements Visible**: 
  - **If confirmation**: Modal asking "Are you sure you want to cancel this job?"
  - Warning text about stopping in progress
  - "Cancel" (keep running) and "Confirm" (stop job) buttons
  - **If no confirmation**: Immediate cancellation
- **Visual Cues**: Warning-styled confirmation

**Step 4: Confirm Cancellation**
- **User Action**: If confirmation appears, click "Confirm" or "Yes, Cancel Job"
- **System Response**: 
  - Active tasks stop immediately
  - Job status changes to "Cancelled"
  - Progress stops advancing
  - Processing engines release tasks
- **UI Elements Visible**: 
  - Status badge updates to "Cancelled" (gray or yellow)
  - Progress bar stops animating
  - "Cancel Job" button disappears
  - "Retry Job" button may appear
- **Visual Cues**: 
  - Animation stops
  - Status color changes
  - Visual indication of stopped state

**Step 5: Job Cancellation Completes**
- **User Action**: Observe updated job state
- **System Response**: 
  - All processing stopped
  - Partial results preserved
  - System resources freed
- **UI Elements Visible**: 
  - Status: "Cancelled"
  - Progress frozen at last point
  - Partial metrics showing work completed before cancellation
  - "Retry" button available
- **Visual Cues**: 
  - Static (non-animated) status
  - Gray or yellow cancelled color

**Final Step: Job Cancelled**
- **Success Indicator**: 
  - Job no longer processing
  - Status shows "Cancelled"
  - System resources freed
  - Can retry or delete job
- **System State Change**: 
  - Job status: Cancelled
  - Processing tasks terminated
  - Partial results preserved
  - Can be restarted if desired
- **Next Possible Actions**: 
  - Retry job with corrections
  - Delete job
  - Review partial results
  - Create new job with correct configuration

---

## Alternative Paths & Strategies

### Strategy A: Cancel from Status Badge
**When to use**: Quick cancellation without viewing details

**Steps**:
1. Click status badge in bottom-right
2. See list of active jobs
3. Identify job to cancel
4. Look for cancel option in badge modal
5. Cancel from modal if available

**QA Note**: Cancel from badge not confirmed. May require navigating to job details.

### Strategy B: Let Job Complete Then Delete
**When to use**: Job nearly complete or cancellation problematic

**Steps**:
1. Allow job to finish
2. Don't activate resulting dataset
3. Delete job and dataset after completion
4. Create new job properly configured

---

## Error States & Recovery

### Error 1: Cancel Button Not Available
**Cause**: Job not in cancellable state  
**User Experience**: 
  - No cancel button visible
  - Job may be in state that can't be cancelled

**Recovery Steps**:
1. Check job status (may be already completed, failed, or cancelled)
2. If stuck in uncancellable state, restart application
3. Job should normalize to proper state

### Error 2: Cancellation Doesn't Stop Processing
**Cause**: Tasks already running don't terminate immediately  
**User Experience**: 
- Status changes to "Cancelled" but processing continues briefly
- Progress may advance slightly more

**Recovery Steps**:
1. Wait 10-30 seconds for tasks to fully terminate
2. Progress should stop soon
3. If continues beyond 1 minute, indicates issue
4. May need to restart application

**QA Note**: Brief continuation normal as running tasks finish. Not an error unless excessive.

---

## Pain Points & Friction

**Identified Issues**:

1. **No Partial Save Option**
   - **Impact**: Cancelling loses all progress; can't save partial results
   - **Frequency**: Jobs cancelled after significant progress
   - **Potential Improvement**: 
     - "Cancel and Save Progress" option
     - Preserve completed work
     - Resume from checkpoint

2. **Cannot Pause Instead of Cancel**
   - **Impact**: Must fully cancel; can't temporarily pause
   - **Frequency**: Need system resources temporarily
   - **Potential Improvement**: 
     - Pause/resume functionality
     - Temporary suspension
     - Resource throttling instead of full stop

---

## Design Considerations

**Following Contextual Design Principles**:

1. **Automation Opportunities**: Auto-save progress before cancellation
2. **User Trust**: Confirmation prevents accidents
3. **Cognitive Load**: Simple cancel action

---

## Related Flows

- [View Job Details Dashboard](./view-job-details.md) - Access cancel option
- [Retry a Failed Job](./retry-failed-job.md) - Restart after cancellation
- [View Active Jobs Status Badge](./view-job-status-indicator.md) - Monitor before cancelling

---

## Technical References

**Knowledge Base Sections**:
- src/components/jobs/blockify-job-processing-screen/index.js - Cancel button
- src/handlers/index.js - cancelJob RPC
- src/localdb/jobs.js - Status update
- src/components/jobs/job-manager.js - Task termination

---

## Version History

| Date | Version | Author | Changes |
|------|---------|--------|---------|
| 2025-10-04 | 1.1 | [Iternal Technologies](https://iternal.ai/airgapai) | Initial comprehensive documentation |

---

## Notes

**Important Considerations**:
- Cancellation is immediate but running tasks may take seconds to fully stop
- Partial results are preserved (can review what completed before cancel)
- Cancelled jobs can be retried
- System resources freed after cancellation
- No undo for cancellation; must retry to resume

**Best Practices**:
- Verify job is truly incorrect before cancelling
- Let job complete if nearly done
- Review partial results before retrying
- Document why job was cancelled for future reference

**Common User Questions**:
- "Can I undo cancellation?" - No, but can retry job
- "Will I lose all progress?" - Progress stops; partial results preserved
- "How long until fully stopped?" - Usually seconds to 30 seconds
- "Can I resume from where it stopped?" - No, retry starts from beginning

