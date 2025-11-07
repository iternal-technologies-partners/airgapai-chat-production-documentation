# Entourage Mode Manage Chat Personas

## Overview
**Flow ID**: `persona-management`  
**Category**: Chat Interactions  
**Estimated Duration**: 5-10 minutes  
**User Role**: All Users  
**Complexity**: Complex  

**Purpose**: This flow enables users to configure multiple AI "personas" within a single chat conversation. Each persona can have different behaviors, contexts, and purposes - for example, one persona that searches datasets, another that provides creative responses, or multiple personas simulating a team discussion. This allows for sophisticated multi-agent conversations and specialized AI behaviors.

---

## Trigger

**What initiates this flow:**
- [x] User manually initiates


**Specific trigger**: User wants to customize how the AI responds by creating or modifying personas, typically because:
- They want specialized AI behaviors for different purposes
- They need to simulate multiple perspectives or roles (e.g., legal team review)
- They want one persona for dataset queries and another for creative thinking
- They're using a template that includes multiple personas and want to adjust them
- They want to create a custom workflow or multi-agent system

---

## Prerequisites

**Before starting, users must have:**
- [x] Application installed and running
- [x] Active chat conversation (new or existing)
- [x] Understanding that personas affect AI behavior
- [x] Optionally: Dataset uploaded if planning to use dataset-query personas
- [x] Patience to configure advanced settings

---

## User Intent Analysis

### Primary Intent
Configure AI behavior by creating and managing multiple personas with different settings, contexts, and purposes to enable sophisticated, multi-faceted conversations.

### Secondary Intents
- Simulate team discussions with different viewpoints
- Separate dataset querying from creative responses
- Create specialized AI assistants for specific tasks
- Build reusable conversation workflows
- Experiment with different AI behaviors

### Subintents
- Understand persona configuration options
- Test persona behaviors before full use
- Organize personas for clear conversation flow
- Balance complexity with usability

---

## Step-by-Step Flow

### Main Path

**Step 1: Open Active Chat**
- **User Action**: Navigate to or create a chat conversation
- **System Response**: Chat interface displays
- **UI Elements Visible**: 
  - Chat conversation area
  - Message input at bottom
  - Settings gear icon (typically near input or in header)
- **Visual Cues**: Gear icon indicates settings available

**Step 2: Access Advanced Settings**
- **User Action**: Click the settings gear icon (typically in the input area or chat header)
- **System Response**: Advanced settings panel expands or opens
- **UI Elements Visible**: 
  - Expandable/collapsible settings panel (may slide in from side or expand inline)
  - Multiple sections or tabs:
    - General settings
    - Prompt configuration
    - **Personas section** (target area)
  - Close or collapse control
- **Visual Cues**: 
  - Panel slides in with animation
  - Sections clearly labeled
  - Personas section stands out

**Step 3: Locate Personas Section**
- **User Action**: Scroll to or click on "Personas" section in advanced settings
- **System Response**: Personas section displays or expands
- **UI Elements Visible**: 
  - "Personas" section header
  - List of current personas (if any exist)
  - Each persona shown as a card with:
    - Persona name
    - Brief description or status
    - Drag handle (for reordering)
    - Edit and delete icons
  - "Add Persona" button (prominent, likely blue)
  - "Teed Up Personas" section (if any queued for manual execution)
- **Visual Cues**: 
  - Persona cards visually distinct
  - Drag handles indicate reorderability
  - Add button stands out

**Step 4: Review Default Persona**
- **User Action**: Observe the default persona (typically "Sophie - Assistant" or similar)
- **System Response**: Default persona is displayed
- **UI Elements Visible**: 
  - First persona card showing default assistant
  - Name: e.g., "Sophie (Assistant)"
  - Configuration summary visible or collapsed
  - Edit and delete options available
- **Visual Cues**: Default persona may have special styling or icon

**Step 5: Initiate Add New Persona**
- **User Action**: Click "Add Persona" button
- **System Response**: Add persona modal or form appears
- **UI Elements Visible**: 
  - Modal dialog overlaying chat
  - Title: "Add Persona" or "Create New Persona"
  - Form fields:
    - **Persona Name** (text input)
    - **Persona Prompt/Instructions** (large text area)
    - **Context Type** (dropdown: None, Static Text, Dataset Query)
    - **Context Placement** (dropdown: Insert, Prepend, Append)
    - **Additional options** (checkboxes):
      - Disable generation (dataset results only)
      - First person voice
      - Disabled (inactive)
  - "Cancel" and "Save" or "Add" buttons
- **Visual Cues**: 
  - Modal centered and prominent
  - Required fields may have asterisks
  - Form organized logically

**Step 6: Name the Persona**
- **User Action**: Type a descriptive name in the Persona Name field
- **System Response**: Text appears as typed
- **UI Elements Visible**: 
  - Text input with entered name
  - Character count (if limited)
- **Visual Cues**: Active text field
- **Example Names**: "Legal Reviewer", "Dataset Expert", "Creative Writer", "Marketing Perspective"

**Step 7: Write Persona Instructions**
- **User Action**: In the prompt/instructions text area, write instructions that define this persona's role and behavior
- **System Response**: Text appears as typed, text area may expand
- **UI Elements Visible**: 
  - Large text area with instructions
  - May have helper text or examples
  - Character/token count possibly shown
- **Visual Cues**: Expandable text area
- **Example Instructions**: 
  - "You are a legal expert reviewing documents for compliance issues. Focus on risk assessment and regulatory concerns."
  - "You provide creative, innovative ideas without constraints. Think outside the box."
  - "You are a marketing professional analyzing content for audience appeal and messaging effectiveness."

**Step 8: Select Context Type**
- **User Action**: Click Context Type dropdown and select appropriate option
- **System Response**: Dropdown expands showing three options
- **UI Elements Visible**: 
  - Dropdown with options:
    - **None**: No additional context (AI relies only on prompt and conversation)
    - **Static Text**: Add custom text to every message
    - **Dataset Query**: Automatically search dataset and include results
  - Selected option highlighted
  - Additional fields may appear based on selection
- **Visual Cues**: 
  - Dropdown clearly shows current selection
  - Selection affects which additional fields appear

**Step 9a: Configure Static Text Context (if selected)**
- **User Action**: If "Static Text" was selected, enter text in the Context Info field that appears
- **System Response**: Text area for static context becomes available
- **UI Elements Visible**: 
  - "Context Info" text area
  - Instructions explaining this text will be included with every message
- **Visual Cues**: Conditional field appears based on Context Type selection
- **Use Case**: Company policies, reference information, guidelines that should always be included

**Step 9b: Configure Dataset Query Context (if selected)**
- **User Action**: If "Dataset Query" was selected, system may auto-use active dataset or show dataset selector
- **System Response**: Dataset query will be performed automatically for this persona
- **UI Elements Visible**: 
  - Indication that dataset queries will be performed
  - May show which dataset will be queried
  - Number of results to retrieve (may be configurable here or in general settings)
- **Visual Cues**: Dataset icon or indicator
- **Use Case**: Personas that should always reference your documents

**Step 10: Select Context Placement**
- **User Action**: Choose how context should be included relative to user's message
- **System Response**: Dropdown shows three options
- **UI Elements Visible**: 
  - Context Placement dropdown with:
    - **Insert**: Add as separate message before AI response
    - **Prepend**: Add to beginning of user's message
    - **Append**: Add to end of user's message
  - Selected option highlighted
- **Visual Cues**: Dropdown clearly indicates selection
- **Note**: Affects how AI interprets context

**Step 11: Configure Additional Options**
- **User Action**: Check or uncheck optional checkboxes based on desired behavior
- **System Response**: Checkboxes toggle on/off
- **UI Elements Visible**: 
  - **Disable Generation** checkbox: If checked, persona returns only dataset results without AI processing
  - **First Person** checkbox: If checked, AI responds in first-person voice
  - **Disabled** checkbox: If checked, persona exists but won't be used
- **Visual Cues**: Checked boxes have checkmarks, clear labels explain each option

**Step 12: Save New Persona**
- **User Action**: Click "Save" or "Add" button
- **System Response**: 
  - Modal closes
  - New persona appears in personas list
  - Settings are saved
- **UI Elements Visible**: 
  - Personas section now shows new persona card
  - New persona appears in list (may be at bottom or top)
  - Persona card shows name and brief configuration summary
- **Visual Cues**: 
  - Smooth modal dismissal
  - New persona card appears with animation

**Step 13: Review Personas List**
- **User Action**: Look at the updated personas list
- **System Response**: All personas displayed
- **UI Elements Visible**: 
  - Multiple persona cards (default + newly added)
  - Each showing:
    - Name
    - Drag handle (six dots or bars)
    - Edit button (pencil icon)
    - Delete button (trash or X icon)
    - Configuration hints (icons for context type, etc.)
- **Visual Cues**: 
  - Cards clearly separated
  - Drag handles indicate reorderability

**Step 14: Optional - Reorder Personas**
- **User Action**: Click and drag a persona card to reorder
- **System Response**: 
  - Persona card follows cursor
  - Other personas shift to make space
  - Drop persona in new position
- **UI Elements Visible**: 
  - Persona being dragged appears elevated/highlighted
  - Drop zones indicated between other personas
  - Real-time reordering preview
- **Visual Cues**: 
  - Drag and drop animation
  - Visual feedback during drag
- **Note**: Order affects response sequence if multiple personas used

**Step 15: Optional - Edit Existing Persona**
- **User Action**: Click edit button (pencil icon) on a persona card
- **System Response**: Edit modal opens with persona's current settings pre-filled
- **UI Elements Visible**: 
  - Same modal as "Add Persona" but with "Edit Persona" title
  - All fields populated with current values
  - Can modify any field
  - "Cancel" and "Save Changes" buttons
- **Visual Cues**: Pre-filled form indicates editing mode

**Step 16: Close Advanced Settings**
- **User Action**: Click close button or collapse settings panel
- **System Response**: Settings panel closes or collapses
- **UI Elements Visible**: 
  - Chat interface returns to normal view
  - Conversation area and input fully visible
  - Settings gear icon available to reopen
- **Visual Cues**: Smooth collapse/close animation

**Step 17: Use Personas in Conversation**
- **User Action**: Send a message in the chat
- **System Response**: 
  - If multiple personas configured, system may use first persona OR prompt for selection
  - Persona's instructions, context type, and settings affect response
  - Response reflects persona configuration
- **UI Elements Visible**: 
  - AI response attributed to specific persona name
  - Response content reflects persona's instructions and context
  - May see context information if configured
- **Visual Cues**: 
  - Persona name appears with response
  - Response style matches persona configuration

**Final Step: Personas Configured and Active**
- **Success Indicator**: 
  - Multiple personas exist in settings
  - Can edit, reorder, or delete personas
  - Personas affect conversation behavior as intended
  - Context is applied appropriately
  - Responses match persona instructions
- **System State Change**: 
  - Chat has multiple persona configurations saved
  - Conversation uses persona settings for responses
  - Settings persist for this chat
  - Can return to modify personas anytime
- **Next Possible Actions**: 
  - Continue conversation using configured personas
  - Test different personas by modifying settings
  - Create more personas for additional perspectives
  - Manually trigger specific personas (if "teed up" feature used)
  - Export or reuse persona configurations in new chats

---

## Alternative Paths & Strategies

### Strategy A: Quick Edit Default Persona Only
**When to use**: User wants simple customization without multiple personas

**Steps**:
1. Open advanced settings
2. Click edit on default persona
3. Modify instructions to change AI behavior
4. Save
5. Use chat with modified single persona

### Strategy B: Use Template with Pre-Configured Personas
**When to use**: Starting chat with template that includes multiple personas

**Steps**:
1. Create new chat, select template (e.g., "Legal Review Team")
2. Template automatically loads multiple personas
3. Review pre-configured personas in settings
4. Optionally adjust persona settings
5. Use conversation with full team immediately

### Strategy C: Manual Persona Execution ("Teed Up")
**When to use**: Want to control which persona responds to each message

**Steps**:
1. Configure multiple personas
2. In personas section, use "Teed Up" controls
3. Queue specific persona(s) for next response
4. Send message
5. Only teed-up persona responds
6. Repeat for different perspectives

### Strategy D: Delete All and Start Fresh
**When to use**: Persona configuration became too complex, want to reset

**Steps**:
1. Open advanced settings > Personas
2. Delete each persona (except cannot delete all, must keep one)
3. Edit remaining persona to be new default
4. Add new personas with simpler configuration
5. Save and use refreshed setup

---

## Error States & Recovery

### Error 1: No Persona Name Provided
**Cause**: User tries to save persona without entering name  
**User Experience**: 
- Error message: "Persona name is required"
- Cannot save until name entered
- Field may have red border

**Recovery Steps**:
1. Enter a name in the Persona Name field
2. Click Save again
3. Persona should save successfully

**QA Note**: Form validation should prevent saving. If save button is disabled until name entered, error won't occur.

### Error 2: Persona Instructions Empty
**Cause**: User provides persona name but no instructions  
**User Experience**: 
- Persona may save but behave generically
- No clear guidance for AI behavior
- May see warning about empty instructions

**Recovery Steps**:
1. Edit persona
2. Add clear, specific instructions
3. Save changes
4. Test persona to verify behavior improved

**QA Note**: Empty instructions not technically an error, but results in poor persona behavior. System may allow it.

### Error 3: Context Type Mismatch
**Cause**: "Dataset Query" selected but no dataset available or activated  
**User Experience**: 
- Persona may show error during use
- Message: "Dataset not available"
- Persona fails to function properly

**Recovery Steps**:
1. Ensure dataset is uploaded and activated
2. Edit persona to verify Context Type settings
3. OR change Context Type to "None" or "Static Text" if dataset not needed
4. Save and retry

### Error 4: Cannot Delete Last Persona
**Cause**: User tries to delete all personas (system requires at least one)  
**User Experience**: 
- Delete button may be disabled on last persona
- Error message: "At least one persona required"
- Cannot complete deletion

**Recovery Steps**:
1. This is by design - keep at least one persona
2. Edit the remaining persona instead of deleting
3. Modify it to desired default behavior

**QA Note**: Technical requirement, not recoverable error. User must maintain minimum one persona.

### Error 5: Persona Configuration Too Complex
**Cause**: Multiple personas with conflicting settings or unclear order  
**User Experience**: 
- Responses seem random or inconsistent
- Unclear which persona is responding
- Conversation doesn't flow logically

**Recovery Steps**:
1. Simplify persona configuration
2. Reduce number of active personas
3. Clarify persona instructions to avoid conflicts
4. Test with fewer personas first
5. Gradually add complexity

**QA Note**: Not technical error - user-created complexity. System works but results unsatisfactory.

---

## Pain Points & Friction

**Identified Issues**:

1. **Complexity Overwhelming for New Users**
   - **Impact**: Advanced persona features can intimidate users unfamiliar with AI customization
   - **Frequency**: All first-time persona users
   - **Potential Improvement**: 
     - Add "Simple" and "Advanced" modes
     - Provide templates for common persona configurations
     - Wizard-style guided setup
     - Progressive disclosure of advanced options

2. **Unclear When Multiple Personas Are Used**
   - **Impact**: Users don't understand if all personas respond or just one
   - **Frequency**: When multiple personas configured
   - **Potential Improvement**: 
     - Clearly explain execution model
     - Show which personas will respond before sending
     - Add preview of persona behavior
     - Visual indicators during conversation

3. **No Easy Way to Test Personas**
   - **Impact**: Must use personas in real conversation to see if they work as intended
   - **Frequency**: Every new persona configuration
   - **Potential Improvement**: 
     - Add "Test Persona" button with sample query
     - Show preview of how persona will respond
     - Sandbox mode for experimentation
     - Example responses for different persona types

4. **Context Placement Options Confusing**
   - **Impact**: Users don't understand difference between Insert/Prepend/Append
   - **Frequency**: Configuring context-enabled personas
   - **Potential Improvement**: 
     - Add visual examples showing difference
     - Use simpler terminology
     - Provide recommendations based on use case
     - Show preview of how context appears

5. **Cannot Save Persona as Template**
   - **Impact**: Must recreate personas manually for each new chat
   - **Frequency**: When reusing similar configurations
   - **Potential Improvement**: 
     - Add "Save as Template" option
     - Share personas between chats
     - Create persona library
     - Export/import persona configurations

6. **Drag and Drop Can Be Finicky**
   - **Impact**: Accidentally reorder personas or can't get drop to work
   - **Frequency**: When reordering personas
   - **Potential Improvement**: 
     - Larger drag hit areas
     - Clearer drop zone indicators
     - Alternative: Up/down arrows for reordering
     - Undo for accidental reorders

---

## Design Considerations

**Following Contextual Design Principles**:

1. **Automation Opportunities**: 
   - Auto-suggest persona types based on user goals
   - Auto-configure context settings based on persona type
   - Auto-generate persona instructions from templates
   - Auto-order personas by logical conversation flow

2. **Simplification Opportunities**: 
   - Reduce options to essential settings for most users
   - Provide preset personas for common use cases
   - Hide advanced options until requested
   - Wizard or guided setup for complex configurations

3. **Transition Smoothness**: 
   - Smooth modal opening/closing
   - Immediate effect of persona changes in conversation
   - Easy to switch between editing and using
   - Personas don't interrupt conversation flow

4. **User Trust**: 
   - Clear indication of how personas affect responses
   - Preview or test capability builds confidence
   - Transparent about which persona is responding
   - Consistent persona behavior

5. **Cognitive Load**: 
   - Don't require understanding of technical AI concepts
   - Use plain language for settings
   - Provide examples and guidance
   - Start simple, allow complexity for advanced users

---

## Related Flows

- [Create New Chat from Template](./new-chat-template.md) - Templates with pre-configured personas
- [Chat with Dataset Query Enabled](./rag-enabled-chat.md) - Dataset context in personas
- [Conduct Multi-Turn Conversation](./multi-turn-conversation.md) - Using personas in conversation
- [Configure Chat Behavior Settings](../07-settings-configuration/configure-chat-settings.md) - Related settings
- [Create New Empty Chat](./new-chat-empty.md) - Starting point for persona configuration

---

## Technical References

**Knowledge Base Sections**:
- src/components/chat/chat-advanced-settings.js - Persona management interface
- src/components/ui/persona-card.js - Individual persona display
- src/pages/chat.js - Persona execution logic
- src/constants/chat.js - Persona configuration constants
- src/localdb/workflow-config.js - Template personas

**Key Components**:
- Persona management modal with form
- Drag-and-drop reordering
- Context configuration options
- Multi-persona execution system

---

## Version History

| Date | Version | Author | Changes |
|------|---------|--------|---------|
| 2025-10-04 | 1.1 | [Iternal Technologies](https://iternal.ai/airgapai) | Initial comprehensive documentation |

---

## Notes

**Important Considerations**:
- Personas are chat-specific; each chat has its own persona configuration
- Template chats may include pre-configured personas
- Persona configuration is saved automatically with the chat
- Complex persona setups may slow response generation slightly
- Personas with dataset queries add processing time per message

**Persona Context Types Explained**:
- **None**: Standard AI responses based only on instructions and conversation history
- **Static Text**: Always includes specified text (e.g., company policies, reference info)
- **Dataset Query**: Automatically searches your dataset and includes relevant results

**Context Placement Explained**:
- **Insert**: Adds context as separate system message (AI sees it as distinct from user input)
- **Prepend**: Adds context before user's message (AI sees it as part of user's question)
- **Append**: Adds context after user's message (AI sees it as additional information)

**Best Practices**:
- Start with single default persona, add more only when needed
- Give personas clear, specific instructions
- Test personas individually before combining multiple
- Use descriptive names that indicate persona purpose
- Keep configurations simple unless complexity is required
- Document persona purposes for future reference

**Common User Questions**:
- "How many personas can I have?" - Technically unlimited, but practical limit around 3-5 for usability
- "Do all personas respond to every message?" - Depends on configuration; typically one at a time unless manually triggered
- "Can I use the same persona in different chats?" - Must configure separately per chat, or use templates
- "What's the difference between personas and templates?" - Templates create new chats with preset personas; personas are configured within a chat
- "Will personas remember previous messages?" - Yes, personas have access to full conversation history within the chat

