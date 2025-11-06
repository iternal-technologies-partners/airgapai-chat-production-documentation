# Create New Empty Chat

## Overview
**Flow ID**: `new-chat-empty`  
**Category**: Chat Interactions  
**Estimated Duration**: 1-2 minutes  
**User Role**: All Users  
**Complexity**: Simple  

**Purpose**: This flow allows users to start a fresh conversation with the AI without any predefined templates or settings. It creates a blank slate for free-form conversation where users can ask any questions or have any type of discussion with the AI model.

---

## Trigger

**What initiates this flow:**
- [x] User manually initiates


**Specific trigger**: User wants to start a new conversation with the AI, typically because:
- They want to discuss a new topic unrelated to previous conversations
- They want to start fresh without conversation history
- They're trying the AI for the first time
- They finished a previous conversation and want to begin another

---

## Prerequisites

**Before starting, users must have:**
- [x] Application installed and running
- [x] At least one AI language model uploaded and available
- [x] Optionally: A dataset uploaded if they plan to use dataset query features
- [x] The model has finished loading (if it was just started)

---

## User Intent Analysis

### Primary Intent
Start a new, blank conversation with the AI to ask questions, get information, or have a discussion without any preset constraints or templates.

### Secondary Intents
- Organize conversations by topic (keeping different subjects in separate chats)
- Maintain conversation history for future reference
- Test AI capabilities with different prompts
- Have multiple concurrent conversations on different topics

### Subintents
- Ensure the AI is ready and responsive
- Begin with a clear context (no residual history from previous chats)
- Have the ability to customize chat settings if needed later

---

## Step-by-Step Flow

### Main Path (Happy Path)

**Step 1: Navigate to Chat Page**
- **User Action**: Click "Chat" in the main navigation menu
- **System Response**: The chat page loads and displays
- **UI Elements Visible**: 
  - Navigation menu with "Chat" highlighted
  - Chat sidebar on the left showing previous conversations (if any exist)
  - Main chat area in the center
  - New chat interface in the center (if no chat is currently open)
- **Visual Cues**: Chat icon in navigation, clean interface with input area prominently displayed

**Step 2: View New Chat Options**
- **User Action**: User observes the new chat creation interface in the center of the screen
- **System Response**: System displays the new chat creation screen with available options
- **UI Elements Visible**: 
  - Large text input box for entering first message
  - Prompt placeholder text (e.g., "What would you like to know?" or similar rotating prompts)
  - Dataset toggle control (icon showing dataset on/off status)
  - Upload file button (paperclip or upload icon)
  - Send button (typically an arrow or send icon)
  - Template selection buttons below the input (if any templates are configured)
  - Application disclaimer text at the bottom
- **Visual Cues**: 
  - Centered layout draws attention to input area
  - Placeholder text provides guidance
  - Send button may be disabled until text is entered

**Step 3: Begin Typing Message**
- **User Action**: Click into the large text input area and begin typing a question or message
- **System Response**: 
  - Cursor appears in text box
  - Text appears as user types
  - Placeholder text disappears
  - Send button becomes enabled (changes color, typically to blue)
  - Character count may appear (if limits exist)
- **UI Elements Visible**: 
  - Active text input with cursor
  - Typed text
  - Enabled send button
  - Optional: Character counter
  - Optional: Settings gear icon to access advanced options
- **Visual Cues**: 
  - Text input has focus (may have border highlight)
  - Send button color change indicates it's now clickable
  - Text box expands vertically if message is long

**Step 4: Optional - Enable Dataset Query**
- **User Action**: If user wants to query a dataset, click the dataset toggle/selector
- **System Response**: 
  - Dataset selector expands (if collapsed)
  - Dropdown menu shows available datasets
  - Currently selected dataset is highlighted
  - Toggle switches to "ON" state
- **UI Elements Visible**: 
  - Dataset selector dropdown
  - List of available datasets with names
  - ON/OFF toggle state indicator
  - Visual indication of which dataset is active
- **Visual Cues**: 
  - Toggle color changes (typically gray for OFF, blue for ON)
  - Dataset icon changes to indicate active state
- **Note**: This step can be skipped if dataset query is not needed

**Step 5: Optional - Upload Supporting Documents**
- **User Action**: If user wants to include documents for context, click the upload/paperclip icon
- **System Response**: File browser dialog opens
- **UI Elements Visible**: 
  - Operating system file browser
  - File type filters (PDF, TXT, DOCX, CSV)
- **Visual Cues**: Native file browser appearance
- **Note**: This step can be skipped if no documents are needed

**Step 6: Send First Message**
- **User Action**: Click the send button (arrow icon) or press Enter on keyboard (depending on settings)
- **System Response**: 
  - Input text is submitted
  - Text input area clears
  - Loading indicator appears in the chat area
  - Message appears in the conversation area with user name/icon
  - System begins generating response
- **UI Elements Visible**: 
  - User's message displayed in chat bubble (typically on the right side)
  - Loading indicator or "thinking" animation below the user's message
  - Progress message (e.g., "AI is thinking..." or "Generating response...")
  - Estimated time remaining (if available based on message length)
- **Visual Cues**: 
  - Animated thinking indicator (dots bouncing, spinner, or progress bar)
  - User message appears in distinct bubble or format
  - Chat interface scrolls to show the latest message

**Step 7: AI Response Generation**
- **User Action**: Wait for AI to generate response (no action required)
- **System Response**: 
  - AI generates response word by word (streaming)
  - Text appears progressively in the chat area
  - Response builds in real-time
- **UI Elements Visible**: 
  - AI response bubble appearing below user message
  - Text streaming in character by character or word by word
  - AI persona name/icon
  - Response area expanding as text fills in
- **Visual Cues**: 
  - Smooth text streaming animation
  - AI message appears in different format/color than user message (typically on the left side)
  - Cursor or typing indicator shows generation is in progress

**Step 8: Response Completes**
- **User Action**: Read the AI's complete response
- **System Response**: 
  - Streaming stops
  - Complete message is displayed
  - Action buttons appear below the message
- **UI Elements Visible**: 
  - Full AI response text
  - Action buttons below message: Copy, Edit, Redo, Like/Dislike icons
  - Text input becomes available again for next message
  - Message timestamp or metadata
- **Visual Cues**: 
  - Streaming animation stops
  - Response is fully rendered
  - Action buttons appear (may be subtle until hover)

**Step 9: Continue Conversation**
- **User Action**: Type another message in the text input to continue the conversation
- **System Response**: Same as Steps 3-8, maintaining conversation context
- **UI Elements Visible**: Same as before, with conversation history now visible above
- **Visual Cues**: Conversation flows naturally from previous messages

**Final Step: Chat Created and Active**
- **Success Indicator**: 
  - Conversation is visible in the chat area with user messages and AI responses
  - Chat appears in the left sidebar conversation list (may be titled "New Chat" or timestamped)
  - Can continue conversation with full history maintained
- **System State Change**: 
  - New chat record created in the database
  - Chat ID assigned
  - Conversation history begins accumulating
  - Chat appears in chat list for future access
- **Next Possible Actions**: 
  - Continue the conversation with additional messages
  - Edit chat settings (temperature, persona, etc.) via settings gear
  - Rename the chat to something more descriptive
  - Export the chat conversation
  - Start another new chat
  - Return to this chat later from the sidebar

---

## Alternative Paths & Strategies

### Strategy A: Send Message Immediately
**When to use**: User knows exactly what they want to ask and doesn't need to adjust any settings

**Steps**:
1. Navigate to Chat page
2. Type message directly into input box
3. Press Enter or click Send
4. Proceed directly to response generation (skipping all optional steps)

### Strategy B: Configure Settings Before Sending
**When to use**: User wants to customize AI behavior (temperature, personas, context) before starting conversation

**Steps**:
1. Navigate to Chat page
2. Click settings gear icon before typing
3. Advanced settings panel expands
4. Adjust desired settings (temperature, frequency penalty, personas, etc.)
5. Close or collapse settings panel
6. Type and send first message

### Strategy C: Start with Template
**When to use**: User wants to use a predefined conversation template (covered in separate flow: new-chat-template.md)

**Steps**:
1. Navigate to Chat page
2. Click one of the template buttons (e.g., "Sales Proposal", "Legal Review")
3. Template pre-fills settings and may provide initial context
4. Type first message in context of template
5. Send and proceed

### Strategy D: Type and Enable Dataset Mid-Message
**When to use**: User starts typing, then realizes they need dataset information

**Steps**:
1. Start typing message
2. Mid-typing, click dataset toggle to enable
3. Select appropriate dataset from dropdown
4. Continue typing or send as-is

---

## Error States & Recovery

### Error 1: No Model Selected/Available
**Cause**: No AI language model has been uploaded or selected as active  
**User Experience**: 
- Error message appears: "No AI model available" or "Please select a model"
- Send button may be disabled
- May see warning banner at top of chat

**Recovery Steps**:
1. Navigate to Settings page
2. Go to Chat AI Models or Chat Options tab
3. Upload a model if none exist (see llm-model-upload.md)
4. OR select an existing model as the active chat model
5. Return to Chat page and try again

### Error 2: Model Still Loading
**Cause**: Model is in the process of initializing (can take 30 seconds to 2 minutes)  
**User Experience**: 
- Loading overlay or splash screen shows "Loading model..."
- Progress bar or percentage indicator
- Cannot interact with chat interface yet

**Recovery Steps**:
1. Wait for model loading to complete
2. Progress indicator will show when ready
3. Chat interface will become available automatically when ready
4. No user action required beyond waiting

### Error 3: AI Response Generation Fails
**Cause**: Technical error during response generation  
**User Experience**: 
- Loading indicator stops
- Error message appears: "Failed to generate response" or similar
- Response bubble may show error state

**Recovery Steps**:
1. Click "Retry" or "Redo" button if available
2. OR send message again
3. If error persists, check system resources (RAM, disk space)
4. May need to restart application if model crashed

### Error 4: Message Too Long
**Cause**: User typed a message that exceeds character limit  
**User Experience**: 
- Error message: "Message exceeds maximum length"
- Character counter turns red
- Send button may become disabled

**Recovery Steps**:
1. Shorten your message
2. Split into multiple messages
3. OR upload long text as a document instead of typing directly

### Error 5: Network Connection Lost (if using remote models)
**Cause**: Connection to remote AI service interrupted  
**User Experience**: 
- Error message: "Connection lost" or "Cannot reach AI service"
- Response generation stops

**Recovery Steps**:
1. Check internet connection
2. Verify remote service is online
3. Try sending message again once connection is restored
4. Consider switching to local model if available

**QA Note**: This error only applies if user is using distributed/remote inference. For local-only setups, this error cannot occur.

---

## Pain Points & Friction

**Identified Issues**:

1. **Ambiguous Empty State**
   - **Impact**: First-time users may not immediately understand what to do or what to type
   - **Frequency**: Every new user's first interaction
   - **Potential Improvement**: 
     - Add example prompts or suggestions
     - Include brief "Getting Started" guide
     - Show sample conversations or common use cases

2. **No Indication of Model Capabilities**
   - **Impact**: Users don't know what types of questions the AI can answer well
   - **Frequency**: Constant throughout usage
   - **Potential Improvement**: 
     - Display model description or capabilities
     - Show recommended use cases for selected model
     - Provide guidance on prompt engineering

3. **Long First Response Time**
   - **Impact**: First response may take longer than subsequent ones (model initialization), causing user anxiety
   - **Frequency**: First message in each chat session
   - **Potential Improvement**: 
     - Explain that first response may be slower
     - Show more detailed progress (initialization vs. generation)
     - Pre-warm model if possible

4. **Unclear Dataset Toggle Purpose**
   - **Impact**: Users may not understand what the dataset toggle does or when to use it
   - **Frequency**: Users discovering the feature
   - **Potential Improvement**: 
     - Add tooltip explaining dataset query feature
     - Show examples of when to enable dataset
     - Provide visual indication of what changes when enabled

5. **No Autosave of Draft Messages**
   - **Impact**: If user types a long message and accidentally navigates away, text is lost
   - **Frequency**: Occasional user error
   - **Potential Improvement**: 
     - Auto-save draft messages locally
     - Warn before navigating away with unsent text
     - Restore draft when returning to page

---

## Design Considerations

**Following Contextual Design Principles**:

1. **Automation Opportunities**: 
   - Auto-suggest prompts based on user's previous conversations
   - Auto-select appropriate dataset based on message content
   - Auto-name chats based on first exchange instead of generic "New Chat"
   - Pre-load model during application startup to eliminate wait time

2. **Simplification Opportunities**: 
   - Reduce visual clutter in empty state
   - Hide advanced options until requested
   - Streamline dataset selection if user only has one dataset
   - Eliminate unnecessary confirmation steps

3. **Transition Smoothness**: 
   - Seamless flow from typing to sending to receiving response
   - Smooth animation during text streaming
   - Natural progression from empty state to active conversation
   - Easy to continue to next action (send another message)

4. **User Trust**: 
   - Show clear progress indicators during response generation
   - Display model name so user knows which AI they're talking to
   - Provide timestamps for message history
   - Make it clear when AI is "thinking" vs when response is complete

5. **Cognitive Load**: 
   - Minimal required inputs (just type and send)
   - Optional features are clearly marked as optional
   - Interface doesn't force decisions (can start typing immediately)
   - Clear visual hierarchy guides user attention to primary actions

---

## Related Flows

- [Create New Chat from Template](./new-chat-template.md) - Use predefined settings
- [Chat with Dataset Query Enabled](./rag-enabled-chat.md) - Include dataset information
- [Conduct Multi-Turn Conversation](./multi-turn-conversation.md) - Continue the conversation
- [Upload Document to Chat Context](./upload-document-to-chat.md) - Add file references
- [Entourage Mode Manage Chat Personas](./persona-management.md) - Customize AI behavior
- [Edit Chat Name Manually](./edit-chat-name-manual.md) - Rename this chat
- [Select Active Chat Model](../03-model-management/select-llm-model.md) - Change which AI model is used

---

## Technical References

**Knowledge Base Sections**:
- src/pages/chat.js - Main chat page container
- src/components/chat/new-chat.js - New chat creation interface
- src/components/chat/chat-input.js - Message input component
- src/components/chat/chat-message.js - Message display component
- src/engines/llm.js - AI response generation

**Key Components**:
- Chat input with file upload and dataset controls
- Message streaming display
- Chat sidebar for conversation history
- New chat template system

---

## Version History

| Date | Version | Author | Changes |
|------|---------|--------|---------|
| 2025-10-04 | 1.1 | [Iternal Technologies](https://iternal.ai/airgapai) | Initial comprehensive documentation |

---

## Notes

**Important Considerations**:
- The first message in a chat may take slightly longer as the system initializes conversation context
- Chats are automatically saved as you converse; there is no manual save required
- Chat history is maintained locally in your device
- You can have multiple chats open in different browser tabs if needed
- The AI maintains conversation context only within a single chat; starting a new chat means the AI won't remember previous conversations

**Common User Questions**:
- "Does the AI remember previous chats?" - No, each chat is independent. Start a new message within the same chat to maintain context.
- "How long can my messages be?" - Typically several thousand characters, but shorter messages often get better responses.
- "Can I edit a message after sending?" - Not the sent message itself, but you can use the "Redo" button to regenerate the AI's response or edit the chat settings and resend.
- "What's the difference between this and templates?" - Empty chat is free-form; templates pre-configure settings and sometimes provide initial prompts.

