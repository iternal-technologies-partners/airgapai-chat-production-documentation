# View Dataset List

## Overview
**Flow ID**: `view-dataset-list`  
**Category**: Dataset/Corpus Management  
**Estimated Duration**: 1 minute  
**User Role**: All Users  
**Complexity**: Simple  

**Purpose**: View all uploaded datasets in list format with key information like name, status, size, and quick actions. Provides overview of available knowledge bases.

---

## Trigger

**What initiates this flow:**
- [x] User manually initiates

**Specific trigger**: User wants to see all available datasets, review what knowledge bases exist, or select dataset to view/manage.

---

## Prerequisites

**Before starting, users must have:**
- [x] Application running
- [x] Access to Datasets page or Settings

---

## User Intent Analysis

### Primary Intent
View all available datasets to understand what knowledge bases exist and their status.

### Secondary Intents
- Find specific dataset
- Check which dataset is active
- Access dataset management actions
- Understand dataset library scope

---

## Step-by-Step Flow

### Main Path

**Step 1: Navigate to Datasets**
- **User Action**: Click "Settings" then Datasets-related tab, OR "Datasets" in navigation
- **System Response**: Datasets list page loads
- **UI Elements Visible**: 
  - Page header: "Datasets" or "Knowledge Bases"
  - "Upload Dataset" or "Add Dataset" button
  - List/grid of datasets showing each with:
    - Dataset name (large, prominent)
    - Status badge (ACTIVE in green or INACTIVE in gray)
    - Embedding model name
    - Item count: "1,247 items"
    - File size: "125.5 MB"
    - Upload/creation date
    - Action buttons: Activate/Deactivate, View, Download, Delete

**Step 2: Review Dataset List**
- **User Action**: Scan through available datasets
- **System Response**: All datasets displayed
- **UI Elements Visible**: 
  - Multiple dataset cards or table rows
  - Each showing summary information
  - Active dataset clearly marked with green badge
  - Inactive datasets with gray badges

**Step 3: Identify Active Dataset**
- **User Action**: Look for green "ACTIVE" badge to see which dataset is currently selected
- **System Response**: Active dataset visually distinct
- **UI Elements Visible**: 
  - One dataset (or none) with ACTIVE status
  - All others showing INACTIVE

**Final Step: Datasets Reviewed**
- **Success Indicator**: 
  - Viewed all available datasets
  - Understand which is active
  - Know what's available
- **Next Possible Actions**: 
  - View details of specific dataset
  - Activate different dataset
  - Upload new dataset
  - Download or delete datasets

---

## Alternative Paths & Strategies

### Strategy A: Quick Active Dataset Check
**When to use**: Just need to know which dataset is active

**Steps**:
1. Open datasets list
2. Look for green ACTIVE badge
3. Note which dataset is active
4. Return to previous page

---

## Error States & Recovery

### Error 1: Empty List
**Cause**: No datasets uploaded yet  
**User Experience**: 
- Empty state message: "No datasets" or "Upload your first dataset"
- Prominent upload button

**Recovery Steps**:
1. This is normal for new users
2. Upload dataset to populate list

**QA Note**: Not error - expected for new users.

---

## Pain Points & Friction

**Identified Issues**:

1. **No Search or Filter**
   - **Impact**: Must scan visually for specific dataset
   - **Potential Improvement**: Search box for dataset names

2. **No Grouping or Organization**
   - **Impact**: All datasets in flat list
   - **Potential Improvement**: 
     - Group by category/topic
     - Sort options
     - Tags or labels

---

## Design Considerations

**Following Contextual Design Principles**:

1. **Simplification Opportunities**: Clear list with essential info
2. **User Trust**: Accurate status indicators

---

## Related Flows

- [View Dataset Details](./view-dataset-details.md) - Drill into specific dataset
- [Activate/Deactivate Dataset](./corpus-activation.md) - Change active status
- [Upload New Dataset](./corpus-upload.md) - Add to list

---

## Technical References

**Knowledge Base Sections**:
- src/pages/datasets.js - Datasets list page
- src/reducers/cruddb-reducer.js - Dataset list state

---

## Version History

| Date | Version | Author | Changes |
|------|---------|--------|---------|
| 2025-10-04 | 1.1 | [Iternal Technologies](https://iternal.ai/airgapai) | Initial documentation |

---

## Notes

**List Information**:
- Shows all uploaded/created datasets
- One marked ACTIVE (used for queries)
- Others INACTIVE (available but not used)
- Can activate any dataset instantly

**Best Practices**:
- Use descriptive dataset names
- Regularly review and clean up unused datasets
- Keep active dataset relevant to current work

**Common User Questions**:
- "Can multiple datasets be active?" - No, only one at a time
- "How many datasets can I have?" - Limited only by disk space
- "What if list is empty?" - Normal for new installations; upload first dataset

