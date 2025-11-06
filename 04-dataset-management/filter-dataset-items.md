# Filter and Search Dataset Items

## Overview
**Flow ID**: `filter-dataset-items`  
**Category**: Dataset/Corpus Management  
**Estimated Duration**: 1-2 minutes  
**User Role**: All Users  
**Complexity**: Simple  

**Purpose**: Search and filter dataset items to find specific information quickly. Search works across all text fields (block names, questions, answers) with real-time results.

---

## Trigger

**What initiates this flow:**
- [x] User manually initiates

**Specific trigger**: User needs to find specific items in dataset rather than browsing all items.

---

## Prerequisites

**Before starting, users must have:**
- [x] Dataset details page open
- [x] Dataset with items to search

---

## User Intent Analysis

### Primary Intent
Quickly locate specific information within large dataset by filtering items matching search criteria.

### Secondary Intents
- Verify dataset contains expected information
- Find specific topics or keywords
- Explore related items
- Assess coverage of specific subjects

---

## Step-by-Step Flow

### Main Path (Happy Path)

**Step 1: Locate Search Box**
- **User Action**: On dataset details page, find search/filter input box
- **System Response**: N/A
- **UI Elements Visible**: 
  - Filter input box (typically top-right of items area)
  - Placeholder text: "Search items..." or similar
  - Magnifying glass icon

**Step 2: Enter Search Term**
- **User Action**: Click in search box and type search term
- **System Response**: 
  - Text appears as typed
  - After brief delay (300ms), filtering begins
  - Results update automatically
- **UI Elements Visible**: 
  - Search box with typed term
  - Loading briefly
  - Results list updates
  - Result count updates: "Showing 1-20 of 45 results"

**Step 3: View Filtered Results**
- **User Action**: Review filtered items
- **System Response**: Only matching items displayed
- **UI Elements Visible**: 
  - Items containing search term
  - Search term may be highlighted in results
  - Pagination resets to page 1
  - Page count reflects filtered results
- **Visual Cues**: 
  - Instant filtering (300ms delay)
  - Match highlighting possible

**Step 4: Refine Search (Optional)**
- **User Action**: Modify search term to narrow or broaden results
- **System Response**: Results update with each change
- **UI Elements Visible**: Updated results matching new term

**Step 5: Clear Search**
- **User Action**: Click X button in search box or delete all text
- **System Response**: 
  - Filter clears
  - All items shown again
  - Pagination resets
- **UI Elements Visible**: Full dataset restored

**Final Step: Found Desired Items**
- **Success Indicator**: 
  - Relevant items displayed
  - Can browse filtered results
  - Search works reliably
- **System State Change**: 
  - View filtered to show matches
  - Can navigate and read filtered items
- **Next Possible Actions**: 
  - Read found items
  - Try different search terms
  - Clear search to view all
  - Page through results

---

## Alternative Paths & Strategies

### Strategy A: Multiple Keywords
**When to use**: Searching for combinations

**Steps**:
1. Type multiple words separated by spaces
2. System finds items containing all words
3. Results show items matching all terms

### Strategy B: Progressive Refinement
**When to use**: Too many results initially

**Steps**:
1. Start with general term
2. See large result count
3. Add more specific terms
4. Results narrow to most relevant

---

## Error States & Recovery

### Error 1: No Results Found
**Cause**: Search term doesn't match any items  
**User Experience**: 
- Empty results
- Message: "No items match search"

**Recovery Steps**:
1. Check spelling
2. Try different terms
3. Use more general keywords
4. Clear search to verify dataset has items

**QA Note**: Expected behavior, not error. Search working correctly.

### Error 2: Search Very Slow
**Cause**: Very large dataset  
**User Experience**: 
- Delay before results appear
- May take several seconds

**Recovery Steps**:
1. Wait for search to complete
2. Results will appear
3. Expected for 10,000+ item datasets

---

## Pain Points & Friction

**Identified Issues**:

1. **No Advanced Search Options**
   - **Impact**: Can only do simple text matching
   - **Potential Improvement**: Field-specific search, boolean operators

2. **Cannot Save Searches**
   - **Impact**: Must retype common searches
   - **Potential Improvement**: Search history, saved searches

---

## Design Considerations

**Following Contextual Design Principles**:

1. **Automation Opportunities**: Auto-suggest search terms
2. **Simplification Opportunities**: Simple text matching works well
3. **User Trust**: Instant, reliable results
4. **Cognitive Load**: Familiar search interface

---

## Related Flows

- [View Dataset Details](./view-dataset-details.md) - Parent flow
- [Navigate Through Dataset Pages](./paginate-dataset.md) - Browse results

---

## Technical References

**Knowledge Base Sections**:
- src/components/datasets/index.js - Filter implementation

---

## Version History

| Date | Version | Author | Changes |
|------|---------|--------|---------|
| 2025-10-04 | 1.1 | [Iternal Technologies](https://iternal.ai/airgapai) | Initial documentation |

---

## Notes

**Search Behavior**:
- Searches across: block names, critical questions, trusted answers, source text
- Case-insensitive
- Partial word matching
- Real-time with brief debounce (300ms)

**Best Practices**:
- Use specific terms for targeted results
- Try variations if first search doesn't find what expected
- Use multiple keywords for precision

**Common User Questions**:
- "Can I search multiple terms?" - Yes, space-separated finds items with all terms
- "Is search case-sensitive?" - No
- "Does it search all fields?" - Yes, across all item text content

