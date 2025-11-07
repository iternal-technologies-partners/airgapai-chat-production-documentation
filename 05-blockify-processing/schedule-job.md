# Schedule Job for Future Execution

## Overview
**Flow ID**: `schedule-job`  
**Category**: Blockify Processing  
**Estimated Duration**: 1-2 minutes  
**User Role**: All Users  
**Complexity**: Simple  

**Purpose**: Configure job to start processing automatically at specified future date and time instead of immediately. Useful for scheduling resource-intensive processing during off-hours or specific times.

---

## Trigger

**What initiates this flow:**
- [x] User manually initiates

**Specific trigger**: User wants job to run at future time, typically because:
- Want processing during overnight hours
- Need to use computer now, run job later
- Coordinating with other scheduled tasks
- Running during low-usage periods

---

## User Intent Analysis

### Primary Intent
Set future start time for job to optimize resource usage or coordinate with user's schedule.

### Secondary Intents
- Avoid disrupting current work
- Utilize off-peak system resources
- Batch multiple jobs at specific time
- Plan processing around schedule

---

## Step-by-Step Flow

### Main Path

**Step 1: Configure Job Normally**
- **User Action**: Complete normal job setup (files, settings, etc.)
- **System Response**: Job configuration ready
- **UI Elements Visible**: Job creation form filled out

**Step 2: Locate Schedule Picker**
- **User Action**: Find "Schedule Job" option or calendar icon in job configuration
- **System Response**: N/A
- **UI Elements Visible**: 
  - Calendar icon or "Schedule for Later" button
  - Typically near dataset selection or at bottom of form
  - Current value: "Run Immediately" or schedule time if set

**Step 3: Click Schedule Picker**
- **User Action**: Click calendar icon or schedule button
- **System Response**: Date/time picker appears
- **UI Elements Visible**: 
  - Date picker modal or popup
  - Calendar interface showing current month
  - Time selector (hours and minutes)
  - Today's date highlighted
  - "Clear" or "Remove Schedule" button
  - "Confirm" or "Set Schedule" button

**Step 4: Select Future Date**
- **User Action**: Click on desired date in calendar
- **System Response**: 
  - Selected date highlights
  - Time selector becomes active
- **UI Elements Visible**: 
  - Calendar with selected date highlighted
  - Date updates in picker header
  - Time selector ready

**Step 5: Set Time**
- **User Action**: Select hour and minute for job start
- **System Response**: 
  - Time value updates
  - Full datetime shown: "Oct 5, 2025 10:00 PM"
- **UI Elements Visible**: 
  - Time dropdown or input
  - Selected time displayed
  - Combined date and time preview

**Step 6: Confirm Schedule**
- **User Action**: Click "Confirm" or "Set Schedule" button
- **System Response**: 
  - Picker closes
  - Scheduled time displayed in job form
  - Job creation button may change to "Schedule Job"
- **UI Elements Visible**: 
  - Schedule indicator: "Scheduled for: Oct 5, 2025 at 10:00 PM"
  - Calendar icon now shows scheduled state
  - Time until start may be shown: "In 18 hours"

**Step 7: Create Scheduled Job**
- **User Action**: Click "Create Job" or "Schedule Job" button
- **System Response**: 
  - Job created with scheduled status
  - Redirects to job details
  - Job shows "Scheduled" status
- **UI Elements Visible**: 
  - Job details page
  - Status: "Scheduled" (teal badge)
  - Scheduled time prominently displayed
  - Countdown: "Starts in 17 hours 58 minutes"
  - Warning: "Keep application open for job to start"

**Step 8: Job Awaits Scheduled Time**
- **User Action**: Can close details page, job waits in background
- **System Response**: 
  - Job remains in "Scheduled" status
  - Countdown continues
  - Application must remain open for job to start
- **UI Elements Visible**: 
  - In jobs list: Job shows "Scheduled" with time
  - Status badge may show scheduled in teal/info color

**Step 9: Scheduled Time Arrives**
- **User Action**: None (if application is open)
- **System Response**: 
  - Job automatically changes from "Scheduled" to "Pending"
  - Processing queue picks up job
  - Job begins processing automatically
  - Status changes to "Processing"
- **UI Elements Visible**: 
  - Status badge updates: Scheduled → Pending → Processing
  - Progress begins advancing

**Final Step: Scheduled Job Executes**
- **Success Indicator**: 
  - Job started at scheduled time
  - Processing automatically
  - No manual intervention needed
- **System State Change**: 
  - Job status progression: Scheduled → Pending → Active → Processing
  - Automatic execution at specified time
- **Next Possible Actions**: 
  - Monitor processing
  - Let job complete unattended
  - Check results later

---

## Alternative Paths & Strategies

### Strategy A: Cancel Schedule Before Execution
**When to use**: Change plans before scheduled time

**Steps**:
1. Open scheduled job details
2. Click "Cancel Job" or edit schedule
3. Job cancelled or rescheduled
4. Can reschedule or start immediately

### Strategy B: Reschedule Job
**When to use**: Need to change scheduled time

**Steps**:
1. Open job details
2. Click schedule picker again (if accessible)
3. Select new date/time
4. Confirm changes
5. Job updates to new schedule

**QA Note**: Reschedule capability not confirmed in knowledge base. May need to cancel and recreate.

### Strategy C: Batch Multiple Scheduled Jobs
**When to use**: Schedule several jobs for same time

**Steps**:
1. Create first job, schedule for specific time
2. Create second job, schedule for same time
3. Repeat for all jobs
4. All jobs start at scheduled time
5. Process in queue order (based on priority)

---

## Error States & Recovery

### Error 1: Cannot Select Past Date
**Cause**: User tries to schedule for time that already passed  
**User Experience**: 
- Past dates may be disabled/grayed in calendar
- Or error message: "Cannot schedule in the past"
- Schedule not accepted

**Recovery Steps**:
1. Select current or future date
2. Verify time zone is correct
3. Choose appropriate future time

**QA Note**: UI should prevent selecting past dates. Error only if validation fails.

### Error 2: Job Doesn't Start at Scheduled Time
**Cause**: Application was closed or system was asleep  
**User Experience**: 
- Scheduled time passes
- Job still shows "Scheduled" status
- Processing didn't start

**Recovery Steps**:
1. Application must be open for scheduled jobs
2. If application was closed, job won't start
3. Open application to trigger pending scheduled jobs
4. Job should start when application detects time has passed
5. Or manually start job if needed

**Important**: Application must remain running for scheduled jobs. Closing application prevents scheduled execution.

### Error 3: Schedule Cleared Accidentally
**Cause**: User interaction cleared schedule  
**User Experience**: 
- Schedule shows "Run Immediately" instead of scheduled time
- Schedule lost

**Recovery Steps**:
1. Reschedule if job not yet created
2. If job created without schedule, will run immediately
3. Cancel and recreate with schedule if needed

---

## Pain Points & Friction

**Identified Issues**:

1. **Must Keep Application Open**
   - **Impact**: Application must run continuously until scheduled time
   - **Frequency**: Every scheduled job
   - **Potential Improvement**: 
     - System-level scheduling (even when app closed)
     - Wake-on-schedule if possible
     - Clear warning about requirement
     - Cloud/server-based scheduling

2. **No Recurring Schedules**
   - **Impact**: Cannot schedule daily/weekly job automatically
   - **Frequency**: Users wanting regular processing
   - **Potential Improvement**: 
     - Recurring schedule options
     - Daily, weekly, monthly templates
     - Cron-like scheduling

3. **Limited Scheduling Interface**
   - **Impact**: Can only schedule one specific time
   - **Frequency**: Users wanting conditional scheduling
   - **Potential Improvement**: 
     - "Start when idle" option
     - "Start in X hours" quick options
     - Time range instead of exact time

4. **No Notification When Job Starts**
   - **Impact**: User may not notice job began at scheduled time
   - **Frequency**: Scheduled jobs that start while user away
   - **Potential Improvement**: 
     - Desktop notification when job starts
     - Email/alert option
     - Visible indication in interface

5. **Cannot Edit Schedule After Job Created**
   - **Impact**: Must cancel and recreate to change schedule
   - **Frequency**: When schedules need adjustment
   - **Potential Improvement**: 
     - Edit schedule on job details page
     - Reschedule button for scheduled jobs
     - Drag-and-drop schedule management

---

## Design Considerations

**Following Contextual Design Principles**:

1. **Automation Opportunities**: 
   - Auto-schedule for next off-peak time
   - Suggest optimal times based on system load
   - Auto-start when system idle
   - Remember user's preferred schedule times

2. **Simplification Opportunities**: 
   - Quick time options: "Tonight at midnight", "Tomorrow morning", "In 4 hours"
   - Reduce clicks with smart defaults
   - Calendar with highlighted recommended times

3. **Transition Smoothness**: 
   - Clear confirmation of schedule
   - Obvious scheduled state in all views
   - Smooth automatic start at scheduled time
   - No user intervention needed for execution

4. **User Trust**: 
   - Clear indication job is scheduled (not forgotten)
   - Countdown shows time remaining
   - Warning about keeping application open
   - Automatic execution works reliably

5. **Cognitive Load**: 
   - Familiar calendar picker interface
   - Clear display of scheduled time
   - Simple decision (when to run)
   - No complex configuration

---

## Related Flows

- [Create New Blockify Job](./create-blockify-job.md) - Parent workflow including scheduling
- [Create Basic Chunking Job](./create-chunking-job.md) - Can also be scheduled
- [View Job Details Dashboard](../06-job-management/view-job-details.md) - Shows schedule information
- [Cancel a Running Job](../06-job-management/cancel-running-job.md) - Can cancel scheduled jobs

---

## Technical References

**Knowledge Base Sections**:
- src/components/ui/schedule-job-picker.js - Scheduling interface
- src/components/jobs/job-manager.js - Scheduled job execution
- src/localdb/jobs.js - Schedule persistence
- src/constants/jobs.js - Job status including SCHEDULED

**Key Components**:
- Date/time picker component
- Scheduled job timer system
- Automatic job start mechanism
- Schedule display in job details

---

## Version History

| Date | Version | Author | Changes |
|------|---------|--------|---------|
| 2025-10-04 | 1.1 | [Iternal Technologies](https://iternal.ai/airgapai) | Initial comprehensive documentation |

---

## Notes

**Important Considerations**:
- **Application must remain open** for scheduled jobs to start (critical limitation)
- System doesn't wake up application or start if closed
- Schedule stored in database; persists across page refreshes but not application restarts
- Scheduled jobs appear in jobs list with "Scheduled" status
- Can have multiple jobs scheduled for different times
- Jobs start automatically when scheduled time arrives (if app is open)
- Can cancel scheduled job before it starts

**Time Display**:
- Absolute time: "Oct 5, 2025 at 10:00 PM"
- Relative time: "In 18 hours 32 minutes" (updates automatically)
- Both may be shown for clarity

**Scheduling Best Practices**:
- Schedule resource-intensive jobs for overnight
- Set schedule at least 5-10 minutes in future (not immediate)
- Ensure computer won't sleep or shut down
- Keep application in foreground or background (open)
- Verify schedule before creating job
- Note scheduled time for reference

**Common User Questions**:
- "Will job run if I close the application?" - No, application must remain open
- "Can I schedule for tomorrow?" - Yes, select any future date
- "What time zone is used?" - Your local system time
- "Can I cancel scheduled job?" - Yes, before it starts
- "Will my computer need to stay on?" - Yes, don't shut down or sleep before scheduled time
- "Can I schedule recurring jobs?" - No, currently one-time scheduling only
- "What if I miss the scheduled time?" - Job starts when you next open application (if time has passed)

