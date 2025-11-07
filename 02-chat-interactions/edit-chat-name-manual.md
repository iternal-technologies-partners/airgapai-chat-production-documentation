# Edit Chat Name Manually

## Overview
**Flow ID**: `edit-chat-name-manual`  
**Category**: Chat Interactions  
**Estimated Duration**: 30 seconds  
**User Role**: All Users  
**Complexity**: Simple  

**Purpose**: This flow allows users to change the name of a chat conversation to something more descriptive and memorable. Custom names make it easier to find specific conversations later, especially when managing many chats.

---

## Trigger

**What initiates this flow:**
- [x] User manually initiates


**Specific trigger**: User wants to rename a chat, typically because:
- Default name is generic ("New Chat") and not descriptive
- Want to identify conversation by topic for future reference
- Need to organize chats with clear naming
- Original name no longer reflects conversation content

---

## Prerequisites

**Before starting, users must have:**
- [x] Active chat conversation open
- [x] Application running

---

## User Intent Analysis

### Primary Intent
Assign a descriptive, memorable name to a chat conversation for easier identification and organization.

### Secondary Intents
- Improve chat list organization
- Make specific chats easier to find
- Document conversation topics
- Differentiate between similar conversations

### Subintents
- Choose appropriate, descriptive name
- Save name for persistent reference

---

## Step-by-Step Flow

### Main Path

**Step 1: Access Edit Name Function**
- **User Action**: In chat header, click edit icon (pencil) next to chat name OR click chat name itself
- **System Response**: Name enters edit mode
- **UI Elements Visible**: 
  - Text input field appears in place of chat name
  - Current name shown in editable field
  - Control buttons appear:
    - Generate name button (magic wand icon)
    - Save button (checkmark icon)
    - Cancel button (X icon)
- **Visual Cues**: 
  - Text field replaces display name
  - Cursor appears in field
  - Buttons appear inline

**Step 2: Clear or Modify Existing Name**
- **User Action**: Select all text (Ctrl+A or triple-click) and type new name, OR edit portions of existing name
- **System Response**: Text updates as typed
- **UI Elements Visible**: 
  - Text input with new name
  - Character counter (if limit exists)
  - Save and cancel buttons remain visible
- **Visual Cues**: 
  - Active text field
  - Text selection highlighting

**Step 3: Enter New Name**
- **User Action**: Type descriptive name for the conversation
- **System Response**: Text appears as typed
- **UI Elements Visible**: 
  - Updated name in text field
  - Save button (checkmark) enabled
- **Visual Cues**: Real-time text update

**Step 4: Save New Name**
- **User Action**: Click save button (checkmark icon) OR press Enter
- **System Response**: 
  - Name is saved
  - Edit mode closes
  - New name displays in header
  - Name updates in chat list sidebar
- **UI Elements Visible**: 
  - Chat header showing new name (no longer editable)
  - Edit icon reappears next to name
  - Chat list sidebar shows updated name
- **Visual Cues**: 
  - Smooth transition from edit to display mode
  - Name change visible immediately

**Final Step: Name Updated**
- **Success Indicator**: 
  - New name visible in chat header
  - New name appears in chat list
  - Name persists after refresh
  - Can edit again if needed
- **System State Change**: 
  - Chat name updated in database
  - Name change persists across sessions
  - Searchable by new name
- **Next Possible Actions**: 
  - Continue conversation with new name
  - Edit name again if needed
  - Close chat and find it in list by new name

---

## Alternative Paths & Strategies

### Strategy A: Cancel Editing
**When to use**: User starts editing but decides not to change name

**Steps**:
1. Click edit icon, name field appears
2. Start typing or don't type anything
3. Click cancel button (X icon) OR press Escape
4. Edit mode closes, original name preserved
5. No changes saved

### Strategy B: Use AI to Generate Name
**When to use**: Want automatic name generation based on conversation content

**Steps**:
1. Click edit icon
2. Instead of typing manually, click magic wand icon
3. AI generates name based on conversation
4. Generated name appears in field
5. Accept or modify generated name
6. Save

**Note**: See edit-chat-name-ai.md for detailed AI name generation flow

---

## Error States & Recovery

### Error 1: Name Too Long
**Cause**: Entered name exceeds character limit  
**User Experience**: 
- Error message: "Name too long" or character limit indicator turns red
- Cannot save
- Field may prevent typing beyond limit

**Recovery Steps**:
1. Shorten name to fit within limit
2. Use abbreviations
3. Remove unnecessary words
4. Save once within limit

**QA Note**: Form should prevent typing beyond limit or truncate. Hard error unlikely.

### Error 2: Save Fails
**Cause**: Database error or connection issue  
**User Experience**: 
- Click save but name doesn't update
- Error message may appear
- Edit mode may stay open

**Recovery Steps**:
1. Try saving again
2. Cancel and retry editing
3. Copy new name (Ctrl+C)
4. Refresh page
5. Edit again and paste name

**QA Note**: Simple update operation. Failure indicates system issue, very rare.

### Error 3: Name Reverts After Save
**Cause**: Save didn't persist to database  
**User Experience**: 
- Name appears to save but reverts to old name after refresh
- Changes not persisted

**Recovery Steps**:
1. Try editing again
2. Refresh page first
3. Verify save completes
4. If persists, indicates data persistence issue

---

## Pain Points & Friction

**Identified Issues**:

1. **No Auto-Naming Based on Content**
   - **Impact**: Users must manually name each chat
   - **Frequency**: Every new chat
   - **Potential Improvement**: 
     - Auto-generate names from first exchange
     - Suggest names based on conversation
     - Template-based auto-naming

2. **Edit Mode Not Obvious**
   - **Impact**: Users may not discover they can edit name
   - **Frequency**: New users
   - **Potential Improvement**: 
     - Make edit icon more prominent
     - Tutorial or tooltip
     - Highlight feature during onboarding

**QA Note**: Very simple feature. Most error states theoretical. Feature works reliably with minimal error potential.

---

## Design Considerations

**Following Contextual Design Principles**:

1. **Automation Opportunities**: 
   - Auto-name based on first exchange
   - Suggest names from conversation topics

2. **Simplification Opportunities**: 
   - Inline editing (no modal)
   - Quick save (Enter key)

3. **Transition Smoothness**: 
   - Instant edit mode
   - Smooth save transition

4. **User Trust**: 
   - Changes persist reliably
   - Visible immediately everywhere

5. **Cognitive Load**: 
   - Simple edit/save flow
   - No complex options

---

## Related Flows

- [Generate Chat Name with AI](./edit-chat-name-ai.md) - Automatic name generation
- [Create New Empty Chat](./new-chat-empty.md) - Chats start with default names
- [Pin/Unpin Chat](./pin-chat.md) - Pinned chats benefit from clear names

---

## Technical References

**Knowledge Base Sections**:
- src/components/chat/chat-header.js - Name editing interface
- src/handlers/index.js - updateChat RPC
- src/localdb/base.js - Name persistence

**Key Components**:
- Inline text editing
- Auto-save on enter

---

## Version History

| Date | Version | Author | Changes |
|------|---------|--------|---------|
| 2025-10-04 | 1.1 | [Iternal Technologies](https://iternal.ai/airgapai) | Initial comprehensive documentation |

---

## Notes

**Best Practices**:
- Use descriptive names that indicate conversation topic
- Keep names concise (under 50 characters)
- Include project or category in name for organization
- Rename chats soon after creation while topic is fresh

**Common User Questions**:
- "Can I use emojis in names?" - Depends on system; generally yes
- "Is there a character limit?" - Yes, typically 100-200 characters
- "Does renaming affect conversation content?" - No, only the display name changes

