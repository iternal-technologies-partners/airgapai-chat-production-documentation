# First-Time Application Setup

## Overview
**Flow ID**: `initial-setup`  
**Category**: Onboarding & Initial Setup  
**Estimated Duration**: 2-5 minutes (just wizard navigation)  
**User Role**: All Users (first time only)  
**Complexity**: Simple  

**Purpose**: This flow guides new users through the application for the first time, providing an optional interactive wizard that helps configure essential settings, upload their first model, and understand key features. Users can skip onboarding if they prefer to explore independently.

---

## Trigger

**What initiates this flow:**
- [ ] User manually initiates
- [x] System event (first launch with no prior configuration)

**Specific trigger**: Application launches for the first time on a new installation or after data reset, with no existing configuration detected.

---

## Prerequisites

**Before starting, users must have:**
- [x] Application installed and launched successfully
- [x] No previous configuration exists (fresh install)
- [x] Time to complete onboarding (or willingness to skip)

---

## User Intent Analysis

### Primary Intent
Get started with the application quickly by understanding essential features and completing minimum required configuration.

### Secondary Intents
- Learn what the application does
- Understand key features
- Set up basic working environment
- Avoid feeling lost or confused
- Get to productive use quickly

### Subintents
- Know what steps are needed for first use
- Understand what's optional vs. required
- Feel confident using the application
- Skip if already knowledgeable

---

## Step-by-Step Flow

### Main Path (Happy Path)

**Step 1: Application First Launch**
- **User Action**: Launch application for first time
- **System Response**: 
  - Application loads
  - System detects no prior configuration
  - Onboarding screen appears automatically
- **UI Elements Visible**: 
  - Welcome screen or splash
  - Onboarding wizard interface
  - Welcome message: "Welcome to AirgapAI" or similar
  - Brief description of application purpose
  - Two buttons:
    - "Get Started" or "Begin Setup" (primary, blue)
    - "Skip" or "I'll Explore on My Own" (secondary, gray)
  - Progress indicator showing steps (e.g., "Step 1 of 4")
- **Visual Cues**: 
  - Welcoming, clean design
  - Clear call-to-action
  - Professional appearance

**Step 2: Read Welcome Information**
- **User Action**: Read welcome text to understand what application does
- **System Response**: Information displayed
- **UI Elements Visible**: 
  - Application description
  - Key capabilities listed:
    - Offline AI conversations
    - Document processing and search
    - Complete privacy (no internet required)
  - Visual elements or graphics explaining features
- **Visual Cues**: 
  - Friendly, informative tone
  - Icons or illustrations

**Step 3: Choose to Continue or Skip**
- **User Action**: Decide whether to complete onboarding or skip
  - If continuing: Click "Get Started"
  - If skipping: See Alternative Path below
- **System Response**: 
  - If continuing: Advances to first onboarding step
  - If skipping: Goes directly to main application
- **UI Elements Visible**: 
  - Next step loads (if continuing)
  - Main application interface (if skipping)

**Step 4: Model Upload Step (if continuing)**
- **User Action**: Follow prompts to upload first AI model
- **System Response**: Model upload interface embedded in onboarding
- **UI Elements Visible**: 
  - Step header: "Step 1: Upload AI Model" or similar
  - Explanation of why model is needed
  - File upload interface
  - "Next" button (may be disabled until model uploaded)
  - "Skip this step" option
  - Progress: "Step 1 of 4"
- **Visual Cues**: 
  - Step number highlighted
  - Clear instructions
- **Note**: See onboarding-model-upload.md for detailed model upload during onboarding

**Step 5: Chat Style Selection Step**
- **User Action**: Choose preferred chat visual style from options
- **System Response**: Style options displayed
- **UI Elements Visible**: 
  - Step header: "Step 2: Choose Chat Style"
  - Multiple style preview cards (e.g., Professional, Casual, Teams-style, etc.)
  - Each showing sample conversation appearance
  - "Next" button
- **Visual Cues**: 
  - Visual previews of each style
  - Selectable cards
- **Note**: See onboarding-chat-style.md for detailed style selection

**Step 6: Optional Dataset Setup**
- **User Action**: Optionally upload or skip dataset configuration
- **System Response**: Dataset setup interface or skip option
- **UI Elements Visible**: 
  - Step header: "Step 3: Add Knowledge (Optional)"
  - Explanation of dataset feature
  - Upload option
  - "Skip" or "Do This Later" button prominent
  - "Next" button
- **Visual Cues**: "Optional" clearly marked
- **Note**: See onboarding-corpus-setup.md for detailed dataset setup

**Step 7: Completion Screen**
- **User Action**: Review setup summary
- **System Response**: Onboarding completion screen displays
- **UI Elements Visible**: 
  - Congratulations message
  - Summary of completed steps with checkmarks
  - "Start Using AirgapAI" or "Get Started" button
  - Possibly: Quick tips or getting started guide
- **Visual Cues**: 
  - Success indicators
  - Celebratory or welcoming design

**Step 8: Enter Main Application**
- **User Action**: Click "Start Using AirgapAI" or equivalent button
- **System Response**: 
  - Onboarding wizard closes
  - Main application interface loads
  - User brought to primary page (typically Chat or Home)
  - Onboarding marked as complete (won't show again)
- **UI Elements Visible**: 
  - Full application interface
  - Navigation menu
  - Main content area (chat, home, or dashboard)
  - All features available
- **Visual Cues**: 
  - Smooth transition from onboarding to main app
  - Normal application appearance

**Final Step: Onboarding Complete**
- **Success Indicator**: 
  - Onboarding wizard closed
  - In main application interface
  - Basic configuration complete (if steps were completed)
  - Can begin using application
  - Onboarding won't appear on next launch
- **System State Change**: 
  - Onboarding marked as complete in database
  - Configuration saved (model, style, etc. if set during onboarding)
  - User ready to use core features
  - Help resources available if needed
- **Next Possible Actions**: 
  - Start first chat conversation
  - Upload additional models or datasets
  - Explore features independently
  - Adjust settings as needed
  - Access help or documentation

---

## Alternative Path - Skip Onboarding

**Step 1: Choose to Skip**
- **User Action**: On welcome screen, click "Skip" or "I'll Explore on My Own"
- **System Response**: Confirmation dialog may appear

**Step 2: Confirm Skip**
- **User Action**: Confirm you want to skip setup
- **System Response**: 
  - Onboarding wizard closes
  - Main application loads
  - Onboarding marked as skipped
- **UI Elements Visible**: Main application interface

**Step 3: Application with No Configuration**
- **User Action**: Begin using application
- **System Response**: 
  - Most features may show "Not Configured" or require setup
  - No model loaded: Cannot chat until model uploaded
  - No dataset: Cannot use dataset query
- **UI Elements Visible**: 
  - Empty states or prompts to configure
  - Links to settings or upload areas

**Final Step: Skipped Successfully**
- **Success Indicator**: In main application, can configure manually
- **System State Change**: Onboarding skipped flag set
- **Next Actions**: Manually configure each feature as needed

---

## Error States & Recovery

### Error 1: Onboarding Crashes or Freezes
**Cause**: Application error during wizard  
**User Experience**: 
- Wizard stops responding
- Cannot proceed or go back
- Application may freeze

**Recovery Steps**:
1. Close and restart application
2. On restart, may resume onboarding or skip
3. If issue persists, choose "Skip" and configure manually
4. Report bug if consistently fails

### Error 2: Cannot Skip Onboarding
**Cause**: Skip button not working  
**User Experience**: 
- Click skip but nothing happens
- Stuck in onboarding

**Recovery Steps**:
1. Try completing onboarding steps
2. Look for alternative navigation
3. Refresh application
4. If persistent, indicates bug

**QA Note**: Skip should always be available. If not, design/implementation issue.

### Error 3: Onboarding Keeps Reappearing
**Cause**: Completion flag not saving  
**User Experience**: 
- Complete onboarding
- Next launch, shows onboarding again

**Recovery Steps**:
1. Complete or skip each time
2. Check if settings are persisting (other configuration)
3. May indicate database write issue
4. Report if consistent

---

## Pain Points & Friction

**Identified Issues**:

1. **May Feel Forced for Expert Users**
   - **Impact**: Users familiar with AI apps don't need basic explanation
   - **Frequency**: Expert users, repeat installations
   - **Potential Improvement**: 
     - Detect expertise level and offer abbreviated path
     - Very prominent skip option
     - "I'm familiar with AI assistants" fast track

2. **Optional Steps Not Clearly Optional**
   - **Impact**: Users may feel obligated to complete all steps
   - **Frequency**: Users wanting to explore first
   - **Potential Improvement**: 
     - Clearly mark optional vs. required
     - "Skip this step" vs. "Skip all"
     - Progress bar shows minimum required

3. **Cannot Return to Onboarding Later**
   - **Impact**: If skipped, can't access structured tutorial again
   - **Frequency**: Users who skip then want guidance
   - **Potential Improvement**: 
     - "Restart onboarding" option in settings or help
     - Separate tutorial mode
     - Help system replicating onboarding content

4. **No Progress Save During Onboarding**
   - **Impact**: If closed mid-onboarding, must start over
   - **Frequency**: Interruptions during first setup
   - **Potential Improvement**: 
     - Save progress between steps
     - Resume where left off
     - Mark completed steps

---

## Design Considerations

**Following Contextual Design Principles**:

1. **Automation Opportunities**: 
   - Auto-detect user expertise level
   - Auto-skip redundant steps if configuration detected
   - Auto-suggest common configurations based on system

2. **Simplification Opportunities**: 
   - Reduce to essential steps only
   - Make more steps optional
   - Provide "Quick Setup" vs. "Full Setup" paths

3. **Transition Smoothness**: 
   - Natural flow between steps
   - Clear progress indication
   - Smooth entry to main application

4. **User Trust**: 
   - Can skip without penalty
   - Completed steps actually improve experience
   - No forced configuration that can't be changed later

5. **Cognitive Load**: 
   - One concept per step
   - Clear next actions
   - Progress indication reduces uncertainty
   - Skip option reduces pressure

---

## Related Flows

- [Upload Model During Onboarding](./model-upload.md) - Embedded model upload
- [Select Chat Style During Onboarding](./chat-style-selection.md) - Style selection step
- [Setup Dataset During Onboarding](./corpus-setup.md) - Optional dataset step
- [Upload Large Language Model](../03-model-management/llm-model-upload.md) - Manual model upload if skipped

---

## Technical References

**Knowledge Base Sections**:
- src/components/onboarding/index.js - Onboarding orchestrator
- src/components/onboarding/layout.js - Onboarding UI components
- src/localdb/onboarding.js - Onboarding state persistence
- src/reducers/onboarding.js - Onboarding state management

**Key Components**:
- Multi-step wizard interface
- Progress tracking
- Step completion management
- Skip functionality

---

## Version History

| Date | Version | Author | Changes |
|------|---------|--------|---------|
| 2025-10-04 | 1.1 | [Iternal Technologies](https://iternal.ai/airgapai) | Initial comprehensive documentation |

---

## Notes

**Important Considerations**:
- Onboarding only appears once (first launch or after reset)
- All steps in onboarding can be done manually later if skipped
- Skipping onboarding doesn't prevent using application
- Onboarding configuration becomes default settings
- Can reset onboarding to see it again if needed (via settings or data reset)

**Onboarding Philosophy**:
- Designed to reduce initial friction, not force configuration
- Skip option always available (respects user autonomy)
- Steps ordered by importance (essential first, optional later)
- Educational: explains why each configuration matters
- Non-blocking: can use app even if minimal configuration

**Best Practices for New Users**:
- Complete at least model upload step (required for chat)
- Can skip dataset setup initially (explore chat first)
- Take time to understand each step's purpose
- Don't rush through without reading
- Know you can change all settings later

**For Experienced Users**:
- Skip onboarding and configure directly in settings
- Faster to skip and manually set up
- Onboarding designed for first-time AI app users

**Common User Questions**:
- "Do I have to complete onboarding?" - No, can skip entirely
- "Can I go back to a previous step?" - Yes, usually back button available
- "What if I skip?" - Can configure everything manually in Settings
- "Will onboarding appear again?" - No, marked complete after first time
- "Can I restart onboarding?" - Typically need to reset application data or settings

