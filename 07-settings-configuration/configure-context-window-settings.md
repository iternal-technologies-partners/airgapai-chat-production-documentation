# Configure Context Window in Settings

## Overview
**Flow ID**: `configure-context-window-settings`  
**Category**: Settings & Configuration  
**Estimated Duration**: 2-3 minutes  
**User Role**: All Users  
**Complexity**: Moderate  

**Purpose**: Adjust context window size through Settings > Chat Options interface. This is the primary location for context window configuration, accessed through the Settings page tabbed interface rather than other possible access points.

---

## Trigger

**What initiates this flow:**
- [x] User manually initiates

**Specific trigger**: User navigates to Settings to adjust context window among other chat options.

---

## User Intent Analysis

### Primary Intent
Configure context window size from within Settings page as part of general chat configuration management.

---

## Process Reference

**Note**: This flow is identical to [Configure Context Window Size](../03-model-management/configure-context-window.md), which provides the complete detailed flow.

The distinction in the index is organizational:
- **configure-context-window** (03-model-management): Categorized as model management task
- **configure-context-window-settings** (07-settings-configuration): Same task accessed through Settings interface

Both refer to the same Settings > Chat Options > Context Window configuration process.

---

## Step-by-Step Flow

**See**: [Configure Context Window Size](../03-model-management/configure-context-window.md) for complete detailed flow including:
- Accessing Settings > Chat Options
- Adjusting context window slider
- Reviewing performance estimates
- Saving changes
- Model reload process
- Error handling
- Best practices

---

## Related Flows

- [Configure Context Window Size](../03-model-management/configure-context-window.md) - **Primary documentation** for this process
- [Configure Chat Behavior Settings](./configure-chat-settings.md) - Related settings in same interface
- [Navigate Between Settings Tabs](./navigate-settings-tabs.md) - Access Chat Options tab
- [Select Active Chat Model](../03-model-management/select-llm-model.md) - Model selection affects available context sizes

---

## Technical References

**Knowledge Base Sections**:
- src/components/chat-options-tab/index.js - Chat options interface including context window
- src/engines/llm.js - Context window implementation
- src/utils/context-window-size-calculator.js - Context size calculations

**Key Components**:
- Context window slider in Chat Options
- Performance estimation display
- Model reload handling

---

## Version History

| Date | Version | Author | Changes |
|------|---------|--------|---------|
| 2025-10-04 | 1.1 | [Iternal Technologies](https://iternal.ai/airgapai) | Initial documentation - references primary flow |

---

## Notes

**Organizational Note**:
This flow entry exists to maintain index completeness and organizational structure. The actual process is fully documented in configure-context-window.md (03-model-management category).

Both entries refer to the same Settings > Chat Options > Context Window configuration interface. The categorization difference reflects that context window can be viewed as:
- **Model Management** task: Configuring model-specific parameters
- **Settings Configuration** task: Adjusting chat behavior settings

**Access Path**:
Settings > Chat Options tab > Context Window Size slider

**For Complete Documentation**: See [Configure Context Window Size](../03-model-management/configure-context-window.md)

