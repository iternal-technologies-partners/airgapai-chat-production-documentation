# Generate Chat Name with AI

## Overview
**Flow ID**: `edit-chat-name-ai`  
**Category**: Chat Interactions  
**Estimated Duration**: 30-60 seconds  
**User Role**: All Users  
**Complexity**: Simple  

**Purpose**: This flow enables users to automatically generate a descriptive chat name using AI by analyzing the conversation content. The AI reads recent messages and creates a concise, relevant title that captures the conversation's essence.

---

## Trigger

**What initiates this flow:**
- [x] User manually initiates


**Specific trigger**: User wants an AI-generated name instead of manually creating one, typically because:
- They want a quick, accurate name without thinking about it
- The conversation covers complex topics hard to summarize
- They prefer automated naming for consistency
- They want creative or well-phrased names

---

## Prerequisites

**Before starting, users must have:**
- [x] Active chat with at least 1-2 message exchanges
- [x] AI model loaded and ready
- [x] Chat open for editing

---

## User Intent Analysis

### Primary Intent
Automatically generate a descriptive, accurate name for the chat conversation using AI analysis of the conversation content.

### Secondary Intents
- Save time compared to manual naming
- Get creative or well-phrased names
- Ensure name accurately reflects content
- Maintain naming consistency

### Subintents
- Leverage AI capabilities for auxiliary tasks
- Reduce cognitive burden of naming
- Get instant results

---

## Step-by-Step Flow

### Main Path (Happy Path)

**Step 1: Access Edit Name Function**
- **User Action**: Click edit icon (pencil) next to chat name in header
- **System Response**: Name editing interface appears
- **UI Elements Visible**: 
  - Text input field with current name
  - Three control buttons:
    - **Magic wand icon** (generate name with AI)
    - Checkmark icon (save manually entered name)
    - X icon (cancel)
- **Visual Cues**: Inline editing mode active

**Step 2: Initiate AI Name Generation**
- **User Action**: Click magic wand icon button
- **System Response**: 
  - AI begins analyzing conversation
  - Button changes to loading state
  - Cancel option appears
- **UI Elements Visible**: 
  - Loading spinner replaces magic wand icon
  - Cancel button (X) to stop generation
  - Text field may be disabled/grayed during generation
  - Status text may appear: "Generating name..."
- **Visual Cues**: 
  - Animated loading spinner
  - Disabled state on text field

**Step 3: Wait for AI Generation**
- **User Action**: Wait briefly (typically 5-15 seconds)
- **System Response**: 
  - AI reviews recent messages (typically last 10-20 messages)
  - AI generates concise title (2-8 words typically)
  - AI streams or returns generated name
- **UI Elements Visible**: 
  - Loading indicator continues
  - Waiting state
- **Visual Cues**: 
  - Spinner animation indicates AI is working

**Step 4: Generated Name Appears**
- **User Action**: Review AI-generated name
- **System Response**: 
  - Generated name appears in text field
  - Name is automatically capitalized appropriately
  - Loading indicator disappears
  - Save and cancel buttons become active
- **UI Elements Visible**: 
  - Text field with generated name
  - Name is editable if user wants to modify
  - Save button (checkmark) ready to click
  - Magic wand button returns (can generate again)
- **Visual Cues**: 
  - Name appears smoothly
  - Text field active for editing

**Step 5: Review and Optionally Modify**
- **User Action**: Read generated name; either accept as-is or edit to refine
- **System Response**: If edited, text updates as typed
- **UI Elements Visible**: 
  - Editable name in text field
  - Can type to modify AI's suggestion
  - Save button remains ready
- **Visual Cues**: Text field responsive to editing

**Step 6: Save Generated Name**
- **User Action**: Click save button (checkmark icon) or press Enter
- **System Response**: 
  - Name saves
  - Edit mode closes
  - New name displays in header and sidebar
- **UI Elements Visible**: 
  - Chat header showing new AI-generated name
  - Edit icon reappears
  - Chat list sidebar shows updated name
- **Visual Cues**: Smooth transition to display mode

**Final Step: AI-Generated Name Saved**
- **Success Indicator**: 
  - New name visible throughout interface
  - Name persists after refresh
  - Chat easily identifiable in list
- **System State Change**: 
  - Chat name updated in database
  - Name indexed for searching
  - Visible across all views
- **Next Possible Actions**: 
  - Continue conversation
  - Generate new name if not satisfied
  - Manually edit name further
  - Export chat with descriptive name

---

## Alternative Paths & Strategies

### Strategy A: Generate Multiple Times for Best Option
**When to use**: Want to see different name options

**Steps**:
1. Click edit icon
2. Click magic wand to generate
3. Review generated name
4. Click magic wand again without saving
5. New name generates
6. Compare options
7. Save preferred version

### Strategy B: Generate Then Refine
**When to use**: AI name is good but needs tweaking

**Steps**:
1. Generate name with AI
2. Edit parts of generated name manually
3. Combine AI creativity with personal preference
4. Save refined version

### Strategy C: Cancel Generation Mid-Process
**When to use**: AI taking too long or user changes mind

**Steps**:
1. Click magic wand to start generation
2. While loading, click cancel button (X)
3. Generation stops
4. Field returns to original name
5. Can manually edit or close

---

## Error States & Recovery

### Error 1: AI Generation Fails
**Cause**: Model error or insufficient conversation content  
**User Experience**: 
- Error message: "Failed to generate name" or "Not enough conversation content"
- Name field remains at original value
- Can try again or edit manually

**Recovery Steps**:
1. Try generating again
2. If fails repeatedly, edit name manually
3. Ensure conversation has sufficient content (at least one exchange)
4. Check if AI model is working properly

### Error 2: Generation Timeout
**Cause**: AI takes too long (> 30 seconds)  
**User Experience**: 
- Loading indicator continues indefinitely
- May timeout with error message
- Name generation fails

**Recovery Steps**:
1. Cancel generation
2. Try again
3. If persists, use manual editing
4. Check system resources

### Error 3: Generated Name Inappropriate or Nonsensical
**Cause**: AI misunderstood conversation or hallucinated  
**User Experience**: 
- Name doesn't match conversation topic
- Name is confusing or irrelevant
- Name may be too generic or too specific

**Recovery Steps**:
1. Generate again for different result
2. Manually edit generated name
3. Or discard and write custom name
4. Save preferred version

**QA Note**: Not technical error - AI output quality issue. User has full control to override.

### Error 4: Name Too Long
**Cause**: AI generated name exceeds character limit  
**User Experience**: 
- Generated name may be truncated
- Warning about length

**Recovery Steps**:
1. Manually shorten generated name
2. Keep key words, remove filler
3. Save edited version

**QA Note**: AI should generate appropriately-sized names. If occurs, indicates prompt issue.

---

## Pain Points & Friction

**Identified Issues**:

1. **No Control Over Generation Style**
   - **Impact**: Can't specify desired name format or tone
   - **Frequency**: Users with specific naming preferences
   - **Potential Improvement**: 
     - Options: formal, casual, descriptive, concise
     - Length preferences
     - Style templates

2. **Must Have Conversation Content**
   - **Impact**: Can't generate name for empty or new chats
   - **Frequency**: Users trying to name before chatting
   - **Potential Improvement**: 
     - Disable feature until sufficient content
     - Clear message explaining requirement
     - Suggest creating content first

3. **No Name Suggestions (Multiple Options)**
   - **Impact**: Only get one name at a time
   - **Frequency**: When first generated name isn't ideal
   - **Potential Improvement**: 
     - Generate 3-5 options simultaneously
     - Let user choose from list
     - Vote or rate names

**QA Note**: Simple feature with predictable behavior. Few error conditions. Most issues are feature limitations not defects.

---

## Design Considerations

**Following Contextual Design Principles**:

1. **Automation Opportunities**: 
   - Auto-generate name after first exchange
   - Suggest when name is still default

2. **Simplification Opportunities**: 
   - One-click generation
   - Auto-accept if user doesn't object

3. **Transition Smoothness**: 
   - Inline generation
   - Quick process

4. **User Trust**: 
   - Can review before accepting
   - Can edit or regenerate
   - Always have manual override

5. **Cognitive Load**: 
   - Removes naming burden
   - Simple button click
   - Clear what will happen

---

## Related Flows

- [Edit Chat Name Manually](./edit-chat-name-manual.md) - Manual alternative
- [Create New Empty Chat](./new-chat-empty.md) - Chats that need naming
- [Conduct Multi-Turn Conversation](./multi-turn-conversation.md) - Provides content for name generation

---

## Technical References

**Knowledge Base Sections**:
- src/components/chat/chat-header.js - Name generation logic
- src/engines/llm.js - AI generation
- src/handlers/index.js - updateChat RPC

**Key Components**:
- Inline name editor with AI generation
- LLM integration for name creation

---

## Version History

| Date | Version | Author | Changes |
|------|---------|--------|---------|
| 2025-10-04 | 1.1 | [Iternal Technologies](https://iternal.ai/airgapai) | Initial comprehensive documentation |

---

## Notes

**How AI Generates Names**:
- Reviews recent conversation messages (typically last 10-20)
- Creates concise summary title (2-8 words)
- Attempts to capture main topic
- Uses moderate creativity (temperature ~0.7)

**Best Practices**:
- Wait until conversation has some content before generating
- Review generated name before saving
- Edit if name isn't quite right
- Regenerate if completely off-topic

**Common User Questions**:
- "How does AI know what to name it?" - Reads conversation content
- "Can I control what it generates?" - Can regenerate for new options or manually edit
- "Why did it generate a strange name?" - AI may misinterpret; simply edit or regenerate
- "How long does it take?" - Typically 5-15 seconds

