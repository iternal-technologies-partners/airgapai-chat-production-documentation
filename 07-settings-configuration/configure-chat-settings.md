# Configure Chat Behavior Settings

## Overview
**Flow ID**: `configure-chat-settings`  
**Category**: Settings & Configuration  
**Estimated Duration**: 3-5 minutes  
**User Role**: All Users  
**Complexity**: Moderate  

**Purpose**: Adjust global chat behavior settings that affect how the AI responds, including temperature (creativity), frequency penalty (repetition reduction), lookback size (conversation memory), and dataset query parameters.

---

## Trigger

**What initiates this flow:**
- [x] User manually initiates

**Specific trigger**: User wants to customize AI behavior, typically because:
- Default settings don't produce desired results
- Want more creative or more factual responses
- Need to adjust conversation memory
- Optimizing for specific use cases

---

## Prerequisites

**Before starting, users must have:**
- [x] Application running
- [x] Basic understanding of chat settings impact

---

## User Intent Analysis

### Primary Intent
Customize global AI behavior settings to achieve desired response characteristics across all new conversations.

### Secondary Intents
- Optimize response quality
- Control creativity vs. factuality
- Manage context window usage
- Configure dataset query behavior

---

## Step-by-Step Flow

### Main Path

**Step 1: Navigate to Settings**
- **User Action**: Click "Settings" in navigation
- **System Response**: Settings page loads

**Step 2: Access Chat Options Tab**
- **User Action**: Click "Chat Options" tab
- **System Response**: Chat configuration options display
- **UI Elements Visible**: 
  - Model selection (chat model, embedding model)
  - Context window size slider
  - Lookback size slider
  - Temperature slider (0-100)
  - Frequency penalty slider (-200 to 200)
  - Dataset query settings (number of results)
  - Save button (if not auto-save)

**Step 3: Adjust Temperature**
- **User Action**: Move temperature slider to desired value
- **System Response**: 
  - Slider moves
  - Current value displays
  - Description may update (e.g., "Higher values = more creative")
- **UI Elements Visible**: 
  - Temperature slider
  - Value display (e.g., "70")
  - Range: 0 (deterministic) to 100 (very creative)
  - Guidance text explaining effect
- **Visual Cues**: Slider position indicates current value

**Step 4: Adjust Frequency Penalty**
- **User Action**: Move frequency penalty slider
- **System Response**: Value updates
- **UI Elements Visible**: 
  - Slider (-200 to 200 range)
  - Current value
  - Explanation: "Reduces repetition in responses"
- **Visual Cues**: Slider with neutral (0) in middle

**Step 5: Set Lookback Size**
- **User Action**: Adjust lookback slider (conversation memory)
- **System Response**: Value changes
- **UI Elements Visible**: 
  - Slider (1-50 messages range)
  - Current value (e.g., "14 messages")
  - Explanation: "How many previous messages AI remembers"

**Step 6: Configure Dataset Query Settings**
- **User Action**: Adjust number of dataset results slider
- **System Response**: Value updates
- **UI Elements Visible**: 
  - Slider (1-10 results range)
  - Current value (e.g., "5 results")
  - Explanation: "Number of document passages to include"

**Step 7: Save Settings**
- **User Action**: Click "Save" if required (or auto-saves)
- **System Response**: 
  - Settings saved to database
  - Success notification may appear
  - Settings active immediately for new chats
- **UI Elements Visible**: 
  - Success message
  - Save button may show "Saved" state briefly

**Final Step: Settings Configured**
- **Success Indicator**: 
  - All settings at desired values
  - Settings persist after refresh
  - New chats use these settings
- **System State Change**: 
  - Global chat settings updated
  - Applies to all new conversations
  - Existing conversations unchanged (unless modified individually)
- **Next Possible Actions**: 
  - Test settings in new chat
  - Adjust further if needed
  - Configure per-chat settings for exceptions

---

## Alternative Paths & Strategies

### Strategy A: Reset to Defaults
**When to use**: Settings became problematic, want factory defaults

**Steps**:
1. Navigate to Chat Options
2. Click "Reset to Defaults" button (if available)
3. All settings revert to recommended values
4. Save if required

### Strategy B: Per-Chat Custom Settings
**When to use**: Want different settings for specific conversation

**Steps**:
1. Set global defaults in Settings
2. Open specific chat
3. Access advanced settings in chat
4. Override specific settings for this chat only
5. Chat uses custom settings; others use global

---

## Error States & Recovery

**QA Note**: Settings are constrained to valid ranges. Invalid values prevented by UI controls (sliders). Technical errors unlikely.

---

## Pain Points & Friction

**Identified Issues**:

1. **Settings Require Understanding AI Concepts**
   - **Impact**: Non-technical users uncertain what values to use
   - **Potential Improvement**: 
     - Presets: "Creative", "Balanced", "Precise"
     - Recommendations based on use case
     - Examples of setting effects

2. **No Preview of Settings Impact**
   - **Impact**: Must test in real conversation
   - **Potential Improvement**: 
     - Live preview with sample response
     - Show example outputs for different values
     - A/B comparison

3. **Global Settings Override Complex**
   - **Impact**: Per-chat overrides not obvious
   - **Potential Improvement**: 
     - Clearer hierarchy explanation
     - Visual indication when using custom

---

## Design Considerations

**Following Contextual Design Principles**:

1. **Automation Opportunities**: Recommend settings based on usage patterns
2. **Simplification Opportunities**: Preset configurations
3. **User Trust**: Clear explanations of each setting
4. **Cognitive Load**: Reduce technical terminology

---

## Related Flows

- [Configure Context Window Settings](./configure-context-window-settings.md) - Related setting
- [Entourage Mode Manage Chat Personas](../02-chat-interactions/persona-management.md) - Per-chat overrides
- [Create New Empty Chat](../02-chat-interactions/new-chat-empty.md) - Uses these settings

---

## Technical References

**Knowledge Base Sections**:
- src/components/chat-options-tab/index.js - Settings interface
- src/components/chat/chat-advanced-settings.js - Per-chat overrides
- src/localdb/settings.js - Settings persistence

---

## Version History

| Date | Version | Author | Changes |
|------|---------|--------|---------|
| 2025-10-04 | 1.1 | [Iternal Technologies](https://iternal.ai/airgapai) | Initial comprehensive documentation |

---

## Notes

**Settings Explained**:
- **Temperature**: 0 = predictable/factual, 100 = creative/varied
- **Frequency Penalty**: Negative values allow repetition, positive reduce it
- **Lookback Size**: How many recent messages AI considers (more = better context, slower)
- **Dataset Results**: More results = more context but slower processing

**Best Practices**:
- Start with defaults (temperature: 70, frequency penalty: 0, lookback: 14)
- Adjust one setting at a time to understand impact
- Use higher temperature for creative tasks, lower for factual
- Increase lookback for complex conversations needing lots of context
- Use 3-5 dataset results for balance of speed and coverage

**Common User Questions**:
- "What should I set temperature to?" - 50-70 for balanced, 80-100 for creative, 0-30 for factual
- "Why do settings have numbers instead of labels?" - Provides fine-grained control; presets would simplify
- "Do settings affect existing chats?" - No, only new chats unless overridden per-chat
- "What's safe to experiment with?" - All settings; can always reset to defaults

