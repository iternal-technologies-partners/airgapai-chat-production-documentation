# Conduct Multi-Turn Conversation

## Overview
**Flow ID**: `multi-turn-conversation`  
**Category**: Chat Interactions  
**Estimated Duration**: Ongoing (varies by conversation length)  
**User Role**: All Users  
**Complexity**: Simple  

**Purpose**: This flow describes how users continue an ongoing conversation with the AI, sending multiple messages back and forth. The AI maintains context from previous messages in the conversation, allowing for natural, contextual discussions where questions can reference earlier parts of the conversation.

---

## Trigger

**What initiates this flow:**
- [x] User manually initiates


**Specific trigger**: User wants to continue a conversation after the AI has responded to their first message, typically because:
- They want to ask a follow-up question
- They need clarification on the AI's previous response
- They want to explore the topic in more depth
- They want to shift the conversation to a related topic
- They received a partial answer and need more information

---

## Prerequisites

**Before starting, users must have:**
- [x] Active chat conversation already started (see new-chat-empty.md)
- [x] At least one exchange completed (user message + AI response)
- [x] Chat interface open and visible
- [x] AI model loaded and ready

---

## User Intent Analysis

### Primary Intent
Continue an existing conversation with the AI while maintaining context from previous messages, enabling natural back-and-forth dialogue similar to conversing with a person.

### Secondary Intents
- Build upon previous responses to dive deeper into a topic
- Refine or clarify information received in earlier responses
- Explore tangential or related subjects
- Test the AI's consistency and context retention
- Develop complex ideas through iterative discussion

### Subintents
- Ensure the AI remembers previous context
- Get progressively more detailed or specific information
- Verify understanding through follow-up questions
- Maintain conversation coherence across multiple exchanges

---

## Step-by-Step Flow

### Main Path (Happy Path)

**Step 1: Review Previous AI Response**
- **User Action**: Read and process the AI's latest response in the conversation
- **System Response**: Chat history is displayed with all previous messages visible (can scroll up to see earlier exchanges)
- **UI Elements Visible**: 
  - Conversation thread showing all previous messages
  - User messages on the right (or in user-designated style)
  - AI messages on the left (or in AI-designated style)
  - Action buttons under AI's latest message (Copy, Redo, Like/Dislike)
  - Text input box at the bottom, ready for next message
  - Send button
- **Visual Cues**: 
  - Clear distinction between user and AI messages through color, position, or styling
  - Latest message is at the bottom of the visible chat area
  - Scrollbar indicates if there are more messages above

**Step 2: Formulate Follow-Up Message**
- **User Action**: Think about and compose the next message based on the AI's response
- **System Response**: Text input remains active and ready
- **UI Elements Visible**: 
  - Empty text input field with cursor
  - Placeholder text (if no text entered yet)
  - All previous conversation visible above
  - Dataset toggle (if applicable)
  - File upload option
- **Visual Cues**: 
  - Input field is prominent and accessible
  - Context from previous messages is easily visible by scrolling up

**Step 3: Type Follow-Up Message**
- **User Action**: Click into text input (if not already focused) and type the follow-up message
- **System Response**: 
  - Text appears as typed
  - Text box may expand vertically if message is long
  - Send button becomes enabled
  - Character count updates (if visible)
- **UI Elements Visible**: 
  - Active text input with your typed message
  - Enabled send button (changes to active color)
  - Previous conversation history above
  - Optional: Advanced settings gear icon
- **Visual Cues**: 
  - Text input has focus indicator
  - Send button color indicates it's ready to click
  - Automatic text wrapping in input box

**Step 4: Optional - Reference Previous Context**
- **User Action**: User may write message that explicitly references earlier parts of the conversation (e.g., "Based on what you said about...", "Can you expand on the second point?")
- **System Response**: No special system response; text is treated as normal input
- **UI Elements Visible**: Same as Step 3
- **Visual Cues**: N/A
- **Note**: The AI uses conversation history automatically; explicit references are optional but can help clarity

**Step 5: Send Follow-Up Message**
- **User Action**: Click send button or press Enter
- **System Response**: 
  - Message is submitted
  - User's message appears in the conversation thread
  - Text input clears
  - Loading indicator appears below user's new message
  - System begins generating AI response
- **UI Elements Visible**: 
  - User's new message added to conversation thread
  - Loading/thinking animation
  - Progress text ("AI is thinking..." or estimated time)
  - Previous conversation history scrolls up to accommodate new messages
- **Visual Cues**: 
  - Animated loading indicator
  - Chat automatically scrolls to show the latest message and loading state
  - Smooth animation as new message appears

**Step 6: AI Processes Context**
- **User Action**: None (wait for response)
- **System Response**: 
  - AI reviews all previous messages in the conversation (up to a context limit)
  - AI generates contextually relevant response
  - Response begins streaming
- **UI Elements Visible**: 
  - Loading animation continues briefly
  - AI response bubble begins appearing
  - Text starts streaming in
- **Visual Cues**: 
  - Transition from loading to response streaming
  - AI message bubble expands as text fills in

**Step 7: Receive Contextual Response**
- **User Action**: Read the AI's contextual response as it streams in
- **System Response**: 
  - Response continues streaming word by word
  - AI demonstrates awareness of previous context
  - Response may reference or build upon earlier exchanges
- **UI Elements Visible**: 
  - AI response text appearing progressively
  - Response bubble expanding
  - Conversation history scrolling to keep current response visible
- **Visual Cues**: 
  - Smooth text animation
  - Response appears in AI's message style
  - May see thinking indicator briefly between pauses

**Step 8: Response Completes**
- **User Action**: Finish reading the complete response
- **System Response**: 
  - Streaming stops
  - Full response is visible
  - Action buttons appear
  - Text input becomes ready for next message
- **UI Elements Visible**: 
  - Complete AI response
  - Action buttons (Copy, Redo, Like/Dislike)
  - Empty text input ready for next follow-up
  - Send button (disabled until text is entered)
- **Visual Cues**: 
  - Streaming animation stops
  - Cursor returns to text input
  - Visual indication that it's the user's turn to respond

**Step 9: Decide Whether to Continue**
- **User Action**: User decides whether to:
  - Ask another follow-up question (return to Step 3)
  - End the conversation (take no action)
  - Perform other actions (export chat, adjust settings, etc.)
- **System Response**: Waits for user input
- **UI Elements Visible**: Same as Step 8
- **Visual Cues**: Interface remains ready for user action

**Step 10 (Optional): Continue Conversation Loop**
- **User Action**: To continue conversation, repeat Steps 3-9
- **System Response**: Each cycle adds more context to the conversation
- **UI Elements Visible**: Conversation thread grows with each exchange
- **Visual Cues**: Scrollbar indicates expanding conversation history

**Final Step: Ongoing Conversation**
- **Success Indicator**: 
  - Multiple exchanges between user and AI are visible
  - AI responses demonstrate awareness of previous context
  - Conversation flows naturally
  - No errors or context loss
- **System State Change**: 
  - Conversation history accumulates in the database
  - Context window fills with messages (subject to model limits)
  - Chat becomes more contextually rich
  - Chat may be auto-named based on content
- **Next Possible Actions**: 
  - Continue adding more messages to the conversation
  - Edit chat settings if AI responses need adjustment
  - Export the conversation for reference
  - Start a new chat on a different topic
  - End the session and return later (conversation is saved)

---

## Alternative Paths & Strategies

### Strategy A: Rapid-Fire Questions
**When to use**: User has a list of quick questions to ask in succession

**Steps**:
1. Type first question and send
2. While AI is responding, mentally prepare next question
3. As soon as AI finishes, immediately type and send next question
4. Repeat for each question in the list
5. Can result in very long conversation threads quickly

### Strategy B: Deep Dive on One Topic
**When to use**: User wants comprehensive information on a single subject

**Steps**:
1. Ask initial broad question
2. Based on response, ask for more detail on specific aspects
3. Continue drilling down with increasingly specific questions
4. Ask for examples, clarifications, or elaborations
5. Build a thorough understanding through layered questioning

### Strategy C: Correction and Refinement
**When to use**: User needs to correct or refine their original question

**Steps**:
1. Receive AI response
2. Realize the question wasn't clear or was misunderstood
3. Send clarifying message: "Actually, I meant..." or "Let me rephrase..."
4. AI responds based on the clarified intent
5. Continue from the corrected understanding

### Strategy D: Topic Shifting
**When to use**: User wants to change subjects while staying in the same chat

**Steps**:
1. Complete discussion on first topic
2. Send message indicating topic change: "Now let's discuss..." or "Switching topics..."
3. AI acknowledges shift and begins new topic
4. Continue with new subject (AI may still remember previous topic)

### Strategy E: Use Redo Button
**When to use**: User wants a different version of the AI's last response without sending a new message

**Steps**:
1. After receiving AI response, click "Redo" button under the message
2. AI regenerates response with the same input
3. Compare new response to original
4. Can click Redo multiple times to get different variations
5. Continue conversation from preferred response version

---

## Error States & Recovery

### Error 1: Context Limit Exceeded
**Cause**: Conversation has become so long that older messages fall outside the AI's context window  
**User Experience**: 
- AI seems to "forget" things said many exchanges ago
- Responses may lack continuity with early conversation
- No explicit error message (degraded behavior)

**Recovery Steps**:
1. Summarize key points from earlier in the conversation
2. Re-include important context in your current message
3. Consider starting a new chat if the topic has shifted significantly
4. Use export feature to save the conversation before starting fresh

**QA Note**: This is not a technical error but a model limitation. System cannot error-check for this condition, only user can notice the quality degradation.

### Error 2: Response Generation Times Out
**Cause**: AI takes too long to generate a response (network issue, system overload, or very complex query)  
**User Experience**: 
- Loading indicator continues for an unusually long time
- May eventually show error: "Response generation timed out" or similar
- Partial response may be visible if it started streaming

**Recovery Steps**:
1. Wait an additional moment (may just be slow)
2. If timeout error appears, click "Redo" to try again
3. Try simplifying or breaking down your question
4. Check system resources (CPU, RAM usage)
5. Consider restarting the application if persists

### Error 3: Model Crashes Mid-Conversation
**Cause**: AI model encounters a technical issue and stops working  
**User Experience**: 
- Response stops streaming abruptly
- Error message: "Model error" or "Failed to generate response"
- Cannot send new messages until model reloads

**Recovery Steps**:
1. System may automatically reload the model (wait 30-60 seconds)
2. Loading screen may appear during reload
3. Once reloaded, conversation history is typically preserved
4. Last message may need to be resent
5. If reload fails, may need to restart application

### Error 4: Text Input Becomes Unresponsive
**Cause**: Browser or application interface issue  
**User Experience**: 
- Cannot type in text input field
- Clicking in text box doesn't activate it
- Keyboard input doesn't appear

**Recovery Steps**:
1. Click outside the text box, then click back in
2. Refresh the page (conversation should be saved)
3. Try clicking directly on the send button area, then back to text input
4. As last resort, close and reopen the chat (data is saved)

### Error 5: Messages Appear Out of Order
**Cause**: Rare timing issue with rapid message sending  
**User Experience**: 
- Messages display in incorrect sequence
- AI response doesn't match the expected question
- Conversation flow seems broken

**Recovery Steps**:
1. Refresh the page to reload conversation in correct order
2. If order is still incorrect, note which messages are mismatched
3. Continue conversation by explicitly stating which question you're following up on
4. Report the issue if it happens frequently

**QA Note**: This error is theoretically possible but extremely rare in local-only deployments.

---

## Pain Points & Friction

**Identified Issues**:

1. **Context Window Limits Not Visible**
   - **Impact**: Users don't know when they're approaching context limits; AI gradually "forgets" without warning
   - **Frequency**: Occurs in every long conversation
   - **Potential Improvement**: 
     - Display context usage meter (e.g., "35 of 50 messages in context")
     - Warn when approaching limit
     - Offer to summarize and start fresh while preserving key information

2. **No Visual Distinction of Context-Aware Responses**
   - **Impact**: Users can't tell if the AI successfully used previous context or just answered generically
   - **Frequency**: Constant concern, especially for validation
   - **Potential Improvement**: 
     - Highlight or link referenced context in responses
     - Show tooltip indicating which previous messages were used
     - Add "context strength" indicator

3. **Difficult to Reference Specific Previous Messages**
   - **Impact**: In long conversations, hard to point to a specific earlier exchange without scrolling and copying
   - **Frequency**: Common in complex discussions
   - **Potential Improvement**: 
     - Add message numbering or timestamps that can be referenced
     - Add "reply to" or "reference" button on previous messages
     - Implement quote/reference feature

4. **Loss of Response if Connection Fails**
   - **Impact**: If AI was mid-response and connection fails, the partial response is lost
   - **Frequency**: Occasional with local models, more common with remote
   - **Potential Improvement**: 
     - Save partial responses during streaming
     - Allow resuming from partial response
     - Provide "regenerate" option that preserves visible partial content

5. **Input Box Hidden When Scrolling Through History**
   - **Impact**: When reviewing earlier messages, user must scroll back down to send next message
   - **Frequency**: Every time user scrolls up to review context
   - **Potential Improvement**: 
     - Sticky/floating input box that remains accessible
     - Quick scroll-to-bottom button
     - Keyboard shortcut to jump to input

6. **No Indicators for Long Processing Times**
   - **Impact**: Complex questions may take longer; user doesn't know if system is working or stuck
   - **Frequency**: With complex queries or large context windows
   - **Potential Improvement**: 
     - Show processing stage (reading context, thinking, generating)
     - Display token count being processed
     - Estimate time remaining based on input complexity

---

## Design Considerations

**Following Contextual Design Principles**:

1. **Automation Opportunities**: 
   - Auto-summarize long conversations to manage context limits
   - Auto-detect when context limit is near and offer to start fresh with summary
   - Auto-suggest follow-up questions based on AI's response
   - Auto-scroll to show latest message without manual intervention

2. **Simplification Opportunities**: 
   - Eliminate need to manually reference previous context (AI should automatically use relevant parts)
   - Streamline the send process (Enter key should always send without extra confirmation)
   - Hide advanced options unless explicitly requested
   - Reduce visual clutter in conversation thread

3. **Transition Smoothness**: 
   - Seamless flow from reading response to composing next message
   - Smooth scrolling when new messages appear
   - Natural progression through multiple exchanges
   - Easy to switch between reading history and sending new messages

4. **User Trust**: 
   - Clear indication that AI is processing and using context
   - Visual confirmation that messages are sent and received
   - Obvious progress during response generation
   - Reliable autosave of conversation (no manual save needed)

5. **Cognitive Load**: 
   - Don't require user to remember context limits or technical details
   - Conversation flows naturally without forcing decisions
   - Clear visual separation between messages
   - Easy to scan conversation history

---

## Related Flows

- [Create New Empty Chat](./new-chat-empty.md) - Start the conversation
- [Chat with Dataset Query Enabled](./rag-enabled-chat.md) - Add dataset information to context
- [Upload Document to Chat Context](./upload-document-to-chat.md) - Include files in conversation
- [Edit Chat Name Manually](./edit-chat-name-manual.md) - Name the conversation for easy reference
- [Export Chat as Text File](./export-chat-txt.md) - Save the conversation
- [Entourage Mode Manage Chat Personas](./persona-management.md) - Adjust AI behavior mid-conversation

---

## Technical References

**Knowledge Base Sections**:
- src/pages/chat.js - Main chat container
- src/components/chat/chat-message.js - Individual message rendering
- src/components/chat/chat-input.js - Message input and sending
- src/engines/llm.js - Context management and response generation
- src/components/chat/chat-message-loading-indicator.js - Progress display

**Key Components**:
- Conversation thread with message history
- Context window management (lookback size)
- Streaming response display
- Message action buttons (Redo, Copy, etc.)

---

## Version History

| Date | Version | Author | Changes |
|------|---------|--------|---------|
| 2025-10-04 | 1.1 | [Iternal Technologies](https://iternal.ai/airgapai) | Initial comprehensive documentation |

---

## Notes

**Important Considerations**:
- The AI maintains context only within a single chat; starting a new chat means starting from scratch
- Context limits vary by model (typically 2000-32000 tokens, configured in settings)
- Longer conversations may result in slower response times as the AI processes more context
- Each message sends the entire conversation history (up to context limit) to the AI
- Conversation is auto-saved continuously; no manual save action required

**Best Practices for Multi-Turn Conversations**:
- Be specific in follow-up questions to get best results
- Explicitly reference earlier points if many messages have passed
- Break complex topics into multiple focused exchanges rather than one massive query
- Start a new chat if you shift to a completely different topic
- Use the Redo button if you want alternative phrasings or approaches from the AI

**Common User Questions**:
- "How long can a conversation be?" - Technically unlimited, but AI context is limited to recent messages
- "Does the AI remember everything?" - It remembers messages within the context window (typically 10-50 messages depending on length and settings)
- "Can I go back and change an earlier message?" - No, but you can use Redo to regenerate responses
- "Why does the AI seem to forget things from early in the conversation?" - Context window limits; older messages drop out of context

