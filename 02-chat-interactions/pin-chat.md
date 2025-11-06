# Pin/Unpin Chat to Favorites

## Overview
**Flow ID**: `pin-chat`  
**Category**: Chat Interactions  
**Estimated Duration**: 10 seconds  
**User Role**: All Users  
**Complexity**: Simple  

**Purpose**: This flow allows users to "pin" important or frequently-used chat conversations to keep them easily accessible at the top of their chat list. Pinned chats appear in a dedicated "Pinned" section, separate from date-organized chats, making them quick to find regardless of when they were last used.

---

## Trigger

**What initiates this flow:**
- [x] User manually initiates


**Specific trigger**: User wants to mark a chat as important for quick access, typically because:
- They return to this conversation frequently
- The chat contains important ongoing work
- They want to keep track of a specific conversation
- They have many chats and need to prioritize certain ones

---

## Prerequisites

**Before starting, users must have:**
- [x] Application installed and running
- [x] At least one chat conversation created
- [x] Chat list sidebar visible (on Chat page)

---

## User Intent Analysis

### Primary Intent
Mark a chat conversation as favorite/important so it remains easily accessible at the top of the chat list, regardless of when it was last used.

### Secondary Intents
- Organize conversations by importance
- Reduce time searching for frequently-used chats
- Keep ongoing work conversations visible
- Separate priority conversations from casual ones

### Subintents
- Quickly access important conversations
- Maintain awareness of active projects
- Reduce cognitive load of finding conversations

---

## Step-by-Step Flow

### Main Path - Pin a Chat (Happy Path)

**Step 1: Navigate to Chat Page**
- **User Action**: Click "Chat" in navigation menu
- **System Response**: Chat page loads with conversation list sidebar
- **UI Elements Visible**: 
  - Chat list sidebar on left
  - Conversations organized by date sections (Today, This Week, etc.)
  - Each chat showing name and last update time
- **Visual Cues**: Chat page active in navigation

**Step 2: Locate Chat to Pin**
- **User Action**: Find the chat you want to pin in the chat list
- **System Response**: Chat may be in any date section
- **UI Elements Visible**: 
  - Chat entry with name
  - Star icon (outline/empty) next to chat name
  - Hover state may appear when mouse over chat
- **Visual Cues**: Empty star icon indicates chat is not pinned

**Step 3: Click Star Icon**
- **User Action**: Click the star icon next to the chat name
- **System Response**: 
  - Star icon fills (becomes solid)
  - Chat immediately moves to "Pinned" section at top of list
  - If no "Pinned" section existed, it's created
- **UI Elements Visible**: 
  - Filled/solid star icon
  - Chat now appears in "Pinned" section at top
  - Chat no longer in its original date section
  - "Pinned" section header visible
- **Visual Cues**: 
  - Star icon changes from outline to filled (color may be gold/yellow)
  - Smooth animation as chat moves to pinned section
  - Visual separation between pinned and regular sections

**Final Step - Chat Pinned**
- **Success Indicator**: 
  - Chat appears in "Pinned" section at top of list
  - Star icon is filled/solid
  - Chat is easily accessible
- **System State Change**: 
  - Chat marked as pinned in database
  - Chat list reorganized with pinned section
  - Setting persists across sessions
- **Next Possible Actions**: 
  - Pin additional chats
  - Unpin chats when no longer needed
  - Access pinned chat quickly from top of list

---

## Alternative Path - Unpin a Chat

**Step 1: Locate Pinned Chat**
- **User Action**: Find the pinned chat in the "Pinned" section at top of chat list
- **System Response**: Pinned chats visible in dedicated section
- **UI Elements Visible**: 
  - "Pinned" section header
  - Pinned chat(s) with filled star icons
- **Visual Cues**: Filled stars indicate pinned status

**Step 2: Click Star Icon to Unpin**
- **User Action**: Click the filled star icon next to the pinned chat
- **System Response**: 
  - Star icon becomes outline/empty
  - Chat immediately moves out of Pinned section
  - Chat returns to appropriate date section (Today, This Week, etc.)
  - If this was the last pinned chat, "Pinned" section disappears
- **UI Elements Visible**: 
  - Empty star icon
  - Chat in normal date-organized position
  - No longer in Pinned section
- **Visual Cues**: 
  - Star changes from filled to outline
  - Smooth animation as chat moves
  - Pinned section removed if empty

**Final Step - Chat Unpinned**
- **Success Indicator**: 
  - Chat no longer in Pinned section
  - Star icon is outline/empty
  - Chat appears in chronological position
- **System State Change**: 
  - Chat no longer marked as pinned
  - Chat list reorganized
  - Setting persists

---

## Error States & Recovery

### Error 1: Star Icon Not Responding
**Cause**: UI interaction issue or click missed the icon  
**User Experience**: 
- Click doesn't register
- No change to pin status
- Star doesn't fill

**Recovery Steps**:
1. Try clicking star icon again
2. Ensure clicking directly on star, not chat name
3. Refresh page if issue persists
4. Pin status should toggle on successful click

**QA Note**: This error indicates a system issue. Pin/unpin is a simple toggle with no validation that should fail. If occurs, likely UI bug not user error.

### Error 2: Chat Doesn't Move After Pinning
**Cause**: Display sync issue  
**User Experience**: 
- Star fills but chat stays in original position
- Pinned section doesn't appear

**Recovery Steps**:
1. Refresh the page
2. Chat should appear in pinned section after refresh
3. Star should show correct state
4. Data is saved even if display didn't update immediately

**QA Note**: Rare display issue, not data issue. Refresh resolves.

---

## Pain Points & Friction

**Identified Issues**:

1. **Star Icon May Be Small/Hard to Click**
   - **Impact**: Users may accidentally click chat name instead of star
   - **Frequency**: On devices with small screens or touch input
   - **Potential Improvement**: 
     - Larger click/touch target
     - Make entire star area clickable
     - Add right-click menu option to pin/unpin

2. **No Indication of What Pinning Does**
   - **Impact**: First-time users may not understand purpose of star icon
   - **Frequency**: New users discovering feature
   - **Potential Improvement**: 
     - Tooltip on hover: "Pin to favorites"
     - Brief explanation in onboarding
     - Help icon near pinned section

3. **No Limit Indication**
   - **Impact**: Users don't know if there's a limit to pinned chats
   - **Frequency**: Users wanting to pin many chats
   - **Potential Improvement**: 
     - Display count: "Pinned (3/10)" if limit exists
     - Warn when approaching limit
     - Or clearly communicate no limit

**QA Note on Compliance**: Most error states and pain points for this simple feature are minor or theoretical. The feature is straightforward with minimal error potential. Non-compliance with full checklist justified by feature simplicity.

---

## Design Considerations

**Following Contextual Design Principles**:

1. **Automation Opportunities**: 
   - Auto-pin chats user accesses frequently
   - Suggest pinning based on usage patterns
   - Auto-unpin chats not accessed in long time

2. **Simplification Opportunities**: 
   - One-click toggle (no confirmation needed)
   - Immediate visual feedback
   - No configuration required

3. **Transition Smoothness**: 
   - Smooth animation when chat moves
   - No jarring jumps in list
   - Instant response to click

4. **User Trust**: 
   - Clear visual indication of pinned state
   - Predictable behavior
   - Reversible action (can unpin anytime)

5. **Cognitive Load**: 
   - Simple star metaphor (familiar from other apps)
   - No decisions required
   - Visual distinction between pinned and unpinned

---

## Related Flows

- [Create New Empty Chat](./new-chat-empty.md) - Create chats to organize and pin
- [Conduct Multi-Turn Conversation](./multi-turn-conversation.md) - Build conversations worth pinning
- [Edit Chat Name Manually](./edit-chat-name-manual.md) - Name chats for easy identification when pinned

---

## Technical References

**Knowledge Base Sections**:
- src/components/chat/chat-nav.js - Chat navigation sidebar
- src/handlers/index.js - updateChat RPC for saving pin status
- src/localdb/base.js - Chat data persistence

**Key Components**:
- Star icon toggle
- Chat list with section organization
- Pin status persistence

---

## Version History

| Date | Version | Author | Changes |
|------|---------|--------|---------|
| 2025-10-04 | 1.1 | [Iternal Technologies](https://iternal.ai/airgapai) | Initial comprehensive documentation |

---

## Notes

**Important Considerations**:
- Pinned status persists across application restarts
- Multiple chats can be pinned simultaneously
- Pinned chats maintain their conversation history and settings
- Pinning does not affect the chat itself, only its position in the list

**Best Practices**:
- Pin only most frequently-used chats (3-5 recommended)
- Regularly unpin chats when no longer actively needed
- Use descriptive chat names for pinned chats for easier identification
- Review pinned chats periodically to keep list manageable

**Common User Questions**:
- "How many chats can I pin?" - No specific limit, but keep it manageable for usability
- "Does pinning affect the chat?" - No, only changes list position for easier access
- "Can I see pinned chats on other devices?" - Only if using same database/profile
- "What happens if I delete a pinned chat?" - It's deleted normally; pin status is removed with it

