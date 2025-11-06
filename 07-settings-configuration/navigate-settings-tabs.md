# Navigate Between Settings Tabs

## Overview
**Flow ID**: `navigate-settings-tabs`  
**Category**: Settings & Configuration  
**Estimated Duration**: 10 seconds  
**User Role**: All Users  
**Complexity**: Simple  

**Purpose**: Move between different settings categories using tabbed interface to access various configuration areas including models, chat options, benchmarking, and admin overrides.

---

## Trigger

**What initiates this flow:**
- [x] User manually initiates

**Specific trigger**: User needs to access different settings category.

---

## User Intent Analysis

### Primary Intent
Access specific settings category quickly through tab navigation.

---

## Step-by-Step Flow

**Step 1: Open Settings Page**
- **User Action**: Click "Settings" in navigation
- **System Response**: Settings loads on default tab

**Step 2: View Available Tabs**
- **UI Elements Visible**: 
  - Tab bar across top:
    - Chat AI Models
    - Embedding Models
    - Chat Options
    - Benchmarking
    - Admin Overrides
  - Current tab highlighted

**Step 3: Click Different Tab**
- **User Action**: Click desired tab
- **System Response**: 
  - Content area updates
  - Selected tab highlights
  - Previous tab content hides

**Final Step**: Navigated to desired settings section
- **Next Actions**: Configure settings in that category

---

## Error States & Recovery

**QA Note**: Simple tab navigation with no error conditions. Standard UI pattern.

---

## Design Considerations

1. **Simplification Opportunities**: Clear tab labels
2. **User Trust**: Tabs work reliably

---

## Related Flows

All settings-related flows accessed via these tabs.

---

## Version History

| Date | Version | Author | Changes |
|------|---------|--------|---------|
| 2025-10-04 | 1.1 | [Iternal Technologies](https://iternal.ai/airgapai) | Initial documentation |

---

## Notes

**Tab Organization**:
- Chat AI Models: Upload and manage language models
- Embedding Models: Upload and manage embedding models (may be combined with Chat AI Models)
- Chat Options: Chat behavior, context window, temperature
- Benchmarking: Performance testing
- Admin Overrides: System-wide advanced settings

**Best Practices**:
- Familiarize yourself with tab locations
- Use keyboard if shortcuts available
- Most-used tabs typically: Chat Options, Chat AI Models

**Common User Questions**:
- "Where do I upload models?" - Chat AI Models or Embedding Models tabs
- "Where are chat settings?" - Chat Options tab
- "Where's benchmarking?" - Benchmarking tab

