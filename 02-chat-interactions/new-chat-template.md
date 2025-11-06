# Create New Chat from Template

## Overview
**Flow ID**: `new-chat-template`  
**Category**: Chat Interactions  
**Estimated Duration**: 1-3 minutes  
**User Role**: All Users  
**Complexity**: Simple  

**Purpose**: This flow allows users to create a new chat conversation using a predefined template that includes pre-configured settings, personas, prompts, and behaviors. Templates streamline common workflows like creating social media content, generating proposals, or conducting multi-perspective analysis.

---

## Trigger

**What initiates this flow:**
- [x] User manually initiates

**Specific trigger**: User wants to use predefined chat configuration for specific task rather than starting from scratch.

---

## Prerequisites

**Before starting, users must have:**
- [x] Application running
- [x] At least one chat model available
- [x] Templates configured (default templates or custom ones)
- [x] For dataset templates: Active dataset available

---

## User Intent Analysis

### Primary Intent
Start a conversation pre-configured for a specific task or workflow using a template that includes appropriate settings, personas, and context.

### Secondary Intents
- Save time configuring settings
- Use proven configurations for common tasks
- Access specialized workflows (multi-persona, dataset-only, etc.)
- Ensure consistent approach for recurring tasks

---

## Step-by-Step Flow

### Main Path (Happy Path)

**Step 1: Navigate to New Chat**
- **User Action**: Click "Chat" in navigation (if no chat open) OR click "New Chat" button
- **System Response**: New chat creation screen displays
- **UI Elements Visible**: 
  - Large text input for starting conversation
  - Template selection buttons below input
  - Each template showing:
    - Name (e.g., "LinkedIn Post", "Sales Proposal", "Legal Review")
    - Brief description
  - Disclaimer text at bottom
- **Visual Cues**: Template buttons prominent and clickable

**Step 2: Review Available Templates**
- **User Action**: Read template names and descriptions
- **System Response**: Templates displayed
- **UI Elements Visible**: 
  - 3-6 template buttons (varies by configuration)
  - Common templates:
    - Social Media Content
    - Sales Proposal
    - Multi-Agent Team Discussion
    - Legal Review
    - Dataset Query Only (Pure Search)
  - Each button styled consistently
- **Visual Cues**: Buttons arranged in grid or list

**Step 3: Select Template**
- **User Action**: Click desired template button
- **System Response**: 
  - Chat creates with template configuration
  - If template requires dataset: Dataset query auto-enabled and locked
  - If template has multiple personas: All personas loaded
  - Chat interface loads
- **UI Elements Visible**: 
  - Loading indicator briefly
  - Chat interface appears
  - Template-specific settings visible:
    - May see multiple persona names
    - Dataset query may be enabled and locked
    - Special instructions or context may be shown
  - Text input ready for first message
- **Visual Cues**: 
  - Smooth transition to chat interface
  - Template indicator may show in header

**Step 4: Observe Template Configuration**
- **User Action**: Notice template-specific setup
- **System Response**: Chat displays with template configurations applied
- **UI Elements Visible**: 
  - Chat header shows chat name (may be template-based)
  - Subtitle may indicate template used
  - For multi-persona templates: Multiple persona indicators
  - For dataset templates: Dataset selector locked "ON"
  - Text input with template-appropriate placeholder
- **Visual Cues**: 
  - Template branding or indicators
  - Special UI elements based on template

**Step 5: Enter First Message**
- **User Action**: Type message appropriate for template purpose
- **System Response**: Text appears, send button enables
- **UI Elements Visible**: 
  - Text input with message
  - Template-specific controls active
  - Send button ready
- **Visual Cues**: Standard input behavior

**Step 6: Send Message**
- **User Action**: Click send or press Enter
- **System Response**: 
  - Template-specific processing:
    - Single persona: Standard response
    - Multi-persona: Multiple responses from different perspectives
    - Dataset-only: Search results without generation
  - Response(s) generate according to template
- **UI Elements Visible**: 
  - Loading indicators
  - Template-appropriate response format
  - Multiple persona responses if applicable
- **Visual Cues**: Template-specific response styling

**Final Step: Template Chat Active**
- **Success Indicator**: 
  - Chat created with template configuration
  - Settings match template
  - Can use immediately
  - Template behavior works as expected
- **System State Change**: 
  - New chat created
  - Template settings applied
  - Chat marked with template ID for reference
  - Can modify settings if needed
- **Next Possible Actions**: 
  - Continue conversation using template
  - Modify template settings if needed
  - Save chat for reuse
  - Create more template-based chats

---

## Alternative Paths & Strategies

### Strategy A: Type Then Select Template
**When to use**: User starts typing then realizes template would be better

**Steps**:
1. Start typing in text input
2. Before sending, click template button
3. Template loads and may preserve typed text
4. Continue with template configuration

**QA Note**: Text preservation not confirmed. May lose typed text when selecting template.

### Strategy B: Modify Template After Creation
**When to use**: Template is close but needs adjustment

**Steps**:
1. Create chat from template
2. Open advanced settings
3. Modify personas, prompts, or settings
4. Save changes
5. Use modified template configuration

---

## Error States & Recovery

### Error 1: Template Requires Dataset But None Available
**Cause**: Template needs dataset but no dataset is active  
**User Experience**: 
- Error message: "Dataset required for this template"
- Cannot use template
- May auto-navigate to dataset upload

**Recovery Steps**:
1. Upload and activate a dataset
2. Return to new chat
3. Select template again
4. Should work with dataset available

### Error 2: Template Configuration Fails
**Cause**: Template definition error or missing personas  
**User Experience**: 
- Template loads but behaves like standard chat
- Missing expected personas or settings
- Error notification may appear

**Recovery Steps**:
1. Manually configure desired settings
2. Check template configuration if access to settings
3. Use empty chat and configure manually
4. Report template issue

---

## Pain Points & Friction

**Identified Issues**:

1. **Cannot Preview Template Configuration**
   - **Impact**: Don't know what template does until created
   - **Frequency**: First-time template users
   - **Potential Improvement**: 
     - Show template details before creating
     - Preview personas and settings
     - Example conversations

2. **Cannot Customize Template Before Creation**
   - **Impact**: Must create then modify
   - **Frequency**: When template is close but not perfect
   - **Potential Improvement**: 
     - Template customization wizard
     - Choose template as starting point, then adjust
     - Save custom variations

3. **Limited Template Discovery**
   - **Impact**: Users may not know all available templates
   - **Frequency**: New users
   - **Potential Improvement**: 
     - Template gallery with screenshots
     - Search/filter templates
     - Categorize by use case

---

## Design Considerations

**Following Contextual Design Principles**:

1. **Automation Opportunities**: Auto-suggest templates based on user patterns
2. **Simplification Opportunities**: One-click chat creation
3. **User Trust**: Templates work reliably as described
4. **Cognitive Load**: Clear template purposes

---

## Related Flows

- [Create New Empty Chat](./new-chat-empty.md) - Alternative without template
- [Entourage Mode Manage Chat Personas](./persona-management.md) - Templates include personas
- [Chat with Dataset Query Enabled](./rag-enabled-chat.md) - Dataset templates

---

## Technical References

**Knowledge Base Sections**:
- src/components/chat/new-chat.js - Template selection
- src/localdb/workflow-config.js - Template definitions
- src/pages/chat.js - Chat creation

---

## Version History

| Date | Version | Author | Changes |
|------|---------|--------|---------|
| 2025-10-04 | 1.1 | [Iternal Technologies](https://iternal.ai/airgapai) | Initial comprehensive documentation |

---

## Notes

**Common Templates**:
- **Social Media**: Optimized for creating posts with emojis and viral content
- **Sales Proposals**: Professional business writing
- **Multi-Agent Team**: Simulates team discussion with multiple perspectives
- **Legal Review**: Multiple attorney personas for comprehensive analysis
- **Dataset Only**: Pure search without AI generation (fastest responses)

**Best Practices**:
- Choose template matching your task
- Understand template configuration before using
- Modify settings if template doesn't quite fit
- Create custom templates for recurring workflows

**Common User Questions**:
- "Can I modify templates?" - Can modify settings after creation, or ask admin to update template definition
- "How do I create custom templates?" - Typically requires admin access to configuration
- "What's the difference from empty chat?" - Templates pre-configure settings; empty chat requires manual setup

