# Run Full Benchmark Suite

## Overview
**Flow ID**: `run-full-benchmark`  
**Category**: Performance Benchmarking  
**Estimated Duration**: 15-60 minutes (depends on models and hardware)  
**User Role**: All Users (though technical users benefit most)  
**Complexity**: Moderate  

**Purpose**: This flow enables users to run comprehensive performance tests on their AI models to understand how well they perform on their specific hardware. Benchmarking measures speed, throughput, latency, and resource usage across various test scenarios, helping users make informed decisions about model selection and configuration.

---

## Trigger

**What initiates this flow:**
- [x] User manually initiates


**Specific trigger**: User wants to test model performance, typically because:
- They just uploaded a new model and want to know how it performs
- They want to compare different models to choose the best one
- They're experiencing performance issues and want diagnostic data
- They want to optimize settings (context window, memory allocation)
- They're documenting system capabilities for deployment planning

---

## Prerequisites

**Before starting, users must have:**
- [x] Application installed and running
- [x] At least one chat model uploaded
- [x] At least one embedding model uploaded (for full suite)
- [x] Optional: Dataset uploaded for embedding tests
- [x] Time to let tests run uninterrupted (15-60 minutes)
- [x] Application window should remain open and in focus (recommended)

---

## User Intent Analysis

### Primary Intent
Measure and document how well AI models perform on the current hardware to make informed decisions about model selection, configuration, and deployment.

### Secondary Intents
- Compare multiple models to identify the best one
- Identify performance bottlenecks
- Validate hardware capabilities before production use
- Generate performance reports for documentation
- Optimize settings based on measured data
- Troubleshoot slow performance issues

### Subintents
- Understand tokens per second (speed) for different scenarios
- Measure memory usage and resource consumption
- Test context window handling
- Validate stability under load
- Collect data for future reference

---

## Step-by-Step Flow

### Main Path

**Step 1: Navigate to Benchmarking Section**
- **User Action**: Click "Settings" in navigation, then click "Benchmarking" tab
- **System Response**: Benchmarking page loads
- **UI Elements Visible**: 
  - "Benchmarking" tab highlighted
  - Page divided into two main areas:
    - Left panel: System information and status
    - Right panel: Benchmark results tables
  - "Run Benchmark" button (prominent, likely blue)
  - System hardware information displayed
  - Any previous benchmark results shown in tables
- **Visual Cues**: 
  - Clean dashboard layout
  - Clear call-to-action button

**Step 2: Review System Information**
- **User Action**: Review system specs displayed in left panel
- **System Response**: Hardware information shown
- **UI Elements Visible**: 
  - System info card showing:
    - Operating System
    - CPU model and core count
    - RAM amount
    - GPU information (model, VRAM)
    - NPU availability (Yes/No)
  - Current date/time
  - Previous benchmark date (if any)
- **Visual Cues**: 
  - Clean card layout
  - Icons for each hardware component
  - Clear labels

**Step 3: Check Models Configured**
- **User Action**: Verify which models will be tested (shown in results table or header)
- **System Response**: Displays models that will be benchmarked
- **UI Elements Visible**: 
  - Model sections in results table:
    - Chat model section (e.g., "Llama-3-8B")
    - Embedding model section (e.g., "Jina Embeddings")
  - Each model has expandable test categories
  - Status indicators for each test (Pending, Completed, etc.)
- **Visual Cues**: 
  - Model names in section headers
  - Expandable arrows or indicators

**Step 4: Initiate Benchmark**
- **User Action**: Click "Run Benchmark" button
- **System Response**: 
  - Button changes to "Running..." or becomes disabled
  - Loading model phase begins
  - System info panel updates to show "Running" status
  - Progress information appears
  - Stop button becomes available
- **UI Elements Visible**: 
  - "Stop Benchmark" button replaces "Run Benchmark"
  - Status text: "Running Benchmark..."
  - Progress section showing:
    - Start time
    - Overall progress (X of Y tests completed)
    - Progress bar
  - Test status cells begin updating
- **Visual Cues**: 
  - Blue or animated indicators for active state
  - Progress bar begins filling
  - Status text updates

**Step 5: Model Loading Phase**
- **User Action**: Wait while model loads (30-90 seconds)
- **System Response**: 
  - Status shows "Loading model..."
  - Progress updates
- **UI Elements Visible**: 
  - Loading status text
  - May show percentage
  - Model being loaded shown
- **Visual Cues**: 
  - Animated loading indicators
  - Progress bar advances slightly

**Step 6: LLM Tests Execute**
- **User Action**: Watch as chat model tests run automatically
- **System Response**: 
  - Series of tests execute sequentially:
    1. Context Size tests (different sizes: 2048, 4096, 8192 tokens)
    2. Non-Streaming tests
    3. Chat History tests (multi-turn simulation)
    4. Memory Override tests (different VRAM allocations)
  - Each test updates table cell with results
  - Progress bar advances
  - Real-time metrics displayed
- **UI Elements Visible**: 
  - Results table with test categories expanded
  - Each test row showing:
    - Test name (e.g., "Context Size 4096, 25% tokens")
    - Status (changes from Pending → Loading → In Progress → Completed)
    - Load time (seconds)
    - First token time
    - Generation time
    - Input/output tokens
    - Tokens per second
    - CPU usage percentage
  - Tests complete with green "Completed" badges
  - Failed tests show red "Error" badges
  - Current test highlighted or animated
- **Visual Cues**: 
  - Color-coded status badges
  - Animated current test
  - Numbers populate in real-time
  - Progress percentage increases

**Step 7: Monitor LLM Test Progress**
- **User Action**: Observe tests completing; can work on other tasks in other applications
- **System Response**: Tests continue automatically
- **UI Elements Visible**: 
  - Tests completing one by one
  - Results populating table
  - Progress: "15 of 30 tests completed" or similar
  - Elapsed time counter
  - Overall progress bar (may be at 30-40% after LLM tests)
- **Visual Cues**: 
  - Smooth progression through tests
  - Rows change color as they complete
  - Progress bar incrementally advances

**Step 8: Embedding Tests Begin**
- **User Action**: Continue waiting/monitoring
- **System Response**: 
  - After LLM tests complete, embedding tests start
  - Embedding model loads
  - Embedding test categories execute:
    1. Single Embedding tests (various text sizes)
    2. Bulk Embedding tests (different batch sizes and worker counts)
  - Table updates with embedding results
- **UI Elements Visible**: 
  - Embedding model section becomes active
  - Test rows for embedding benchmarks
  - Results showing:
    - Test name (e.g., "500 characters, NPU")
    - Status
    - Load time
    - Embedding time
    - Workers used (NPU/CPU counts)
    - Embeddings per second
    - CPU load
  - Progress continues: "20 of 30 tests completed"
- **Visual Cues**: 
  - Focus shifts to embedding section
  - Similar visual updates as LLM tests
  - Progress bar advances further (60-80% range)

**Step 9: Monitor System Performance**
- **User Action**: Optionally watch system stats in left panel during tests
- **System Response**: Real-time system usage displayed
- **UI Elements Visible**: 
  - System panel showing current:
    - CPU usage (percentage)
    - Memory usage
    - GPU usage (if applicable)
    - Temperature (possibly)
  - May show real-time graphs or charts
  - Updates every few seconds
- **Visual Cues**: 
  - Live-updating numbers
  - Graphs or meters showing resource usage
  - Color coding for high usage (may turn red if excessive)

**Step 10: All Tests Complete**
- **User Action**: No action required
- **System Response**: 
  - Final test completes
  - Progress reaches 100%
  - Status changes to "Completed"
  - "Stop Benchmark" button becomes "Run Benchmark" again
  - Completion time and duration displayed
- **UI Elements Visible**: 
  - All test rows showing "Completed" status (or some may show "Error" if failed)
  - Full results table populated
  - Summary statistics:
    - Total tests: 30 (or actual count)
    - Completed: X
    - Failed: Y
    - Duration: "25 minutes 43 seconds"
  - Export button available
  - Reset button available
- **Visual Cues**: 
  - Green completion indicators
  - Progress bar at 100%
  - No more animations
  - Results table fully populated

**Step 11: Review Results**
- **User Action**: Scroll through results tables to examine performance data
- **System Response**: Results displayed with all metrics
- **UI Elements Visible**: 
  - Expandable test categories (click to expand/collapse)
  - Detailed metrics for each test
  - Color-coded performance indicators
  - Comparison data between tests
- **Visual Cues**: 
  - Data presented in organized table format
  - Numbers aligned for easy comparison
  - Categories clearly separated

**Step 12: Optional - Export Results**
- **User Action**: Click "Export Results" or "Download" button
- **System Response**: 
  - Results exported as TSV (tab-separated values) file
  - File downloads to computer
- **UI Elements Visible**: 
  - Export button
  - Download dialog or browser notification
- **Visual Cues**: Download progress indicator
- **Note**: See export-benchmark-data.md for detailed export flow

**Final Step: Benchmark Complete with Results**
- **Success Indicator**: 
  - All tests completed (or failed tests documented)
  - Full results table populated with data
  - Can export and reference results
  - Performance characteristics understood
- **System State Change**: 
  - Benchmark results saved in database
  - Performance data available for system optimization
  - Results used to estimate future processing times
  - Can compare with future benchmarks
- **Next Possible Actions**: 
  - Export results for documentation
  - Compare models based on benchmark data
  - Adjust settings based on findings (e.g., optimal context window size)
  - Re-run specific tests to verify results
  - Reset and run fresh benchmark with different models
  - Use benchmark data to configure chat settings optimally

---

## Alternative Paths & Strategies

### Strategy A: Continue Partial Benchmark
**When to use**: Benchmark was interrupted previously

**Steps**:
1. Navigate to Benchmarking tab
2. See incomplete test results with some tests marked "Cancelled" or not started
3. Click "Continue Benchmark" button (if available)
4. System resumes from where it stopped
5. Only incomplete tests re-run
6. Total time reduced compared to full re-run

### Strategy B: Quick Single-Test Benchmark
**When to use**: Just want to test one specific scenario

**Steps**:
1. Navigate to Benchmarking
2. Expand test category
3. Click "Re-test" on specific test row
4. Single test runs
5. Results update for just that test
6. Much faster than full suite (30 seconds - 2 minutes)

### Strategy C: Model-Specific Benchmark
**When to use**: Only care about one model (LLM or embedding), not both

**Steps**:
1. Start benchmark normally
2. When first model completes, click "Stop Benchmark"
3. Accept partial results
4. Complete results for first model
5. Second model tests remain as "Not Started"
6. Saves time if only testing one model

### Strategy D: Background Benchmark
**When to use**: Want to work on other tasks while benchmark runs

**Steps**:
1. Start benchmark
2. Navigate to other pages or minimize application
3. Benchmark continues in background
4. Periodically check progress via status badge or returning to benchmarking page
5. Return when complete to view results

**QA Note**: Background operation may be slower or less reliable. Keeping application in focus recommended.

---

## Error States & Recovery

### Error 1: Model Load Failure
**Cause**: Insufficient memory, corrupted model, or system error  
**User Experience**: 
- Error during model loading phase
- Message: "Failed to load model" or "Model error"
- Benchmark stops
- Test marked as "Error"

**Recovery Steps**:
1. Close other applications to free memory
2. Try running benchmark again
3. Try different model if specific model consistently fails
4. Check model file integrity
5. Restart application if needed

### Error 2: Individual Test Timeout
**Cause**: Test takes longer than maximum allowed time (4 minutes)  
**User Experience**: 
- Test running indicator for long time
- Eventually shows "Error" or "Timeout"
- Message: "Test exceeded maximum time"
- Benchmark continues to next test

**Recovery Steps**:
1. Note which test timed out
2. Allow benchmark to continue (other tests may succeed)
3. Test may be too demanding for hardware
4. Consider not using that context size or configuration
5. Can manually re-test later to verify

### Error 3: Benchmark Stops Unexpectedly
**Cause**: Application crash, system sleep, or user accidentally stopped it  
**User Experience**: 
- Progress stops mid-benchmark
- Some tests marked "Cancelled"
- Incomplete results

**Recovery Steps**:
1. Check application status (did it crash?)
2. Restart application if needed
3. Return to Benchmarking tab
4. Use "Continue Benchmark" to resume (if available)
5. Or reset and run full benchmark again

### Error 4: No Test Data File Available
**Cause**: Missing benchmark test data file used for consistent testing  
**User Experience**: 
- Error message at top of page: "Test data not loaded" or similar
- "Run Benchmark" button may be disabled
- Warning that benchmarks cannot run

**Recovery Steps**:
1. Check internet connection (if test data needs download)
2. Refresh page to retry loading test data
3. Verify application installation is complete
4. Reinstall application if file consistently missing
5. Contact support if issue persists

### Error 5: Out of Memory During Tests
**Cause**: System runs out of RAM during intensive testing  
**User Experience**: 
- Application becomes unresponsive
- May crash or freeze
- Benchmark stops with error
- Possible system warnings about low memory

**Recovery Steps**:
1. Close other applications before running benchmark
2. Restart application
3. Try benchmarking smaller model
4. Skip memory-intensive tests (large context sizes)
5. Upgrade system RAM if needed for desired models

---

## Pain Points & Friction

**Identified Issues**:

1. **Long Duration Without Clear Time Estimate**
   - **Impact**: Users don't know if benchmark will take 15 minutes or 2 hours
   - **Frequency**: Every benchmark run
   - **Potential Improvement**: 
     - Show estimated total time before starting
     - Display time remaining during execution
     - Warn about duration for large model/context combinations
     - Allow selecting subset of tests for faster results

2. **Cannot Pause Mid-Benchmark**
   - **Impact**: If user needs to use computer, must stop and lose progress
   - **Frequency**: Long benchmarks that need interruption
   - **Potential Improvement**: 
     - Add pause/resume functionality
     - Save progress to resume later
     - Allow partial completion with option to continue

3. **Results Table Overwhelming**
   - **Impact**: Many rows and columns of numbers can be confusing
   - **Frequency**: Viewing results, especially first time
   - **Potential Improvement**: 
     - Add summary view with key highlights
     - Visual indicators for good/bad performance
     - Comparison to typical values
     - Graphs/charts alongside tables

4. **Unclear What "Good" Results Look Like**
   - **Impact**: Users see numbers but don't know if performance is acceptable
   - **Frequency**: All users without technical background
   - **Potential Improvement**: 
     - Add benchmarks or baselines for comparison
     - Color code results (green=good, yellow=ok, red=poor)
     - Provide interpretation: "This is excellent/good/poor for this hardware"
     - Show comparisons to similar systems

5. **System Becomes Sluggish During Tests**
   - **Impact**: Difficult to use computer for other tasks while benchmark runs
   - **Frequency**: On lower-spec systems or with large models
   - **Potential Improvement**: 
     - Warn users before starting that system will be under load
     - Provide "low-impact" mode that runs slower but allows other work
     - Recommend running overnight or during breaks
     - Better resource throttling

6. **No Automatic Re-Test for Failed Tests**
   - **Impact**: Failed tests require manual retry
   - **Frequency**: When occasional failures occur
   - **Potential Improvement**: 
     - Auto-retry failed tests once
     - Option to "Retry Failed Tests" in batch
     - Identify and explain failure patterns

---

## Design Considerations

**Following Contextual Design Principles**:

1. **Automation Opportunities**: 
   - Auto-run lightweight benchmark when new model uploaded
   - Auto-retry failed tests once
   - Auto-export results when complete
   - Auto-recommend optimal settings based on results

2. **Simplification Opportunities**: 
   - Provide "Quick Benchmark" with essential tests only
   - Hide advanced test categories by default
   - Summary view before detailed results
   - One-click benchmark with smart defaults

3. **Transition Smoothness**: 
   - Clear progress indication throughout
   - Smooth test transitions
   - Results populate incrementally
   - Easy to stop and resume

4. **User Trust**: 
   - Accurate progress estimation
   - Reliable test execution
   - Verifiable results
   - Clear success/failure for each test

5. **Cognitive Load**: 
   - Don't require understanding technical metrics
   - Provide interpretations of results
   - Visual progress indicators
   - Clear start/stop controls

---

## Related Flows

- [View Benchmark Results](./view-benchmark-results.md) - Analyze completed benchmark data
- [Export Benchmark Results](./export-benchmark-data.md) - Save results to file
- [Cancel Running Benchmark](./cancel-benchmark.md) - Stop benchmark mid-run
- [Resume Incomplete Benchmark](./resume-partial-benchmark.md) - Continue interrupted benchmark
- [Upload Large Language Model](../03-model-management/llm-model-upload.md) - Add models to test
- [Upload Embedding Model](../03-model-management/embedding-model-upload.md) - Add embedding models
- [Configure Context Window Size](../03-model-management/configure-context-window.md) - Optimize based on benchmark

---

## Technical References

**Knowledge Base Sections**:
- src/components/benchmarking/index.js - Benchmark orchestrator
- src/components/benchmarking/benchmark-results.js - Results display
- src/benchmarking/start-benchmark.js - Test execution coordinator
- src/benchmarking/benchmark-llm.js - LLM test runner
- src/benchmarking/benchmark-embeddings.js - Embedding test runner
- src/components/benchmarking/system-stats-card.js - System info display

**Key Components**:
- Benchmark test orchestration system
- Real-time results tables
- Progress tracking
- System resource monitoring
- Multi-model testing capability

---

## Version History

| Date | Version | Author | Changes |
|------|---------|--------|---------|
| 2025-10-04 | 1.1 | [Iternal Technologies](https://iternal.ai/airgapai) | Initial comprehensive documentation |

---

## Notes

**Important Considerations**:
- Benchmark runs CPU and GPU at high utilization; computer may become hot or loud
- Results are saved and used by system for optimizing future performance
- First benchmark provides baseline; can re-run to track performance over time
- Different models will have vastly different results (expected)
- Tests are designed to stress different aspects of model performance
- Keep application in focus and avoid interruptions for best results

**Test Categories Explained**:

**LLM Tests**:
- **Context Size**: Tests handling different amounts of conversation history
- **Non-Streaming**: Tests batch processing mode (whole response at once)
- **Chat History**: Tests multi-turn conversation performance
- **VRAM Override**: Tests different memory allocations to find optimal

**Embedding Tests**:
- **Embedding Sizes**: Tests processing different text lengths
- **Bulk Embedding**: Tests parallel processing with multiple workers (NPU and CPU)

**Metrics Explained**:
- **Tokens per second**: How fast the model generates text (higher is better)
- **First token time**: Latency before response starts (lower is better)
- **Load time**: How long model takes to initialize (lower is better)
- **CPU load**: Processor usage during test (lower is better if adequate performance)
- **Embeddings per second**: Throughput for embedding generation (higher is better)

**Best Practices**:
- Run benchmarks when not using computer for other tasks
- Close other applications before benchmarking for accurate results
- Run benchmark after uploading new models to understand their performance
- Keep benchmark results for documentation and comparison
- Re-benchmark periodically to track performance changes
- Use results to guide context window, VRAM, and worker configuration

**Common User Questions**:
- "How long does benchmark take?" - Typically 15-45 minutes depending on models and hardware
- "Can I stop and resume?" - Yes, use "Continue Benchmark" after stopping
- "Do I need to benchmark every model?" - Recommended, but not required; helps optimize settings
- "What's a good tokens-per-second rate?" - Varies by hardware; 10-50 tokens/sec is typical for consumer hardware
- "Why did some tests fail?" - Tests may exceed hardware capabilities or timeout; this helps identify limits
- "Can I use the application while benchmarking?" - Technically yes, but will slow benchmark and may affect results

