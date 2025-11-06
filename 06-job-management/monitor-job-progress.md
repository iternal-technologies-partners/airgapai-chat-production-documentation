# Monitor Job Progress in Real-Time

## Overview
**Flow ID**: `monitor-job-progress`  
**Category**: Job Management  
**Estimated Duration**: Ongoing  
**User Role**: All Users  
**Complexity**: Simple  

**Purpose**: Observe real-time updates of job processing progress including completion percentage, current stage, processing rate, and estimated time remaining. Enables passive or active monitoring without manual refreshes.

---

## Trigger

**What initiates this flow:**
- [x] User manually initiates (opening job details)
- [x] System event (job is processing)

**Specific trigger**: User has active job and wants to monitor its progress.

---

## User Intent Analysis

### Primary Intent
Track job processing in real-time to know when it will complete and verify it's progressing normally.

### Secondary Intents
- Detect stalls or errors early
- Estimate completion time
- Understand processing rate
- Verify job is working

---

## Step-by-Step Flow

### Main Path (Happy Path)

**Step 1: Open Job Details**
- **User Action**: Navigate to job details page (from status badge, jobs list, or direct link)
- **System Response**: Job details dashboard loads
- **UI Elements Visible**: 
  - Full dashboard with real-time elements
  - Progress timeline
  - Metrics cards
  - Charts section

**Step 2: View Progress Timeline**
- **User Action**: Look at horizontal progress bar in timeline section
- **System Response**: Current progress displayed
- **UI Elements Visible**: 
  - Overall completion percentage (large): "67%"
  - Progress bar with four colored layers
  - Animated striped pattern on in-progress layer
  - Estimated time remaining: "14 minutes remaining"
  - Elapsed time: "28 minutes elapsed"
  - Current stage indicator

**Step 3: Observe Real-Time Updates**
- **User Action**: Watch without interaction
- **System Response**: 
  - Progress percentage increases incrementally
  - Metrics update every 2 seconds
  - Progress bar fills
  - Estimated time updates
- **UI Elements Visible**: 
  - Live-updating percentage
  - Metrics changing (e.g., "750 of 1000 chunks" → "751 of 1000")
  - Timer counting up
  - Processing rate updates

**Step 4: Monitor Metrics Cards**
- **User Action**: Periodically glance at metrics cards
- **System Response**: Real-time data displayed
- **UI Elements Visible**: 
  - Files Processed: "15 / 20 complete (75%)"
  - Blockification Progress: "750 / 1000 chunks, 12.5 chunks/min"
  - IdeaBlocks: "2,450 created, 1,200 embedded"
  - Processing Time: Live timer "28m 14s", rate "12.5/min"
- **Visual Cues**: 
  - Numbers update dynamically
  - Live timer counts up

**Step 5: Check Processing Rate**
- **User Action**: Note chunks per minute or processing rate
- **System Response**: Rate displayed and updates
- **UI Elements Visible**: 
  - Rate metric: "12.5 chunks/minute" or similar
  - Helps estimate if job is on track

**Step 6: Optional - Navigate Away**
- **User Action**: Navigate to other page while job processes
- **System Response**: 
  - Job continues in background
  - Status badge in corner shows ongoing progress
- **UI Elements Visible**: Status badge remains visible

**Step 7: Return to Check Progress**
- **User Action**: Return to job details to check progress
- **System Response**: Updated progress shown
- **UI Elements Visible**: 
  - Significantly advanced progress
  - Updated metrics reflecting time elapsed

**Final Step: Continuous Monitoring**
- **Success Indicator**: 
  - Can track progress reliably
  - Updates are timely and accurate
  - Know when job will complete
- **System State Change**: User has real-time awareness of job status
- **Next Actions**: 
  - Continue monitoring
  - Let job complete unattended
  - Navigate away and check back periodically

---

## Alternative Paths & Strategies

### Strategy A: Passive Monitoring via Status Badge
**When to use**: Don't need detailed progress, just completion awareness

**Steps**:
1. Start job
2. Navigate away from job details
3. Occasionally glance at status badge in corner
4. Badge shows job count and active state
5. When badge disappears, job complete

### Strategy B: Active Detailed Monitoring
**When to use**: Critical job or troubleshooting

**Steps**:
1. Keep job details page open
2. Watch all metrics continuously
3. Note any anomalies (sudden rate changes, stalls)
4. Check charts for patterns
5. Intervene if problems detected

---

## Error States & Recovery

### Error 1: Progress Stops Advancing
**Cause**: Job stalled or crashed  
**User Experience**: 
- Percentage stops changing
- Time remaining stops updating
- Rate drops to zero

**Recovery Steps**:
1. Wait 1-2 minutes (may be temporary pause)
2. Refresh page to verify state
3. Check status badge for error
4. If truly stalled, may need to cancel and retry

### Error 2: Updates Stop (Real-Time Sync Lost)
**Cause**: Update mechanism paused  
**User Experience**: 
- Metrics frozen at one value
- No live updates visible

**Recovery Steps**:
1. Refresh page manually
2. Progress should show current state
3. Updates may resume after refresh

---

## Pain Points & Friction

**Identified Issues**:

1. **No Alerts When Complete**
   - **Impact**: May not notice job finished
   - **Potential Improvement**: Desktop notification, audio alert

2. **Must Keep Page Open for Real-Time**
   - **Impact**: Closing details page loses real-time view
   - **Potential Improvement**: Updates work even when page closed, show on return

---

## Design Considerations

**Following Contextual Design Principles**:

1. **Automation Opportunities**: Auto-notify on completion
2. **User Trust**: Reliable real-time updates
3. **Cognitive Load**: Glanceable progress indicators

---

## Related Flows

- [View Job Details Dashboard](./view-job-details.md) - Full dashboard context
- [View Active Jobs Status Badge](./view-job-status-indicator.md) - Alternative monitoring
- [Cancel a Running Job](./cancel-running-job.md) - Action if problems detected

---

## Technical References

**Knowledge Base Sections**:
- src/components/jobs/blockify-job-processing-screen/index.js - Real-time updates
- src/components/ui/job-timer.js - Live timer
- src/components/jobs/blockify-job-processing-screen/ui/progress-timeline.js - Progress display

---

## Version History

| Date | Version | Author | Changes |
|------|---------|--------|---------|
| 2025-10-04 | 1.1 | [Iternal Technologies](https://iternal.ai/airgapai) | Initial documentation |

---

## Notes

**Real-Time Update Frequency**:
- Progress percentage: Updates every 2 seconds
- Metrics cards: Update when underlying data changes
- Timer: Updates every second
- Charts: Update as new data points available

**Best Practices**:
- Check progress periodically, not constantly
- Use status badge for passive monitoring
- Jump to details only when needed
- Trust automatic updates (no manual refresh needed)

**Common User Questions**:
- "Do I need to refresh?" - No, updates automatically
- "Why did updates stop?" - May need page refresh if connection lost
- "How accurate is estimated time?" - Improves as job progresses; early estimates less reliable

