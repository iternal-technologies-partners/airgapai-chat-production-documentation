# Set Default Chat Template

## Overview
**Flow ID**: `configure-default-template`  
**Category**: Settings & Configuration  
**Estimated Duration**: 1 minute  
**User Role**: All Users  
**Complexity**: Simple  

**Purpose**: Set a default template that automatically applies when creating new chats by typing without selecting a specific template. Streamlines workflow for users who consistently use same chat configuration.

---

## Trigger

**What initiates this flow:**
- [x] User manually initiates

**Specific trigger**: User wants all new chats to automatically use specific template settings.

---

## User Intent Analysis

### Primary Intent
Automate chat creation with preferred template to avoid selecting it manually each time.

### Secondary Intents
- Streamline repetitive workflows
- Ensure consistency across chats
- Save time on setup

---

## Step-by-Step Flow

### Main Path

**Step 1: Navigate to Admin Overrides**
- **User Action**: Settings > Admin Overrides tab
- **System Response**: Admin settings display

**Step 2: Locate Default Template Setting**
- **User Action**: Find "Default Chat Template" dropdown in Workflow section
- **UI Elements Visible**: 
  - "Default Chat Template" label
  - Dropdown showing current selection
  - Options list

**Step 3: Open Template Dropdown**
- **User Action**: Click dropdown
- **System Response**: Template list appears
- **UI Elements Visible**: 
  - "No Default Template" option
  - Available templates:
    - Social Media Post
    - Sales Proposal
    - Legal Review
    - Dataset Query Only
    - Others configured
  - Current selection highlighted

**Step 4: Select Default Template**
- **User Action**: Click desired template
- **System Response**: 
  - Selection updates
  - Dropdown closes
- **UI Elements Visible**: Selected template shown

**Step 5: Save**
- **User Action**: Click Save (if required)
- **System Response**: Setting saved
- **UI Elements Visible**: Success confirmation

**Final Step: Default Template Set**
- **Success Indicator**: 
  - Template selected as default
  - New chats without template selection will use this
- **System State Change**: Default template active
- **Next Actions**: 
  - Create new chat (will use default template automatically)
  - Can still select different template manually

---

## Alternative Path - Clear Default

**Step 1: Select "No Default Template"**
- **User Action**: Choose "No Default Template" from dropdown
- **System Response**: Default cleared
- **Final Step**: New chats will use empty configuration

---

## Error States & Recovery

**QA Note**: Simple dropdown with no error conditions beyond standard form handling.

---

## Pain Points & Friction

**Identified Issues**:

1. **Cannot Set Per-User Defaults**
   - **Impact**: System-wide setting affects all users
   - **Potential Improvement**: Per-user template preferences

---

## Design Considerations

**Following Contextual Design Principles**:

1. **Automation Opportunities**: Auto-apply based on usage patterns
2. **Simplification Opportunities**: One-click template setting
3. **User Trust**: Clear when default is applied

---

## Related Flows

- [Create New Chat from Template](../02-chat-interactions/new-chat-template.md) - Manual template selection
- [Create New Empty Chat](../02-chat-interactions/new-chat-empty.md) - Uses default if set

---

## Technical References

**Knowledge Base Sections**:
- src/components/admin-overrides-tab/index.js - Default template setting
- src/components/chat/new-chat.js - Default template application

---

## Version History

| Date | Version | Author | Changes |
|------|---------|--------|---------|
| 2025-10-04 | 1.1 | [Iternal Technologies](https://iternal.ai/airgapai) | Initial documentation |

---

## Notes

**How Default Works**:
- When user starts typing in new chat (without clicking template button), default template automatically applied
- User can still manually select different template
- Default makes frequent workflow faster

**Best Practices**:
- Set default to most-used template
- Clear default if workflows vary frequently
- Communicate to users if set organization-wide

**Common User Questions**:
- "Can I override default per chat?" - Yes, select different template manually
- "Does this affect existing chats?" - No, only new chats
- "Can I have different defaults per use case?" - No, single system default

