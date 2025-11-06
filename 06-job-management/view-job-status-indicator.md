# View Active Jobs Status Badge

## Overview
**Flow ID**: `view-job-status-indicator`  
**Category**: Job Management  
**Estimated Duration**: Ongoing (passive monitoring)  
**User Role**: All Users  
**Complexity**: Simple  

**Purpose**: This flow describes how users monitor background job processing through a persistent status badge that appears in the bottom-right corner of the screen when jobs are running. The badge provides at-a-glance status of processing jobs without requiring users to navigate away from their current task.

---

## Trigger

**What initiates this flow:**
- [ ] User manually initiates
- [x] System event (job processing starts or is ongoing)

**Specific trigger**: A background processing job (blockify or chunking) becomes active, is currently processing, or is queued, causing the system to automatically display a status indicator.

---

## Prerequisites

**Before starting, users must have:**
- [x] Application installed and running
- [x] At least one job created that is processing or queued
- [x] User can be on any page of the application

---

## User Intent Analysis

### Primary Intent
Maintain awareness of background job status without needing to actively check or navigate to a dedicated jobs page, enabling users to continue other work while monitoring progress passively.

### Secondary Intents
- Know when jobs complete without constant checking
- Identify if jobs encounter errors
- Track processing progress at a glance
- Understand system load (how many jobs are running)
- Access job details quickly if needed

### Subintents
- Avoid interrupting current workflow to check job status
- Get notified of completion without missing it
- Detect problems early through visual indicators

---

## Step-by-Step Flow

### Main Path (Happy Path)

**Step 1: Job Processing Begins**
- **User Action**: None required (system-initiated)
- **System Response**: 
  - Job processing starts (either immediately after creation or when scheduled time arrives)
  - Status badge appears in bottom-right corner
  - Badge shows initial state
- **UI Elements Visible**: 
  - Small, circular or rounded badge in bottom-right of screen (fixed position)
  - Badge color (typically green for active, orange for loading)
  - Badge text showing status (e.g., "1 in progress")
  - Animated pulsing effect on badge
- **Visual Cues**: 
  - Badge appearance draws attention
  - Pulsing animation indicates active processing
  - Position stays fixed even when scrolling

**Step 2: Passive Awareness**
- **User Action**: User continues working on current task (chat, settings, browsing datasets, etc.) while periodically glancing at badge
- **System Response**: Badge remains visible and updates automatically
- **UI Elements Visible**: 
  - Status badge persistently displayed in corner
  - Badge updates without user interaction
  - Badge text may change as jobs progress (e.g., "1 in progress, 1 pending")
  - Color may change based on state
- **Visual Cues**: 
  - Badge is small enough to not be distracting but visible enough to notice
  - Animation catches peripheral vision
  - Color-coded status (green=active, orange=loading, gray=idle)

**Step 3: Check Status at a Glance**
- **User Action**: User looks at the badge to see current status
- **System Response**: Badge displays current state information
- **UI Elements Visible**: 
  - Badge showing:
    - Number of jobs in progress (e.g., "2 in progress")
    - Number of jobs pending (e.g., "3 pending")
    - Engine status (if engines are loading)
  - Status dot with pulsing animation (if active)
  - Color indicating overall state
- **Visual Cues**: 
  - Text is concise and readable at small size
  - Color immediately conveys status type
  - Animation speed may indicate urgency or activity level

**Step 4: Optional - Click Badge for Details**
- **User Action**: Click on the status badge to see more information
- **System Response**: Modal or popup appears with detailed job information
- **UI Elements Visible**: 
  - Expanded view showing:
    - Engine status cards (Blockify Engine, Embedding Engine)
    - Engine states: Loading, Loaded, Error, Pending
    - Each engine shows icon status (⏳ loading, ✅ loaded, ❌ error, ⏸️ pending)
    - List of active jobs with:
      - Job name
      - Progress bar per job
      - Completion percentage
      - File counts (e.g., "5 of 10 files complete")
    - "View All Jobs" button at bottom
  - Close button (X) to dismiss modal
- **Visual Cues**: 
  - Modal overlays current page
  - Background may be dimmed
  - Color coding for engine states
  - Progress bars show visual progress

**Step 5: Optional - Navigate to Job Details**
- **User Action**: Click on a specific job in the detailed view to go to its details page
- **System Response**: 
  - Modal closes
  - User navigates to Job Details page for selected job
- **UI Elements Visible**: 
  - Full job details dashboard (see view-job-details.md)
  - Comprehensive job information and analytics
- **Visual Cues**: Page transition animation

**Step 6: Optional - Close Details Modal**
- **User Action**: Click "X" or click outside modal to close the detailed view
- **System Response**: Modal closes, returns to previous view
- **UI Elements Visible**: 
  - Badge returns to compact state in corner
  - Previous page content fully visible
- **Visual Cues**: Smooth modal dismissal animation

**Step 7: Monitor Progress Updates**
- **User Action**: Continue with other tasks, occasionally glancing at badge
- **System Response**: 
  - Badge text updates as jobs progress
  - Progress percentages change
  - Job counts update when jobs complete or are queued
- **UI Elements Visible**: 
  - Badge with updated status text
  - Text changes reflect real progress (e.g., "1 in progress, 2 pending" → "3 pending" as first job completes)
  - Percentage may be shown (e.g., "45% complete" if only one job)
- **Visual Cues**: 
  - Badge updates smoothly without jarring changes
  - Numbers increment/decrement as status changes

**Step 8: Job Completes**
- **User Action**: None required
- **System Response**: 
  - Job completion detected
  - Badge updates to reflect completion
  - If no more active jobs, badge may:
    - Show "Completed" status briefly
    - Fade out after a few seconds
    - Change to inactive state (gray)
- **UI Elements Visible**: 
  - Badge showing completion state
  - Text: "Completed" or similar
  - Possibly: Success checkmark icon
  - Pulsing animation stops
- **Visual Cues**: 
  - Color change (green → gray or disappears)
  - Animation stops
  - May show brief completion notification

**Step 9: Badge Disappears or Goes Idle**
- **User Action**: None
- **System Response**: 
  - After all jobs complete, badge either:
    - Fades out completely (if no jobs remain)
    - Shows "Loaded" or idle state (engines ready, no jobs)
  - Badge only reappears when new jobs start
- **UI Elements Visible**: 
  - No badge visible (or minimal idle badge)
  - Clean interface without status indicator
- **Visual Cues**: Smooth fade-out transition

**Final Step: Ongoing Monitoring Cycle**
- **Success Indicator**: 
  - User was able to monitor job progress without leaving current page
  - Badge provided accurate, timely status updates
  - User knows when jobs complete
  - No surprises or missed notifications
- **System State Change**: 
  - Job progresses from pending → active → processing → completed
  - Badge visibility and content tracks job lifecycle
  - User awareness maintained throughout process
- **Next Possible Actions**: 
  - Continue current task, knowing jobs are processing
  - Click badge to view detailed status at any time
  - Navigate to Job Details page for full analysis
  - Start additional jobs (badge will reflect all active jobs)
  - Use completed dataset in conversations

---

## Alternative Paths & Strategies

### Strategy A: Ignore Badge (Background Processing)
**When to use**: User trusts system to process jobs and doesn't need constant monitoring

**Steps**:
1. Start job as usual
2. Badge appears but user doesn't actively monitor it
3. User continues other work
4. Badge disappears when complete
5. User later checks results when convenient

### Strategy B: Active Monitoring with Frequent Clicks
**When to use**: User wants detailed, real-time progress updates

**Steps**:
1. Badge appears when job starts
2. User immediately clicks badge to view details
3. User keeps modal open to watch progress
4. Modal updates in real-time with progress bars
5. User clicks specific job to view full analytics
6. User returns to modal or badge to continue monitoring

### Strategy C: Multiple Jobs Monitoring
**When to use**: User has several jobs running simultaneously

**Steps**:
1. Badge shows "3 in progress, 2 pending"
2. User clicks badge to see all jobs listed
3. Each job shows individual progress
4. User can click any job to view its specific details
5. Can monitor which job is fastest or having issues
6. Badge updates as each job completes

### Strategy D: Check Only When Notified
**When to use**: User wants passive monitoring with attention only when needed

**Steps**:
1. Badge appears and pulses (minimal attention)
2. User checks badge only when animation changes or catches attention
3. Badge color change (green → red) indicates problem, drawing attention
4. User clicks to investigate only when necessary
5. Otherwise, lets jobs complete on their own

---

## Error States & Recovery

### Error 1: Badge Not Appearing for Active Job
**Cause**: Display issue or job not properly registered  
**User Experience**: 
- Job is processing but no badge appears
- User unaware of job status
- No visual feedback

**Recovery Steps**:
1. Navigate to Blockify page
2. Check "View Jobs" tab to verify job exists and is running
3. Refresh the page
4. Badge should appear if job is truly active
5. If badge still missing, job may have failed to start properly

**QA Note**: Badge visibility is automatic when jobs are active. This error indicates system issue that should be rare. Documented for completeness.

### Error 2: Badge Shows Incorrect Status
**Cause**: State synchronization issue  
**User Experience**: 
- Badge says "1 in progress" but job actually completed
- Numbers don't match actual job count
- Stale information displayed

**Recovery Steps**:
1. Refresh the page to resync state
2. Click badge to view detailed status
3. Navigate to Jobs list to see actual status
4. Badge should correct itself on refresh

**QA Note**: Real-time updates should prevent this. If occurs, indicates update mechanism failure.

### Error 3: Badge Doesn't Disappear After Completion
**Cause**: Completion event not detected properly  
**User Experience**: 
- Jobs complete but badge remains showing "in progress"
- Badge stuck in active state
- Pulsing animation continues

**Recovery Steps**:
1. Click badge to view detailed status
2. Check if jobs are actually complete in modal
3. Refresh page to reset badge state
4. Badge should disappear if no active jobs

### Error 4: Cannot Click Badge / No Response
**Cause**: UI interaction issue  
**User Experience**: 
- Badge visible but clicking doesn't open details
- No modal appears
- Badge appears non-interactive

**Recovery Steps**:
1. Try clicking again (may be timing issue)
2. Refresh page
3. Navigate manually to Jobs page (Blockify > View Jobs tab)
4. Check job status there

### Error 5: Badge Blocks Other UI Elements
**Cause**: Position overlap with other interface elements  
**User Experience**: 
- Badge covers important buttons or content
- Cannot click elements behind badge
- Badge in the way

**Recovery Steps**:
1. Click badge to view details (removes badge temporarily)
2. Close modal to work with page
3. Scroll page if badge blocks content (badge is fixed position)
4. Complete action, badge remains in corner

**QA Note**: Badge should be positioned to avoid critical UI elements. If occurs, design issue not user error.

---

## Pain Points & Friction

**Identified Issues**:

1. **Badge May Go Unnoticed**
   - **Impact**: Users may not realize jobs are running if not looking at bottom-right corner
   - **Frequency**: First-time users or when multitasking
   - **Potential Improvement**: 
     - Add audio notification when jobs start/complete (optional)
     - Make initial appearance more prominent (larger, then shrink)
     - Add notification to navigation area temporarily
     - Show progress in browser tab title

2. **Limited Information in Compact State**
   - **Impact**: Can only see count, not which specific jobs or detailed progress
   - **Frequency**: When multiple jobs running
   - **Potential Improvement**: 
     - Show job names on hover
     - Add tooltip with more details before clicking
     - Show most critical job status (e.g., longest running)

3. **No Distinction Between Job Types**
   - **Impact**: Can't tell if jobs are blockify, chunking, or other types without clicking
   - **Frequency**: Users running different job types
   - **Potential Improvement**: 
     - Add icon indicating job type
     - Color code by job type
     - Show job type in compact badge text

4. **Badge Position May Conflict with Other Elements**
   - **Impact**: Could overlap with chat input, other floating elements, or browser features
   - **Frequency**: On smaller screens or with certain browser extensions
   - **Potential Improvement**: 
     - Make badge position configurable
     - Auto-adjust position if conflicts detected
     - Allow dragging to reposition

5. **No History When Badge Disappears**
   - **Impact**: If user misses completion, no way to know from badge that job finished
   - **Frequency**: Users looking away when job completes
   - **Potential Improvement**: 
     - Keep badge visible longer after completion
     - Add "Recent Jobs" indicator
     - Show last completion time
     - Maintain notification in browser

6. **Animation May Be Distracting**
   - **Impact**: Pulsing animation draws attention when user trying to focus on other tasks
   - **Frequency**: Users sensitive to motion or during long jobs
   - **Potential Improvement**: 
     - Make animation subtler
     - Add option to reduce motion
     - Allow disabling animation
     - Use static indicators instead

---

## Design Considerations

**Following Contextual Design Principles**:

1. **Automation Opportunities**: 
   - Auto-notify when jobs complete (no need to check)
   - Auto-navigate to results when job done (optional)
   - Auto-hide badge when no jobs (reduces clutter)
   - Auto-prioritize display of most important job info

2. **Simplification Opportunities**: 
   - Show only most essential information in compact state
   - One-click to full details (no intermediate steps)
   - Clear, simple status text (avoid technical jargon)
   - Minimize user decision-making (automatic behavior)

3. **Transition Smoothness**: 
   - Badge appears/disappears smoothly
   - Modal opens/closes with smooth animation
   - Updates happen gradually, not jarring
   - Natural flow from badge → details → full page

4. **User Trust**: 
   - Badge always present when jobs active (reliable indicator)
   - Status updates are accurate and timely
   - Progress percentages reflect actual progress
   - Completion is clearly indicated

5. **Cognitive Load**: 
   - Passive monitoring requires minimal attention
   - Information density appropriate for badge size
   - Don't force user to remember to check status
   - Visual cues (color, animation) convey state without reading

---

## Related Flows

- [Create New Blockify Job](../05-blockify-processing/create-blockify-job.md) - Starts jobs that trigger badge
- [View Job Details Dashboard](./view-job-details.md) - Full details accessed from badge
- [View All Jobs in Table](./view-jobs-table.md) - Alternative job monitoring view
- [Monitor Job Progress in Real-Time](./monitor-job-progress.md) - Detailed monitoring flow
- [Cancel a Running Job](./cancel-running-job.md) - Actions available from badge modal

---

## Technical References

**Knowledge Base Sections**:
- src/components/jobs/job-status-indicator.js - Status badge component
- src/components/jobs/job-manager.js - Job processing coordinator
- src/reducers/jobs.js - Job state management
- src/reducers/embedding.js - Engine status tracking
- src/reducers/blockify.js - Blockify engine status

**Key Components**:
- Fixed-position status badge with click interaction
- Real-time job progress tracking
- Engine status monitoring
- Modal overlay with detailed status

---

## Version History

| Date | Version | Author | Changes |
|------|---------|--------|---------|
| 2025-10-04 | 1.1 | [Iternal Technologies](https://iternal.ai/airgapai) | Initial comprehensive documentation |

---

## Notes

**Important Considerations**:
- Badge only appears when jobs are actively processing or queued, not for completed historical jobs
- Badge updates automatically; no refresh or manual action required
- Multiple jobs are aggregated into a single badge (click to see individual job details)
- Badge persists across page navigation within the application
- Application must remain open for badge to display; closing application pauses jobs

**Badge States Explained**:
- **Green Pulsing**: One or more jobs actively processing
- **Orange**: Engines loading (preparing to process)
- **Gray/Idle**: Engines loaded but no active jobs
- **Not Visible**: No jobs running and engines not actively needed

**Best Practices**:
- Use badge for passive monitoring; don't stare at it constantly
- Click badge if you want detailed progress information
- If badge shows error state (red), click immediately to investigate
- Let jobs complete in background while you work on other tasks
- Only actively monitor if job is critical and time-sensitive

**Common User Questions**:
- "Why did the badge disappear?" - All jobs completed or were cancelled
- "Can I hide the badge?" - Not currently; it only shows when jobs are active
- "Does the badge slow down my computer?" - No, it's a lightweight display element
- "What if I miss the completion?" - Check the Jobs list page to see recently completed jobs
- "Can I interact with jobs from the badge?" - Yes, click to view details and access actions

