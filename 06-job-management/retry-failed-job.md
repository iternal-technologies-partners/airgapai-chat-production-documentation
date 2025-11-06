# Retry a Failed Job

## Overview
**Flow ID**: `retry-failed-job`  
**Category**: Job Management  
**Estimated Duration**: 30 seconds (to initiate)  
**User Role**: All Users  
**Complexity**: Simple  

**Purpose**: This flow allows users to restart a job that previously failed or was cancelled. The retry attempts to process the job again from the beginning, giving users a chance to succeed after resolving the issue that caused the original failure.

---

## Trigger

**What initiates this flow:**
- [x] User manually initiates

**Specific trigger**: User has a failed or cancelled job they want to run again after addressing the cause of failure.

---

## Prerequisites

**Before starting, users must have:**
- [x] Job with status "Failed" or "Cancelled"
- [x] Issue causing failure resolved (if applicable)
- [x] System resources available for processing

---

## User Intent Analysis

### Primary Intent
Restart failed job to successfully complete the processing after resolving issues.

### Secondary Intents
- Recover from temporary failures
- Complete partially finished work
- Avoid recreating entire job configuration

---

## Step-by-Step Flow

### Main Path (Happy Path)

**Step 1: Locate Failed Job**
- **User Action**: Navigate to Jobs list (Blockify > View Jobs tab) or job details
- **System Response**: Jobs list shows failed job with status badge
- **UI Elements Visible**: 
  - Job with "Failed" or "Cancelled" status badge (red or gray)
  - "Retry" button in actions column
- **Visual Cues**: Red failure badge or gray cancelled badge

**Step 2: Review Failure Details**
- **User Action**: Optionally click job to view details and understand why it failed
- **System Response**: Job details show error information
- **UI Elements Visible**: 
  - Error message explaining failure
  - Partial results (if any)
  - Failed files or stages highlighted
- **Visual Cues**: Error indicators and messages

**Step 3: Click Retry Button**
- **User Action**: Click "Retry" button
- **System Response**: 
  - Job status resets to "Pending"
  - Job enters queue for processing
  - Status badge updates
- **UI Elements Visible**: 
  - Status changes to "Pending" (yellow badge)
  - Progress timeline resets to 0%
  - "Retry" button disappears
  - "Cancel" button becomes available
- **Visual Cues**: Status color changes, job enters processing queue

**Step 4: Job Restarts Processing**
- **User Action**: Wait for job to begin (typically within seconds)
- **System Response**: 
  - Job status changes to "Processing" or "Active"
  - Processing begins from start
  - Progress indicators activate
- **UI Elements Visible**: 
  - Status: "Processing" (blue badge)
  - Progress bar at 0% and beginning to advance
  - Metrics resetting and updating
- **Visual Cues**: Animated progress indicators

**Final Step: Job Retry Initiated**
- **Success Indicator**: 
  - Job is processing again
  - Progress advancing normally
  - No immediate errors
- **System State Change**: 
  - Job status: Pending → Active/Processing
  - Processing queue includes job
  - Fresh attempt at completion
- **Next Possible Actions**: 
  - Monitor progress
  - Cancel if issues recur
  - Wait for completion

---

## Alternative Paths & Strategies

### Strategy A: Retry with Configuration Changes
**When to use**: Need to modify settings before retrying

**Steps**:
1. Note why job failed
2. Delete failed job
3. Create new job with corrected configuration
4. More reliable than retry if settings were wrong

**QA Note**: Retry uses same configuration. For setting changes, new job required.

### Strategy B: Retry Individual Files
**When to use**: Only some files failed

**Steps**:
1. View job details
2. Identify which files failed
3. Remove failed files
4. Add corrected versions
5. Retry job

**QA Note**: File-level retry not confirmed. Current retry is full job restart.

---

## Error States & Recovery

### Error 1: Retry Fails Again
**Cause**: Underlying issue not resolved  
**User Experience**: 
- Job fails again with same or different error
- Back to failed status

**Recovery Steps**:
1. Review error message carefully
2. Address root cause before retrying again
3. Common issues:
   - Insufficient disk space
   - Incompatible files
   - System resource limitations
4. Fix issue and retry again

### Error 2: Retry Button Not Available
**Cause**: Job in state that can't be retried  
**User Experience**: 
- No retry button visible
- Job may be already processing or completed

**Recovery Steps**:
1. Check job status
2. If processing, let it continue
3. If completed, no retry needed
4. If stuck, restart application

---

## Pain Points & Friction

**Identified Issues**:

1. **No Indication of What Changed**
   - **Impact**: Don't know if retry will succeed
   - **Frequency**: Every retry
   - **Potential Improvement**: 
     - Show what was fixed
     - Require acknowledging fix before retry
     - Provide fix suggestions

2. **Full Restart (No Resume from Checkpoint)**
   - **Impact**: Loses all completed work
   - **Frequency**: Jobs that fail late in process
   - **Potential Improvement**: 
     - Resume from last successful stage
     - Preserve completed files
     - Incremental retry

---

## Design Considerations

**Following Contextual Design Principles**:

1. **Automation Opportunities**: Auto-retry transient failures
2. **Simplification Opportunities**: One-click retry
3. **User Trust**: Clear retry will start fresh
4. **Cognitive Load**: Simple retry action

---

## Related Flows

- [Cancel a Running Job](./cancel-running-job.md) - Stop before failure
- [View Job Details Dashboard](./view-job-details.md) - Review before retry
- [Create New Blockify Job](../05-blockify-processing/create-blockify-job.md) - Alternative to retry

---

## Technical References

**Knowledge Base Sections**:
- src/handlers/index.js - restartJob RPC
- src/localdb/jobs.js - Status reset
- src/components/jobs/job-manager.js - Job restart handling

---

## Version History

| Date | Version | Author | Changes |
|------|---------|--------|---------|
| 2025-10-04 | 1.1 | [Iternal Technologies](https://iternal.ai/airgapai) | Initial comprehensive documentation |

---

## Notes

**Important Considerations**:
- Retry starts job completely fresh (no partial resume)
- Must resolve failure cause before retry
- Same configuration used unless job recreated
- Retry can be repeated multiple times if needed

**Best Practices**:
- Understand failure cause before retrying
- Check system resources adequate
- Verify files aren't corrupted
- Monitor retry closely for same failure

**Common User Questions**:
- "Will retry work if I didn't change anything?" - No, same config will likely fail again
- "Can I modify settings before retry?" - No, must delete and create new job
- "Does retry preserve any progress?" - No, starts from beginning
- "How many times can I retry?" - Unlimited, but fix issues first

