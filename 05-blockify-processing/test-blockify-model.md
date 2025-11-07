# Test Blockify Model

## Overview
**Flow ID**: `test-blockify-model`  
**Category**: Blockify Processing  
**Estimated Duration**: 1-3 minutes  
**User Role**: All Users  
**Complexity**: Simple  

**Purpose**: Test blockify model with sample text before running full job. Allows verifying model works correctly, understanding output format, and checking processing speed with small test.

---

## Trigger

**What initiates this flow:**
- [x] User manually initiates

**Specific trigger**: User wants to test blockify model before committing to full processing, typically because:
- First time using blockify feature
- Just uploaded new blockify model
- Want to see output format before processing many documents
- Checking model performance
- Verifying model works correctly

---

## Prerequisites

**Before starting, users must have:**
- [x] Blockify model uploaded and loaded
- [x] Access to Blockify page
- [x] Sample text to test (can type or paste)

---

## User Intent Analysis

### Primary Intent
Verify blockify model works correctly and understand its output format before running full job.

### Secondary Intents
- See processing speed for reference
- Understand IdeaBlock structure
- Verify model quality
- Check if results meet expectations

---

## Step-by-Step Flow

### Main Path

**Step 1: Access Test Interface**
- **User Action**: On Blockify page, find "Test Model" or similar option (may be tab or separate screen)
- **System Response**: Test interface displays
- **UI Elements Visible**: 
  - "Test Blockify Model" header
  - Large text input area for sample text
  - Character/token counter
  - "Run Test" button
  - Model status indicator
  - Possibly: Results area (empty initially)

**Step 2: Enter Test Text**
- **User Action**: Type or paste sample text into text area (recommended 200-1000 characters)
- **System Response**: 
  - Text appears as typed/pasted
  - Character and token count updates
  - "Run Test" button becomes enabled
- **UI Elements Visible**: 
  - Text area with sample content
  - Counter: "542 characters (~135 tokens)"
  - Enabled "Run Test" button
  - Model ready indicator

**Step 3: Review Model Status**
- **User Action**: Check that blockify model is loaded and ready
- **System Response**: Status indicator shows model state
- **UI Elements Visible**: 
  - Model status: "Ready" with green indicator
  - OR "Loading..." if still initializing
  - OR "Error" if model failed to load
  - Model name displayed

**Step 4: Run Test**
- **User Action**: Click "Run Test" button
- **System Response**: 
  - Test begins processing
  - Loading indicator appears
  - Status: "Processing test..."
- **UI Elements Visible**: 
  - Loading spinner
  - "Running test..." message
  - Disabled "Run Test" button during processing

**Step 5: Wait for Processing**
- **User Action**: Wait (typically 5-30 seconds depending on text length)
- **System Response**: 
  - Blockify model processes sample text
  - Generates structured output
  - Parses results
- **UI Elements Visible**: Processing indicator continues

**Step 6: View Results**
- **User Action**: Review test results
- **System Response**: Results display below input area
- **UI Elements Visible**: 
  - **Raw Result Section** (collapsible):
    - Shows raw AI output text
    - Formatted text as model generated it
    - Useful for debugging
  - **Parsed Blocks Section**:
    - Structured IdeaBlocks displayed
    - Each block showing:
      - **Block Name**: Title/heading
      - **Critical Question**: Key question addressed
      - **Trusted Answer**: Main content
    - May show 1-3 blocks depending on input size
  - **Usage Statistics**:
    - Tokens processed (input/output)
    - Processing time (seconds)
    - Speed metrics (tokens per second)
    - AI performance data

**Step 7: Assess Results Quality**
- **User Action**: Read parsed blocks to verify quality
- **System Response**: Static display of results
- **UI Elements Visible**: Complete test output
- **Assessment Points**:
  - Are blocks well-structured?
  - Do names make sense?
  - Are questions relevant?
  - Are answers complete?

**Step 8: Optional - Test Different Text**
- **User Action**: Clear or modify text, run test again
- **System Response**: New test executes with new text
- **UI Elements Visible**: Updated results

**Final Step: Model Tested Successfully**
- **Success Indicator**: 
  - Model processed text successfully
  - Output looks reasonable
  - Performance metrics visible
  - Understand output format
- **System State Change**: 
  - Confidence in model verified
  - Ready to use in full job
  - Know expected processing speed
- **Next Possible Actions**: 
  - Proceed with full blockify job
  - Try different test text
  - Adjust model settings if results poor
  - Switch to different blockify model if needed

---

## Alternative Paths & Strategies

### Strategy A: Test with Actual Document Excerpt
**When to use**: Want to see how model handles real content

**Steps**:
1. Open one of your documents
2. Copy 500-1000 characters of representative text
3. Paste into test area
4. Run test
5. Verify results match expectations for your content type

### Strategy B: Multiple Test Iterations
**When to use**: Evaluating model quality thoroughly

**Steps**:
1. Test with factual content
2. Note results
3. Test with narrative content
4. Compare results
5. Test with technical content
6. Assess which content types model handles best

---

## Error States & Recovery

### Error 1: Model Not Loaded
**Cause**: Blockify model not initialized  
**User Experience**: 
- Error message: "Model not ready" or "Please wait for model to load"
- Run Test button disabled
- Status shows "Loading..."

**Recovery Steps**:
1. Wait for model to finish loading (may take 1-2 minutes)
2. Model status will change to "Ready"
3. Run Test button will enable
4. Try test again

### Error 2: Test Processing Fails
**Cause**: Model error or insufficient resources  
**User Experience**: 
- Error message: "Test failed" or "Processing error"
- No results appear
- May show error details

**Recovery Steps**:
1. Try with shorter text sample
2. Check system resources (RAM)
3. Verify model is actually loaded
4. Restart application if persists
5. Try different blockify model if consistent failures

### Error 3: Parsing Fails
**Cause**: Model output doesn't match expected format  
**User Experience**: 
- Raw result appears but parsed blocks section shows warning
- Message: "Could not parse blocks" or similar
- Can see raw output but not structured blocks

**Recovery Steps**:
1. This indicates model output quality issue
2. Review raw result to see what model generated
3. Model may need different prompt or configuration
4. Try different text that's more structured
5. May need to use different blockify model

**QA Note**: Parsing failure doesn't stop test; raw results still shown. Users can assess model quality from raw output.

### Error 4: Test Text Too Short
**Cause**: Entered text is too short for meaningful processing  
**User Experience**: 
- Warning: "Text too short" or "Add more text for better results"
- May process but results minimal

**Recovery Steps**:
1. Add more text (recommended 200+ characters)
2. Include complete sentences and paragraphs
3. Run test with adequate content

---

## Pain Points & Friction

**Identified Issues**:

1. **No Sample Text Provided**
   - **Impact**: Users must provide their own test text
   - **Frequency**: First-time testers who don't have text ready
   - **Potential Improvement**: 
     - Include "Use Sample Text" button
     - Pre-populated example text
     - Quick-fill options for different content types

2. **Cannot Save Test Results**
   - **Impact**: Good test results are lost when page refreshes
   - **Frequency**: Users wanting to reference test output
   - **Potential Improvement**: 
     - Save test history
     - Export test results
     - Compare tests side-by-side

3. **No Comparison Between Models**
   - **Impact**: Can't easily compare different blockify models
   - **Frequency**: Users choosing between multiple models
   - **Potential Improvement**: 
     - Split view testing different models with same text
     - Save and compare results
     - Model comparison mode

4. **Limited Guidance on Interpreting Results**
   - **Impact**: Users see results but don't know if they're "good"
   - **Frequency**: First-time users
   - **Potential Improvement**: 
     - Quality indicators or scoring
     - Explanation of what makes good blocks
     - Examples of good vs. poor results

---

## Design Considerations

**Following Contextual Design Principles**:

1. **Automation Opportunities**: 
   - Auto-populate with sample text option
   - Auto-assess result quality
   - Auto-suggest optimal text length for testing

2. **Simplification Opportunities**: 
   - One-click test with provided sample
   - Hide raw results by default (show parsed only)
   - Simple pass/fail quality indicator

3. **Transition Smoothness**: 
   - Quick test execution
   - Smooth display of results
   - Easy to test multiple times
   - Natural flow to full job creation

4. **User Trust**: 
   - Transparent processing
   - Can see both raw and parsed output
   - Performance metrics visible
   - Accurate representation of full job behavior

5. **Cognitive Load**: 
   - Simple test interface
   - Clear results display
   - Don't require understanding technical metrics
   - Visual results easier to assess than numbers

---

## Related Flows

- [Create New Blockify Job](./create-blockify-job.md) - Uses tested model
- [Upload Large Language Model](../03-model-management/llm-model-upload.md) - Upload blockify models
- [Configure Advanced Chunk Settings with Preview](./configure-advanced-chunks.md) - Preview chunks vs. preview blockify

---

## Technical References

**Knowledge Base Sections**:
- src/components/blockify-corpus/blockify-test-screen.js - Test interface
- src/engines/blockify.js - Blockify model execution
- src/utils/blockify-parsers.js - Result parsing

**Key Components**:
- Test text input area
- Blockify model execution
- Result parsing and display
- Usage statistics tracking

---

## Version History

| Date | Version | Author | Changes |
|------|---------|--------|---------|
| 2025-10-04 | 1.1 | [Iternal Technologies](https://iternal.ai/airgapai) | Initial comprehensive documentation |

---

## Notes

**Important Considerations**:
- Test uses same blockify model as full job
- Test is quick (seconds) compared to full job (hours)
- Results format matches what full job produces
- Good way to verify model before committing to long processing
- Performance metrics help estimate full job duration

**IdeaBlock Structure**:
Each block has three components:
- **Block Name**: Title or heading summarizing the block
- **Critical Question**: Main question this block answers
- **Trusted Answer**: Detailed answer or content

**Usage Statistics Explained**:
- **Input Tokens**: How many tokens in your test text
- **Output Tokens**: How many tokens model generated
- **Processing Time**: Seconds to generate blocks
- **Tokens per Second**: Processing speed metric
- **Prefill/Decode Speed**: Advanced performance metrics

**Interpreting Test Results**:

**Good Results**:
- Block names are descriptive and accurate
- Questions are relevant to content
- Answers contain key information from text
- Structure is logical

**Poor Results**:
- Generic or nonsensical block names
- Questions don't relate to content
- Answers miss key information
- Parsing errors or malformed output

**Best Practices**:
- Test with representative sample of your actual documents
- Use 200-1000 characters for meaningful test
- Include complete thoughts/paragraphs, not fragments
- Test both simple and complex content
- Review both parsed blocks and raw output
- Note processing speed for estimating full job time
- If results poor, try different blockify model
- Don't judge too harshly on single test; models can vary per text

**Common User Questions**:
- "How long should my test text be?" - 200-1000 characters recommended
- "How many blocks will it create?" - Depends on content; typically 1-3 for test-sized text
- "What if parsing fails?" - Raw output still shown; may indicate model compatibility issue
- "Does testing cost tokens?" - Uses computational resources but no literal cost for offline
- "Should I test every time?" - Recommended for new models; optional for proven models
- "What makes a good block name?" - Should be descriptive, specific, and accurately summarize content

