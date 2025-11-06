# Navigate Through Dataset Pages

## Overview
**Flow ID**: `paginate-dataset`  
**Category**: Dataset/Corpus Management  
**Estimated Duration**: Ongoing  
**User Role**: All Users  
**Complexity**: Simple  

**Purpose**: Navigate through multiple pages of dataset items using pagination controls when dataset contains more items than can be displayed on one page.

---

## Trigger

**What initiates this flow:**
- [x] User manually initiates

**Specific trigger**: User viewing dataset with more items than page size (default 20 per page).

---

## User Intent Analysis

### Primary Intent
Browse through all dataset items efficiently when dataset is too large for single page.

### Secondary Intents
- Find items not on first page
- Review entire dataset systematically
- Understand dataset scope

---

## Step-by-Step Flow

**Step 1: View Pagination Controls**
- **User Action**: Scroll to bottom of items list
- **UI Elements Visible**: 
  - Page numbers (1, 2, 3, ...)
  - Previous/Next buttons
  - Page info: "Showing 1-20 of 1,247"
  - Items per page selector (10, 20, 50, 100)

**Step 2: Click Next or Page Number**
- **User Action**: Click "Next" button or specific page number
- **System Response**: 
  - Page changes
  - New items load
  - Info updates: "Showing 21-40 of 1,247"

**Step 3: Continue Browsing**
- **User Action**: Click through pages as needed
- **System Response**: Items update for each page

**Final Step: Browsed Multiple Pages**
- **Success Indicator**: Navigated through dataset successfully
- **Next Possible Actions**: Continue browsing, search instead

---

## Error States & Recovery

**QA Note**: Pagination is simple, reliable feature. Technical errors extremely rare.

---

## Pain Points & Friction

**Identified Issues**:

1. **Many Clicks for Large Datasets**
   - **Impact**: Tedious to browse 1000+ items
   - **Potential Improvement**: 
     - Jump to page number
     - Infinite scroll option
     - Larger page size options

---

## Design Considerations

1. **Simplification Opportunities**: Larger default page size
2. **User Trust**: Reliable page navigation
3. **Cognitive Load**: Standard pagination interface

---

## Related Flows

- [View Dataset Details](./view-dataset-details.md) - Parent context
- [Filter and Search Dataset Items](./filter-dataset-items.md) - Alternative to browsing all

---

## Version History

| Date | Version | Author | Changes |
|------|---------|--------|---------|
| 2025-10-04 | 1.1 | [Iternal Technologies](https://iternal.ai/airgapai) | Initial documentation |

---

## Notes

**Best Practices**:
- Use search instead of browsing for large datasets
- Increase items per page for faster browsing
- Use keyboard (Enter) to jump to page numbers if supported

**Common User Questions**:
- "How many items per page?" - Default 20, adjustable to 10/50/100
- "Can I see all at once?" - Not recommended for large datasets (performance)

