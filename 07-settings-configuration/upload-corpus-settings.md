# Upload Dataset from Settings Page

## Overview
**Flow ID**: `upload-corpus-settings`  
**Category**: Settings & Configuration  
**Estimated Duration**: 2-10 minutes  
**User Role**: All Users  
**Complexity**: Simple  

**Purpose**: Upload pre-processed dataset files directly from Settings page. Alternative access point to dataset upload for users managing datasets through settings interface rather than from job completion context.

---

## Trigger

**What initiates this flow:**
- [x] User manually initiates

**Specific trigger**: User wants to upload dataset through Settings interface.

---

## User Intent Analysis

### Primary Intent
Add new dataset to application through Settings page interface.

### Secondary Intents
- Manage datasets alongside other configuration
- Upload datasets independent of job workflow
- Access dataset management in expected location

---

## Step-by-Step Flow

### Main Path (Happy Path)

**Step 1: Navigate to Datasets in Settings**
- **User Action**: Settings > navigate to Datasets-related section
- **System Response**: Datasets management area displays
- **UI Elements Visible**: 
  - Datasets list or table
  - "Upload Dataset" button

**Step 2: Click Upload Dataset**
- **User Action**: Click "Upload Dataset" button
- **System Response**: Upload modal appears

**Step 3-8: Complete Upload**
- **User Action**: Follow standard dataset upload process (see corpus-upload.md)
- **System Response**: Dataset uploads and registers
- **Note**: Process identical to corpus-upload.md but accessed via Settings

**Final Step: Dataset Uploaded from Settings**
- **Success Indicator**: Dataset added to system
- **System State Change**: Dataset available
- **Next Actions**: 
  - Activate dataset
  - View dataset details
  - Use in conversations

---

## Alternative Paths & Strategies

**Note**: This flow is specifically for accessing dataset upload through Settings rather than through Blockify > Datasets or job completion context. The upload process itself is identical to corpus-upload.md.

---

## Error States & Recovery

**Note**: Error states identical to standard dataset upload flow (see corpus-upload.md).

---

## Design Considerations

**Following Contextual Design Principles**:

1. **Simplification Opportunities**: Single dataset upload interface accessible from multiple locations
2. **User Trust**: Consistent upload process regardless of access point

---

## Related Flows

- [Upload New Dataset](../04-dataset-management/corpus-upload.md) - Detailed upload process
- [Navigate Between Settings Tabs](./navigate-settings-tabs.md) - Access datasets section
- [View Dataset List](../04-dataset-management/view-dataset-list.md) - View uploaded datasets

---

## Technical References

**Knowledge Base Sections**:
- src/pages/settings.js - Settings page
- src/components/ui/upload-corpus-modal.js - Upload interface

---

## Version History

| Date | Version | Author | Changes |
|------|---------|--------|---------|
| 2025-10-04 | 1.1 | [Iternal Technologies](https://iternal.ai/airgapai) | Initial documentation |

---

## Notes

**Important Considerations**:
- Same upload process as corpus-upload.md
- Settings provides alternative access point
- Helpful for users who expect dataset management in Settings
- Process and requirements identical to main dataset upload flow

**Best Practices**:
- Use whichever access point is most convenient
- Settings upload when managing configuration
- Blockify page upload when creating from jobs

**Common User Questions**:
- "Is this different from uploading in Datasets page?" - No, same process
- "Where should I upload datasets?" - Either Settings or Datasets page works
- "Does location matter?" - No, results are identical

