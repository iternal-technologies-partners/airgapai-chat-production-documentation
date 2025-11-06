# Configure Context Window Size

## Overview
**Flow ID**: `configure-context-window`  
**Category**: Model Management  
**Estimated Duration**: 2-3 minutes  
**User Role**: All Users  
**Complexity**: Moderate  

**Purpose**: Adjust how much conversation history the AI model can process at once. Larger context windows allow AI to remember more messages but take longer to process. Finding optimal balance between memory and speed is key to good performance.

---

## Trigger

**What initiates this flow:**
- [x] User manually initiates

**Specific trigger**: User needs to adjust context limits, typically because:
- Responses too slow (want smaller context)
- AI forgetting too much (want larger context)
- Optimizing based on benchmark results
- Model supports larger/smaller than default

---

## Prerequisites

**Before starting, users must have:**
- [x] Application running
- [x] Chat model selected
- [x] Understanding that larger = slower but better memory

---

## User Intent Analysis

### Primary Intent
Set optimal context window size balancing conversation memory with response speed.

### Secondary Intents
- Optimize performance
- Maximize context if hardware allows
- Minimize latency if speed critical

---

## Step-by-Step Flow

### Main Path (Happy Path)

**Step 1: Navigate to Chat Options**
- **User Action**: Settings > Chat Options tab
- **System Response**: Chat options page displays
- **UI Elements Visible**: 
  - Model selection
  - **Context window size slider** (prominent)
  - Current value displayed (e.g., "4096 tokens")
  - Performance estimates (if benchmark data available)

**Step 2: Review Current Setting**
- **User Action**: Note current context window size
- **System Response**: Current value shown
- **UI Elements Visible**: 
  - Slider at current position
  - Value in tokens (e.g., "4096 tokens")
  - Character equivalent (e.g., "~16,000 characters")
  - Performance estimate: "Average prefill time: 2.3 seconds"

**Step 3: Adjust Context Slider**
- **User Action**: Move slider to desired size
- **System Response**: 
  - Value updates in real-time
  - Estimates recalculate
- **UI Elements Visible**: 
  - Slider moving
  - Value updating (snaps to supported sizes: 2048, 4096, 8192, etc.)
  - Estimated prefill time updates
  - Character equivalent updates

**Step 4: Review Performance Impact**
- **User Action**: Look at estimated prefill time
- **System Response**: Shows predicted impact
- **UI Elements Visible**: 
  - "Estimated prefill time: X seconds"
  - Based on benchmark data if available
  - Warning if very long time predicted

**Step 5: Save Changes**
- **User Action**: Click "Save" button
- **System Response**: 
  - Settings saved
  - Model begins reloading with new context size
  - Loading indicator appears
- **UI Elements Visible**: 
  - Loading overlay
  - "Loading model with new context window..."
  - Progress indicator
  - 30-90 second load time

**Step 6: Model Reloads**
- **User Action**: Wait for reload
- **System Response**: Model initializes with new context size
- **UI Elements Visible**: Loading progress
- **Visual Cues**: Progress animation

**Step 7: Loading Completes**
- **User Action**: No action required
- **System Response**: 
  - Model ready with new context
  - Returns to settings page
  - Success notification
- **UI Elements Visible**: Updated context size confirmed

**Final Step: Context Window Updated**
- **Success Indicator**: 
  - New size active
  - Model loaded successfully
  - Settings show updated value
- **System State Change**: 
  - Context window size updated globally
  - All new conversations use new size
  - Model reloaded with appropriate configuration
- **Next Possible Actions**: 
  - Test in new chat
  - Adjust further if needed
  - Run benchmark with new size

---

## Error States & Recovery

### Error 1: Size Not Supported by Model
**Cause**: Selected size exceeds model capabilities  
**User Experience**: 
- Warning or error message
- May revert to maximum supported

**Recovery Steps**:
1. Check model specifications
2. Select supported size
3. Use smaller model for larger contexts

### Error 2: Reload Fails
**Cause**: Insufficient memory for larger context  
**User Experience**: 
- Model fails to load
- Error message about memory

**Recovery Steps**:
1. Select smaller context size
2. Close other applications
3. Try again with more RAM available

---

## Pain Points & Friction

**Identified Issues**:

1. **Requires Model Reload**
   - **Impact**: 30-90 second wait when changing
   - **Potential Improvement**: Warm-swap contexts without full reload

2. **No Guidance on Optimal Size**
   - **Impact**: Users uncertain what to choose
   - **Potential Improvement**: 
     - Recommendations based on use case
     - Auto-optimize based on usage

3. **Performance Impact Not Clear Before Change**
   - **Impact**: Users may set too high and get slow responses
   - **Potential Improvement**: Visual warnings for extreme values

---

## Design Considerations

**Following Contextual Design Principles**:

1. **Automation Opportunities**: Auto-select based on hardware capabilities
2. **User Trust**: Clear performance predictions
3. **Cognitive Load**: Simplified explanations of technical setting

---

## Related Flows

- [Select Active Chat Model](./select-llm-model.md) - Model selection
- [Run Full Benchmark Suite](../08-benchmarking/run-full-benchmark.md) - Gather performance data
- [Configure Chat Behavior Settings](./configure-chat-settings.md) - Related settings

---

## Technical References

**Knowledge Base Sections**:
- src/components/chat-options-tab/index.js - Context window controls
- src/engines/llm.js - Context window implementation
- src/utils/context-window-size-calculator.js - Size calculations

---

## Version History

| Date | Version | Author | Changes |
|------|---------|--------|---------|
| 2025-10-04 | 1.1 | [Iternal Technologies](https://iternal.ai/airgapai) | Initial comprehensive documentation |

---

## Notes

**Context Window Explained**:
Amount of text (measured in tokens) the AI can process at once. Includes:
- Your current message
- Previous conversation messages
- System prompts and persona instructions
- Dataset query results (if enabled)

**Size Recommendations**:
- **2048-4096**: Fast responses, shorter conversations
- **8192**: Balanced for most uses
- **16384+**: Long conversations, slower but comprehensive memory

**Best Practices**:
- Start with 4096-8192 for general use
- Increase if AI forgets things too quickly
- Decrease if responses too slow
- Run benchmarks to understand performance at different sizes
- Monitor response times in actual use

**Common User Questions**:
- "What's the best size?" - Depends on hardware; 4096-8192 good starting point
- "Why does changing it reload the model?" - Context size built into model initialization
- "Can I use different sizes for different chats?" - No, global setting applies to all
- "What happens if I exceed context?" - Oldest messages drop out of AI's memory

