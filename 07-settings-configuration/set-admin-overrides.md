# Set Admin Performance Overrides

## Overview
**Flow ID**: `set-admin-overrides`  
**Category**: Settings & Configuration  
**Estimated Duration**: 1-2 minutes  
**User Role**: Power Users / Administrators  
**Complexity**: Simple  

**Purpose**: Configure advanced system-wide performance settings including CPU worker count for parallel processing and default chat template. These settings affect all users and all operations.

---

## Trigger

**What initiates this flow:**
- [x] User manually initiates

**Specific trigger**: Administrator wants to optimize system performance or set organizational defaults.

---

## Prerequisites

**Before starting, users must have:**
- [x] Understanding of performance implications
- [x] Knowledge of system hardware (CPU cores)
- [x] Admin access or confidence to change system settings

---

## User Intent Analysis

### Primary Intent
Optimize system-wide performance by configuring worker counts and default templates.

### Secondary Intents
- Maximize hardware utilization
- Standardize workflows with default templates
- Fine-tune for specific use cases

---

## Step-by-Step Flow

### Main Path (Happy Path)

**Step 1: Navigate to Admin Overrides**
- **User Action**: Settings > Admin Overrides tab
- **System Response**: Admin settings page displays
- **UI Elements Visible**: 
  - "Admin Overrides" tab highlighted
  - Warning banner: "Admin settings affect all users and operations"
  - Performance section
  - Workflow section

**Step 2: Review Current Settings**
- **User Action**: Note current values
- **UI Elements Visible**: 
  - **Performance Section**:
    - "Additional CPU Workers" input field
    - Current value shown (e.g., "8")
    - Available cores display: "Available CPU Cores: 16"
  - **Workflow Section**:
    - "Default Chat Template" dropdown
    - Current selection shown

**Step 3: Adjust CPU Workers**
- **User Action**: Change number in CPU workers field
- **System Response**: 
  - Value updates
  - Validation ensures within range (1 to max cores)
- **UI Elements Visible**: 
  - Number input showing new value
  - Range hint: "1 to 16" or similar
- **Recommendation**: Set to number of available cores minus 2-4 for system overhead

**Step 4: Select Default Template (Optional)**
- **User Action**: Open default template dropdown and select template
- **System Response**: 
  - Template selected
  - This template will be used when creating new chats
- **UI Elements Visible**: 
  - Dropdown with template options:
    - "No Default Template"
    - Available templates listed

**Step 5: Save Changes**
- **User Action**: Click "Save" button (if not auto-save)
- **System Response**: 
  - Settings saved
  - Success notification
  - Changes take effect
- **UI Elements Visible**: 
  - Success message
  - Saved values confirmed

**Final Step: Admin Settings Configured**
- **Success Indicator**: 
  - Settings saved successfully
  - Take effect immediately for new operations
- **System State Change**: 
  - Worker count updated globally
  - Future embedding operations use new worker count
  - New chats use selected default template
- **Next Possible Actions**: 
  - Test performance with new settings
  - Run jobs to verify worker count optimization
  - Create chats to verify template behavior

---

## Error States & Recovery

### Error 1: Worker Count Too High
**Cause**: Set higher than available cores  
**User Experience**: 
- Warning or auto-constrains to maximum

**Recovery Steps**:
1. System prevents invalid values
2. Set to reasonable number (cores minus 2-4)

---

## Pain Points & Friction

**Identified Issues**:

1. **No Guidance on Optimal Worker Count**
   - **Impact**: Users don't know best value
   - **Potential Improvement**: Auto-optimize button, recommendations

2. **Changes Affect All Operations**
   - **Impact**: No per-user or per-job customization
   - **Potential Improvement**: Per-user profiles or job-specific overrides

---

## Design Considerations

**Following Contextual Design Principles**:

1. **Automation Opportunities**: Auto-detect optimal worker count
2. **User Trust**: Clear warning about system-wide impact
3. **Cognitive Load**: Simple number input

---

## Related Flows

- [Run Full Benchmark Suite](../08-benchmarking/run-full-benchmark.md) - Test worker configuration
- [Create New Blockify Job](../05-blockify-processing/create-blockify-job.md) - Uses worker settings

---

## Technical References

**Knowledge Base Sections**:
- src/components/admin-overrides-tab/index.js - Admin settings UI
- src/engines/bulk-engines/bulk-embedding.js - Worker management

---

## Version History

| Date | Version | Author | Changes |
|------|---------|--------|---------|
| 2025-10-04 | 1.1 | [Iternal Technologies](https://iternal.ai/airgapai) | Initial documentation |

---

## Notes

**Worker Count Recommendations**:
- Conservative: cores - 4 (leaves room for system)
- Balanced: cores - 2
- Aggressive: cores - 1 (may impact responsiveness)

**Best Practices**:
- Test with benchmarks after changing
- Monitor system responsiveness
- Leave headroom for OS and other apps

**Common User Questions**:
- "How many workers should I use?" - Start with cores minus 2
- "Will more workers always be faster?" - Not always; diminishing returns and overhead
- "Can I change per job?" - No, system-wide setting

