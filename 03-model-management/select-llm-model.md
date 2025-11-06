# Select Active Chat Model

## Overview
**Flow ID**: `select-llm-model`  
**Category**: Model Management  
**Estimated Duration**: 1-2 minutes  
**User Role**: All Users  
**Complexity**: Simple  

**Purpose**: This flow allows users to choose which AI language model will be used for chat conversations. Different models have different capabilities, speeds, and specialties. Selecting the appropriate model ensures optimal performance for your specific needs.

---

## Trigger

**What initiates this flow:**
- [x] User manually initiates


**Specific trigger**: User needs to change which AI model is being used for conversations, typically because:
- They want to try a different model with different capabilities
- Current model is slow or not providing desired quality
- They've just uploaded a new model and want to use it
- They want a model better suited for a specific task
- System is using a default model they want to change

---

## Prerequisites

**Before starting, users must have:**
- [x] Application installed and running
- [x] At least one language model uploaded
- [x] Preferably: Multiple models to choose from
- [x] Understanding that changing models will reload the AI (takes 30-60 seconds)

---

## User Intent Analysis

### Primary Intent
Switch to a different AI language model to use for chat conversations, ensuring the chosen model matches their current needs for quality, speed, or specialization.

### Secondary Intents
- Optimize performance (speed vs. quality trade-off)
- Test different models to find the best one
- Use specialized models for specific tasks
- Resolve issues with current model
- Take advantage of newly uploaded models

### Subintents
- Understand differences between available models
- Ensure smooth transition without losing conversation data
- Minimize downtime during model switch

---

## Step-by-Step Flow

### Main Path (Happy Path)

**Step 1: Navigate to Settings**
- **User Action**: Click "Settings" in the main navigation menu
- **System Response**: Settings page loads
- **UI Elements Visible**: 
  - Navigation menu with "Settings" highlighted
  - Settings page content area
  - Multiple tabs across the top
- **Visual Cues**: Settings gear icon, highlighted navigation item

**Step 2: Access Chat Options Tab**
- **User Action**: Click the "Chat Options" tab in the Settings page
- **System Response**: Chat Options section displays
- **UI Elements Visible**: 
  - "Chat Options" tab (now highlighted/active)
  - Page content showing chat configuration options
  - Model selection section at the top
  - Label: "Chat AI Model" or similar
  - Dropdown selector showing currently active model
  - Additional settings below (context window, lookback size, etc.)
- **Visual Cues**: Active tab is visually distinct, model selector is prominent

**Step 3: Locate Model Selector**
- **User Action**: Find the "Chat AI Model" dropdown selector
- **System Response**: N/A (static element)
- **UI Elements Visible**: 
  - Label "Chat AI Model" or "Language Model"
  - Dropdown showing currently selected model name
  - Down arrow icon indicating it's a dropdown
  - Possibly: Tooltip icon with information
- **Visual Cues**: Dropdown has standard dropdown styling, current model name visible

**Step 4: Open Model Dropdown**
- **User Action**: Click on the model dropdown selector
- **System Response**: Dropdown menu expands showing all available models
- **UI Elements Visible**: 
  - Expanded dropdown list
  - Each model shown with:
    - Model name
    - Model type indicator (e.g., "LLM")
    - Currently selected model has checkmark or highlight
  - Dropdown overlay may dim background
- **Visual Cues**: 
  - Dropdown expands downward
  - Currently selected model has distinct styling
  - Hover state on dropdown items

**Step 5: Review Available Models**
- **User Action**: Read through the list of available models
- **System Response**: List remains open for browsing
- **UI Elements Visible**: 
  - Full list of uploaded language models
  - Model names (e.g., "Llama-3-8B-Instruct", "Mistral-7B")
  - Type indicators
  - Current selection marked
- **Visual Cues**: 
  - Scrollable list if many models
  - Clear visual distinction between models

**Step 6: Select Different Model**
- **User Action**: Click on the desired model from the dropdown
- **System Response**: 
  - Dropdown closes
  - Selected model name appears in the selector
  - Save button may appear or become enabled
  - System may show loading indicator
- **UI Elements Visible**: 
  - Dropdown closed, showing newly selected model
  - "Save" button (if not auto-save)
  - Possibly: Confirmation message or loading indicator
  - Model information card may update to show new model details
- **Visual Cues**: 
  - Selected model now displayed in dropdown
  - Visual feedback that selection changed

**Step 7: Save Selection (if required)**
- **User Action**: Click "Save" button if changes aren't automatic
- **System Response**: 
  - Settings are saved
  - Model begins loading
  - Loading indicator appears
- **UI Elements Visible**: 
  - Loading spinner or progress indicator
  - Status text: "Loading model..." or "Initializing..."
  - Progress percentage (possibly)
- **Visual Cues**: 
  - Animated loading indicator
  - May see splash screen or overlay while model loads

**Step 8: Model Loading Process**
- **User Action**: Wait for new model to load (30 seconds to 2 minutes)
- **System Response**: 
  - System unloads previous model
  - Loads new model into memory
  - Initializes model for inference
  - May display loading progress
- **UI Elements Visible**: 
  - Loading splash screen or overlay
  - Progress bar
  - Status messages: "Loading [Model Name]...", "Initializing model..."
  - Percentage complete (possibly)
  - Cannot interact with other parts of application during this time
- **Visual Cues**: 
  - Animated progress indicators
  - Page may be dimmed or blocked during loading

**Step 9: Model Loading Completes**
- **User Action**: No action required
- **System Response**: 
  - Loading indicator disappears
  - Success message may appear briefly
  - Settings page returns to normal
  - New model is now active
- **UI Elements Visible**: 
  - Normal Settings page view
  - Model selector showing new model as active
  - Possibly: Success notification "Model loaded successfully"
  - Model information card showing details of new model
- **Visual Cues**: 
  - Green checkmark or success color
  - Loading indicators removed
  - Interface fully responsive again

**Step 10: Verify Model Change**
- **User Action**: Confirm the new model is selected in the dropdown
- **System Response**: Dropdown shows new model as current selection
- **UI Elements Visible**: 
  - Model selector displaying new model name
  - Model details (if shown): Name, Type, Max Tokens, Path
  - No loading or error indicators
- **Visual Cues**: New model name clearly visible

**Final Step: Model Change Complete**
- **Success Indicator**: 
  - New model appears as selected in dropdown
  - No error messages
  - Can navigate away from Settings
  - Model is ready for use in conversations
- **System State Change**: 
  - New model loaded into memory
  - All new chat conversations will use this model
  - Existing conversations maintain their history but will use new model for new responses
  - Setting saved to database for persistence
- **Next Possible Actions**: 
  - Return to Chat page to start conversation with new model
  - Adjust related settings (context window size, temperature, etc.)
  - Run benchmark to test new model performance
  - Continue exploring Settings

---

## Alternative Paths & Strategies

### Strategy A: Quick Select from Model Info Card
**When to use**: If Settings page shows detailed model info card with selection option

**Steps**:
1. Navigate to Settings > Chat Options
2. Locate model information card (may be below dropdown)
3. If card shows different model, click "Use This Model" button in card
4. Model selection updates automatically
5. Model begins loading

### Strategy B: Select via Chat Page (if available)
**When to use**: If model selector is accessible from chat interface

**Steps**:
1. From Chat page, look for model indicator or selector (may be in header or toolbar)
2. Click model name or selector icon
3. Choose different model from menu
4. Confirm selection if prompted
5. Model loads and chat continues with new model

**QA Note**: This path is not currently available based on knowledge base review but included as potential alternative design.

### Strategy C: Change During Conversation
**When to use**: User wants to continue same conversation with different model

**Steps**:
1. From active chat, navigate to Settings
2. Select new model (Steps 1-9 from main path)
3. Return to chat conversation
4. Next message will use new model
5. Previous messages remain unchanged
6. Conversation context is preserved

---

## Error States & Recovery

### Error 1: No Models Available
**Cause**: No language models have been uploaded  
**User Experience**: 
- Dropdown is empty or shows "No models available"
- Cannot select a model
- May see message: "Please upload a model first"

**Recovery Steps**:
1. Navigate to Chat AI Models tab or similar model upload area
2. Upload a language model (see llm-model-upload.md)
3. Wait for upload to complete
4. Return to Chat Options
5. New model should now appear in dropdown

### Error 2: Model Loading Fails
**Cause**: Insufficient memory, corrupted model file, or system error  
**User Experience**: 
- Loading progress stops or fails
- Error message: "Failed to load model" or "Model error"
- May revert to previous model or leave no model active

**Recovery Steps**:
1. Note the error message if provided
2. Try selecting the model again
3. If fails again, try selecting a different model
4. Check system resources (RAM usage)
5. Close other applications to free memory
6. If persists, model file may be corrupted - try re-uploading
7. Restart application as last resort

### Error 3: Model Loading Timeout
**Cause**: Very large model taking too long to load  
**User Experience**: 
- Loading continues for excessive time (>5 minutes)
- May see error: "Loading timeout" or system may appear frozen

**Recovery Steps**:
1. Wait a bit longer (some large models can take 3-5 minutes)
2. If truly stuck (no progress for 5+ minutes), refresh page or restart application
3. Try selecting a smaller model
4. Check available RAM - large models may require 16GB+ RAM
5. Consider using a more powerful computer for very large models

### Error 4: Permission or File Access Error
**Cause**: System cannot access model file  
**User Experience**: 
- Error message: "Cannot access model file" or "Permission denied"
- Model fails to load

**Recovery Steps**:
1. Verify model file still exists in models directory
2. Check file permissions
3. Try restarting application with appropriate permissions
4. Re-upload model if file appears missing or corrupted
5. Contact support if permissions issues persist

### Error 5: Model Incompatibility
**Cause**: Model format not compatible with current application version  
**User Experience**: 
- Error message: "Incompatible model format" or similar
- Model fails to load

**Recovery Steps**:
1. Check model file format (should be compatible format like .gguf)
2. Verify application is up to date
3. Check model documentation for compatibility requirements
4. Try different model that's known to be compatible
5. Update application if model requires newer version

**QA Note**: This error should be rare if model upload process validates compatibility. Included for completeness.

---

## Pain Points & Friction

**Identified Issues**:

1. **Unclear Model Differences**
   - **Impact**: Users don't know which model to choose or what makes them different
   - **Frequency**: Every time user has multiple models
   - **Potential Improvement**: 
     - Add model descriptions or capabilities summary
     - Show comparison chart of speed vs. quality
     - Provide recommendations based on use case
     - Display model sizes and memory requirements

2. **Long Loading Times Not Explained**
   - **Impact**: Users unsure if system is working or stuck during 1-2 minute load
   - **Frequency**: Every model change
   - **Potential Improvement**: 
     - Show detailed loading stages ("Allocating memory...", "Loading weights...", etc.)
     - Display estimated time remaining
     - Explain first-time load may be slower
     - Show what's happening during load

3. **No Preview or Test Option**
   - **Impact**: Users must fully commit to loading a model to try it
   - **Frequency**: When evaluating models
   - **Potential Improvement**: 
     - Add "Quick Test" option to try model with sample query
     - Show recent performance metrics for each model
     - Display sample responses from different models

4. **Existing Conversations Not Clearly Affected**
   - **Impact**: Users uncertain what happens to ongoing conversations when they switch models
   - **Frequency**: When switching with active chats
   - **Potential Improvement**: 
     - Clearly explain that existing messages stay unchanged
     - Show warning if switching mid-conversation
     - Offer to start new chat with new model

5. **Cannot Switch Back Quickly if Dissatisfied**
   - **Impact**: If user doesn't like new model, must go through full loading process again to switch back
   - **Frequency**: Trial and error model selection
   - **Potential Improvement**: 
     - Keep recent model in memory for quick switching
     - Add "Undo" or "Switch Back" quick action
     - Remember last 2-3 models for fast switching

---

## Design Considerations

**Following Contextual Design Principles**:

1. **Automation Opportunities**: 
   - Auto-select best model based on available system resources
   - Auto-recommend model based on query type or conversation history
   - Pre-load commonly used models in background
   - Auto-switch to faster model if system resources limited

2. **Simplification Opportunities**: 
   - Reduce model selection to simple categories (Fast, Balanced, Best Quality)
   - Hide technical details unless user requests them
   - Auto-save model selection without requiring Save button
   - One-click model switching without navigation

3. **Transition Smoothness**: 
   - Smooth loading experience with clear progress
   - Seamless transition back to previous activity after model loads
   - No jarring interruptions when switching models
   - Preserve conversation context during model changes

4. **User Trust**: 
   - Clear indication of which model is active
   - Transparent loading process builds confidence
   - Success confirmation when model ready
   - Model actually works when loading completes (no silent failures)

5. **Cognitive Load**: 
   - Don't require users to understand technical model specifications
   - Simple, descriptive model names
   - Clear current selection always visible
   - Minimal steps to change models

---

## Related Flows

- [Upload Large Language Model](./llm-model-upload.md) - Add models to choose from
- [Configure Context Window Size](./configure-context-window.md) - Adjust model parameters
- [Run Full Benchmark Suite](../08-benchmarking/run-full-benchmark.md) - Compare model performance
- [View Model Information](./view-model-info.md) - See details about selected model
- [Create New Empty Chat](../02-chat-interactions/new-chat-empty.md) - Use selected model in conversation

---

## Technical References

**Knowledge Base Sections**:
- src/pages/settings.js - Settings page container
- src/components/chat-options-tab/index.js - Chat options interface
- src/components/ui/model-selection.js - Model selector component
- src/engines/llm.js - Model loading and initialization
- src/components/engine-initializer/index.js - Engine lifecycle management

**Key Components**:
- Model dropdown selector with list of available models
- Model loading progress indicator
- Model information display
- Settings persistence

---

## Version History

| Date | Version | Author | Changes |
|------|---------|--------|---------|
| 2025-10-04 | 1.1 | [Iternal Technologies](https://iternal.ai/airgapai) | Initial comprehensive documentation |

---

## Notes

**Important Considerations**:
- Changing models requires reloading the AI, which takes 30 seconds to 2 minutes depending on model size
- Larger models (13B+ parameters) may not run on systems with limited RAM (<16GB)
- The application must remain open during model loading; closing it will interrupt the process
- Model selection persists across application restarts
- All new conversations will use the selected model
- Existing conversation history is preserved when changing models

**Best Practices**:
- Choose models based on your priorities: smaller models are faster, larger models more capable
- Test models with benchmark suite to understand their performance on your hardware
- Use smaller models (3B-7B parameters) for quick interactions
- Use larger models (13B-70B parameters) for complex reasoning tasks
- Keep at least 2 models uploaded: one for speed, one for quality
- Document which models work best for which types of questions

**Common User Questions**:
- "Which model should I use?" - Depends on your hardware and needs; start with medium-sized models (7B-8B parameters)
- "Can I use multiple models at once?" - No, only one model can be active for chat at a time
- "Will changing models affect my chat history?" - No, history is preserved; only new responses use the new model
- "How do I know which model is best?" - Run benchmarks or try different models with the same questions to compare
- "Why does loading take so long?" - Large models (several GB) must be loaded into RAM, which takes time

