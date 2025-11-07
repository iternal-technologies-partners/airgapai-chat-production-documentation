# View Job Performance Charts

## Overview
**Flow ID**: `view-job-charts`  
**Category**: Job Management  
**Estimated Duration**: 2-5 minutes  
**User Role**: All Users  
**Complexity**: Simple  

**Purpose**: Explore different visualization charts showing job processing performance including progress, speed, latency, and throughput. Charts help understand patterns, identify issues, and assess efficiency.

---

## Trigger

**What initiates this flow:**
- [x] User manually initiates

**Specific trigger**: User wants visual analysis of job performance through charts.

---

## User Intent Analysis

### Primary Intent
Visualize job performance data through various chart types to understand processing patterns and identify optimization opportunities.

### Secondary Intents
- Spot performance trends
- Identify bottlenecks
- Compare processing across chunks
- Document performance characteristics

---

## Step-by-Step Flow

### Main Path

**Step 1: Access Charts Section**
- **User Action**: On job details page, ensure "Charts" tab is selected (vs. "IdeaBlocks" tab)
- **System Response**: Charts view active
- **UI Elements Visible**: 
  - Charts/IdeaBlocks tab selector
  - "Charts" tab highlighted
  - Chart type selector buttons
  - Large chart display area

**Step 2: View Default Chart (Progress)**
- **User Action**: Observe default progress chart
- **System Response**: Multi-layer arc chart displays
- **UI Elements Visible**: 
  - Circular/arc progress chart showing:
    - Four colored layers (text, blockify, embeddings, total)
    - Percentage for each layer
    - Legend explaining colors
    - Interactive hover states
  - Tooltips on hover showing details

**Step 3: Select Different Chart Type**
- **User Action**: Click chart selector button (e.g., "Tokens Per Second")
- **System Response**: Chart switches to selected type
- **UI Elements Visible**: 
  - Chart selector with buttons:
    - Progress
    - Tokens Per Second
    - E2E Latency
    - Throughput
    - Items Per Chunk
  - Selected button highlighted (blue background)
  - New chart displays

**Step 4: Interpret Tokens Per Second Chart**
- **User Action**: Review line chart showing processing speed
- **System Response**: Chart displays time-series data
- **UI Elements Visible**: 
  - Line chart with:
    - X-axis: Chunk number or time
    - Y-axis: Tokens per second
    - Line showing speed variations
    - Hover tooltips with exact values
  - May show multiple lines (prefill speed, decode speed)

**Step 5: Switch to E2E Latency**
- **User Action**: Click "E2E Latency" button
- **System Response**: Chart changes to latency view
- **UI Elements Visible**: 
  - Chart showing processing time per chunk
  - Bars or line indicating time taken
  - Variations visible across chunks

**Step 6: Explore Other Charts**
- **User Action**: Browse through remaining chart types
- **System Response**: Each chart provides different insight
- **Available Charts**:
  - **Throughput**: Processing rate over time
  - **Items Per Chunk**: Distribution of items created

**Final Step: Charts Explored**
- **Success Indicator**: 
  - Viewed relevant charts
  - Understood job performance
  - Identified patterns or issues if any
- **Next Actions**: 
  - Switch to IdeaBlocks tab to see results
  - Return to all files view
  - Download report with chart data

---

## Error States & Recovery

### Error 1: Chart Shows No Data
**Cause**: Job hasn't generated chart data yet  
**User Experience**: 
- Empty chart or "No data available"

**Recovery Steps**:
1. Wait for job to process some chunks
2. Return later when data available

**QA Note**: Expected for jobs just started. Not error.

---

## Pain Points & Friction

**Identified Issues**:

1. **Chart Types Require Understanding**
   - **Impact**: Non-technical users may not interpret charts
   - **Potential Improvement**: Plain language explanations with charts

---

## Design Considerations

**Following Contextual Design Principles**:

1. **Simplification Opportunities**: Annotate charts with insights
2. **User Trust**: Accurate data representation
3. **Cognitive Load**: Visual easier than numerical data

---

## Related Flows

- [View Job Details Dashboard](./view-job-details.md) - Parent context
- [View Individual File Analytics](./view-file-analytics.md) - File-specific charts

---

## Technical References

**Knowledge Base Sections**:
- src/components/jobs/blockify-job-processing-screen/charts/ - Chart components
- Recharts library for visualization

---

## Version History

| Date | Version | Author | Changes |
|------|---------|--------|---------|
| 2025-10-04 | 1.1 | [Iternal Technologies](https://iternal.ai/airgapai) | Initial documentation |

---

## Notes

**Chart Types Explained**:
- **Progress**: Overall job completion by stage
- **Tokens/Second**: AI processing speed
- **E2E Latency**: Time to process each chunk
- **Throughput**: Items processed per time unit
- **Items Per Chunk**: How many items each chunk produced

**Best Practices**:
- Use progress for overview
- Use latency for troubleshooting slow processing
- Use throughput for rate tracking

**Common User Questions**:
- "Which chart is most useful?" - Depends on goal; Progress for monitoring, Latency for optimization
- "What do spikes mean?" - Variations in processing; may indicate difficult chunks

