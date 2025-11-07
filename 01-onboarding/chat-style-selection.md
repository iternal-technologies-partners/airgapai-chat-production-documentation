# Select LLM Chat Style During Onboarding

## Overview
**Flow ID**: `onboarding-chat-style`  
**Category**: Onboarding & Initial Setup  
**Estimated Duration**: 1-2 minutes  
**User Role**: All Users (first time)  
**Complexity**: Simple  

**Purpose**: Choose visual style for chat conversations from multiple preset themes. Each style offers different appearance, message layout, and visual design. Selection determines how chat messages look throughout the application.

---

## Trigger

**What initiates this flow:**
- [ ] User manually initiates
- [x] System event (reaches chat style step in onboarding)

**Specific trigger**: Onboarding wizard advances to style selection step (typically Step 2 or 3).

---

## Prerequisites

**Before starting, users must have:**
- [x] Onboarding wizard active
- [x] Progressed past earlier steps (or they were skipped)

---

## User Intent Analysis

### Primary Intent
Select preferred visual style for chat interface that matches personal aesthetic preferences and usability needs.

### Secondary Intents
- Personalize application appearance
- Choose style comfortable for extended reading
- Match personal or organizational branding preferences

---

## Step-by-Step Flow

### Main Path (Happy Path)

**Step 1: Style Selection Step Loads**
- **User Action**: Arrive at chat style selection step
- **System Response**: Style options display
- **UI Elements Visible**: 
  - Step header: "Choose Your Chat Style" or "Step 2: Select Appearance"
  - Progress indicator: "Step 2 of 4"
  - Explanation: "Select how you want conversations to look"
  - Grid of style preview cards (typically 6-9 options)
  - Each card shows:
    - Style name (e.g., "Professional", "Teams", "Creative")
    - Preview of chat appearance with sample messages
    - Selection indicator (radio button or border)
  - "Next" button
  - "Skip" option
- **Visual Cues**: 
  - Preview cards show actual chat appearance
  - Clear visual differences between styles

**Step 2: Review Style Options**
- **User Action**: Look through available styles and their previews
- **System Response**: Static display of options
- **UI Elements Visible**: 
  - Multiple style cards showing:
    - **Professional**: Clean, business-appropriate layout
    - **Teams**: Microsoft Teams-like appearance
    - **Creative**: Colorful, artistic design
    - **Space**: Dark theme with centered bubbles
    - **Daylight**: Light, airy theme
    - **Classic**: Traditional chat interface
    - Others depending on configuration
  - Each preview shows sample user and AI messages

**Step 3: Select Preferred Style**
- **User Action**: Click on preferred style card
- **System Response**: 
  - Selected card highlights
  - Other cards may dim slightly
  - Selection indicator appears (checkmark, border, or highlight)
  - "Next" button becomes enabled (if was disabled)
- **UI Elements Visible**: 
  - Selected style card with visual selection indicator
  - Other cards in unselected state
  - "Next" button active
- **Visual Cues**: 
  - Clear visual distinction of selected card
  - Border, background color, or checkmark indicates selection

**Step 4: Optional - Change Selection**
- **User Action**: Click different style card if changing mind
- **System Response**: 
  - Previous selection deselects
  - New card selects
  - Selection updates instantly
- **UI Elements Visible**: Selection indicator moves to new card

**Step 5: Proceed to Next Step**
- **User Action**: Click "Next" button
- **System Response**: 
  - Selection is saved
  - Onboarding advances to next step
  - Style will be applied to all chats
- **UI Elements Visible**: 
  - Next onboarding step loads
  - Progress updates: "Step 3 of 4"
- **Visual Cues**: Step transition animation

**Final Step: Chat Style Selected**
- **Success Indicator**: 
  - Style selected and saved
  - Progressed to next onboarding step
  - Style will be active when using chat
- **System State Change**: 
  - Chat style preference saved to settings
  - All future chats will use this style
  - Can be changed later in settings
- **Next Possible Actions**: 
  - Continue onboarding
  - Complete setup
  - Change style later in settings if desired

---

## Alternative Paths & Strategies

### Strategy A: Skip Style Selection
**When to use**: Don't care about appearance or want to explore later

**Steps**:
1. On style selection step, click "Skip"
2. Default style applied (typically "Professional")
3. Advance to next step
4. Can change in settings later

### Strategy B: Preview Multiple Styles Carefully
**When to use**: Want to make informed choice

**Steps**:
1. Click each style card to select
2. Carefully examine each preview
3. Compare message layouts, colors, spacing
4. Select favorite after reviewing all
5. Proceed

---

## Error States & Recovery

### Error 1: No Styles Available
**Cause**: Configuration error or missing style definitions  
**User Experience**: 
- Empty style selection area
- Error message

**Recovery Steps**:
1. Skip this step
2. Default style will be used
3. Can configure in settings later

**QA Note**: Style list should always be available. If empty, indicates system configuration issue.

### Error 2: Selection Doesn't Save
**Cause**: Database write error  
**User Experience**: 
- Select style, click next
- Style reverts to default later

**Recovery Steps**:
1. Change style in settings after onboarding
2. Selection should persist from settings

---

## Pain Points & Friction

**Identified Issues**:

1. **Limited Preview Size**
   - **Impact**: Small preview may not show full style characteristics
   - **Frequency**: Every style selection
   - **Potential Improvement**: 
     - Larger previews
     - Expandable preview mode
     - Interactive preview with sample content

2. **Cannot Try Before Committing**
   - **Impact**: Must select and complete onboarding to see style in actual use
   - **Frequency**: First-time users
   - **Potential Improvement**: 
     - Live preview mode
     - Test conversation with each style
     - "Try in demo" option

3. **No Guidance on Choosing**
   - **Impact**: Users unsure which style to pick
   - **Frequency**: Users unfamiliar with different layouts
   - **Potential Improvement**: 
     - Recommendations based on use case
     - Popularity indicators
     - "Most readable", "Best for mobile", etc. labels

4. **Difficult to Compare Side-by-Side**
   - **Impact**: Hard to compare features when previews are small
   - **Frequency**: Users choosing between similar styles
   - **Potential Improvement**: 
     - Side-by-side comparison view
     - Highlight differences
     - Feature comparison table

---

## Design Considerations

**Following Contextual Design Principles**:

1. **Automation Opportunities**: 
   - Auto-suggest style based on system theme (light/dark)
   - Recommend based on screen size
   - Default to most popular

2. **Simplification Opportunities**: 
   - Reduce to 3-4 core styles
   - Provide "Classic" default skip option
   - Hide advanced customization

3. **Transition Smoothness**: 
   - Smooth selection interaction
   - Preview accurately represents actual appearance
   - Easy to change mind

4. **User Trust**: 
   - Preview is accurate representation
   - Can change later in settings
   - Selection actually affects appearance

5. **Cognitive Load**: 
   - Visual previews reduce need to understand descriptions
   - Can make choice visually without technical knowledge
   - Optional step doesn't block progress

---

## Related Flows

- [First-Time Application Setup](./initial-setup.md) - Parent onboarding
- [Create New Empty Chat](../02-chat-interactions/new-chat-empty.md) - Uses selected style
- [Conduct Multi-Turn Conversation](../02-chat-interactions/multi-turn-conversation.md) - Display with chosen style

---

## Technical References

**Knowledge Base Sections**:
- src/components/onboarding/chat-style-preview.js - Style preview component
- src/components/onboarding/index.js - Onboarding coordinator
- src/constants/styles.js - Available chat styles
- src/localdb/settings.js - Style preference persistence

**Key Components**:
- Style preview cards with sample conversations
- Visual selection interface
- Style application system

---

## Version History

| Date | Version | Author | Changes |
|------|---------|--------|---------|
| 2025-10-04 | 1.1 | [Iternal Technologies](https://iternal.ai/airgapai) | Initial comprehensive documentation |

---

## Notes

**Available Chat Styles** (may vary by version):
- **Professional**: Clean, business-appropriate, neutral colors
- **Teams**: Microsoft Teams-inspired layout
- **Multicolor**: User messages color-coded for multi-user conversations
- **Creative**: Artistic, colorful design
- **Space**: Dark theme, centered messages
- **Daylight**: Light, minimalist design
- **Classic/OldSchool**: Traditional chat interface
- **Green Phosphorus**: Retro terminal-style
- **Nimbus**: Cloud-themed design

**Best Practices**:
- Choose style comfortable for extended reading
- Consider if others will view chats (professional vs. casual)
- Test style can be changed later (not permanent decision)
- Dark themes (Space) good for low-light environments
- Light themes (Professional, Daylight) good for bright environments

**Style Characteristics**:
- Some styles align messages left, others right or center
- Color schemes vary from neutral to vibrant
- Spacing and density differ between styles
- Some have visual flourishes, others minimal

**Common User Questions**:
- "Can I change style later?" - Yes, in settings
- "Does style affect functionality?" - No, only visual appearance
- "Can different chats have different styles?" - No, global setting affects all chats
- "Which style is most popular?" - Professional and Teams are common for work use
- "Can I customize colors?" - Limited; choose from preset styles

