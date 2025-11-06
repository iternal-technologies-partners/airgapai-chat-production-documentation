# Resume Incomplete Benchmark

## Overview
**Flow ID**: `resume-partial-benchmark`  
**Category**: Performance Benchmarking  
**Estimated Duration**: 1 minute (to resume)  
**User Role**: All Users  
**Complexity**: Simple  

**Purpose**: Continue previously stopped or interrupted benchmark from where it left off instead of starting over. System automatically skips completed tests and runs only remaining tests.

---

## Trigger

**What initiates this flow:**
- [x] User manually initiates

**Specific trigger**: User has partial benchmark results and wants to complete remaining tests.

---

## User Intent Analysis

### Primary Intent
Complete benchmark testing without re-running already completed tests, saving time and resources.

### Secondary Intents
- Maximize use of partial progress
- Avoid duplicating completed work
- Get complete results efficiently

---

## Step-by-Step Flow

### Main Path (Happy Path)

**Step 1: Navigate to Benchmarking**
- **User Action**: Settings > Benchmarking tab
- **System Response**: Benchmark page loads with partial results
- **UI Elements Visible**: 
  - Results tables showing:
    - Some tests: "Completed" (green)
    - Some tests: "Cancelled" (gray) or "Not Started"
  - "Continue Benchmark" or "Resume" button visible
  - "Reset Benchmark" button also available

**Step 2: Review Partial State**
- **User Action**: Note which tests completed and which remain
- **System Response**: Status clearly indicated
- **UI Elements Visible**: 
  - Mix of completed and incomplete tests
  - Progress percentage showing partial completion (e.g., "45% complete")

**Step 3: Click Continue/Resume**
- **User Action**: Click "Continue Benchmark" or "Resume" button
- **System Response**: 
  - Benchmark resumes
  - Skips completed tests
  - Starts first incomplete test
  - Button changes to "Stop Benchmark"
- **UI Elements Visible**: 
  - Status: "Running"
  - Next incomplete test begins
  - Completed tests remain green

**Step 4: Monitor Resumed Tests**
- **User Action**: Watch as remaining tests complete
- **System Response**: 
  - Tests run sequentially
  - Results populate for incomplete tests
  - Progress advances toward 100%

**Step 5: Benchmark Completes**
- **User Action**: Wait for all tests to finish
- **System Response**: 
  - Final tests complete
  - Status: "Completed"
  - 100% progress achieved
- **UI Elements Visible**: 
  - All tests showing "Completed"
  - Complete results table
  - "Run Benchmark" button available

**Final Step: Benchmark Complete**
- **Success Indicator**: 
  - All tests completed
  - No more cancelled/pending tests
  - Full results available
- **System State Change**: 
  - Complete benchmark data saved
  - All tests have results
- **Next Possible Actions**: 
  - View full results
  - Export complete data
  - Use results for optimization

---

## Alternative Path - Reset Instead of Resume

**Step 1: Choose Reset**
- **User Action**: Instead of "Continue", click "Reset Benchmark"
- **System Response**: 
  - All results cleared
  - Tests reset to "Pending"
  - Fresh start

**Step 2: Run Fresh Benchmark**
- **User Action**: Click "Run Benchmark"
- **System Response**: All tests run from beginning

**When to Use Reset**:
- Significant time passed since partial run
- System configuration changed
- Want fresh comparison data
- Suspect partial results unreliable

---

## Error States & Recovery

**QA Note**: Resume is automatic skip logic with no special error handling needed beyond normal benchmark errors.

---

## Pain Points & Friction

**Identified Issues**:

1. **No Clear Indication of What Will Run**
   - **Impact**: Don't know which tests remain
   - **Potential Improvement**: Show "X tests remaining" before resuming

---

## Design Considerations

**Following Contextual Design Principles**:

1. **Automation Opportunities**: Auto-skip completed tests (already implemented)
2. **Simplification Opportunities**: Single "Continue" button
3. **User Trust**: Reliably skips completed, runs remaining

---

## Related Flows

- [Run Full Benchmark Suite](./run-full-benchmark.md) - Initial benchmark
- [Cancel Running Benchmark](./cancel-benchmark.md) - Creates partial results
- [View Benchmark Results](./view-benchmark-results.md) - Review after resuming

---

## Technical References

**Knowledge Base Sections**:
- src/benchmarking/start-benchmark.js - Resume logic with completion checking
- src/components/benchmarking/benchmark-results.js - Continue button

---

## Version History

| Date | Version | Author | Changes |
|------|---------|--------|---------|
| 2025-10-04 | 1.1 | [Iternal Technologies](https://iternal.ai/airgapai) | Initial comprehensive documentation |

---

## Notes

**How Resume Works**:
- System checks status of each test
- Tests with "Completed" status are skipped
- Only runs tests that are "Pending", "Cancelled", or "Not Started"
- Saves time by not re-running completed tests

**Best Practices**:
- Resume if interrupted unintentionally
- Reset if want fresh data after system changes
- Review partial results before deciding to resume or reset

**Common User Questions**:
- "Will resume re-run completed tests?" - No, only runs incomplete tests
- "Can I select which tests to resume?" - No, automatically runs all incomplete
- "Should I reset or resume?" - Resume if just stopped; reset if conditions changed
- "How long will resume take?" - Depends on how many tests remain

