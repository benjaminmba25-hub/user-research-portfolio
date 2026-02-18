# Project 2: Usability Testing - Government Service Prototype

## Project Overview

**Research Question:** Can users with accessibility needs successfully complete a Universal Credit "report a change" task using our redesigned prototype?

**Context:** This usability testing project evaluates a redesigned digital service for reporting changes to Universal Credit circumstances. The prototype incorporates findings from discovery research (Project 1) and aims to be more accessible for users with diverse needs.

**Approach:** GDS-aligned usability testing with a focus on accessibility and inclusive design.

**Timeline:** 2-week testing sprint (simulated)

---

## Background

### Why This Matters

From discovery research (Project 1), we learned that:
- 40% of UC users need additional support
- Many struggle with digital services due to accessibility barriers
- Users with screen readers, motor impairments, and cognitive differences often have poor experiences
- WCAG compliance is the minimum; true inclusivity requires going further

### GDS Accessibility Requirements

The Government Design Service requires all digital services to:
- Meet WCAG 2.1 AA standards as a minimum
- Work with assistive technologies (screen readers, voice control, etc.)
- Be tested with users who have access needs
- Follow inclusive design principles

### Prototype Being Tested

A redesigned "report a change" service that allows UC claimants to:
1. Select what type of change they need to report
2. Provide details of the change
3. Upload supporting evidence
4. Review and submit
5. Receive confirmation

**Key design improvements from previous version:**
- Simplified language (aiming for 9-year-old reading level)
- Clearer navigation and progress indicators
- Better error messages with specific guidance
- Improved screen reader compatibility
- Alternative formats for evidence upload

---

## Research Objectives

1. Can users complete the "report a change" task successfully?
2. Where do users encounter difficulties or confusion?
3. How accessible is the service for users with different access needs?
4. What improvements are needed before beta release?

---

## Research Methodology

### Methods Used

| Method | Purpose | Participants |
|--------|---------|--------------|
| **Moderated usability testing** | Observe task completion, identify issues | 8 participants |
| **Cognitive walkthrough** | Understand mental models and decision-making | Integrated into sessions |
| **Accessibility testing** | Evaluate with assistive technologies | 4 participants with access needs |
| **System Usability Scale (SUS)** | Quantify overall usability | All 8 participants |

### Participant Recruitment

**Target user groups (prioritising accessibility needs):**

| Participant | Profile | Access Needs | Assistive Technology |
|-------------|---------|--------------|---------------------|
| P1 | 34, visual impairment | Blind | Screen reader (JAWS) |
| P2 | 58, motor impairment | Difficulty using mouse | Keyboard only, voice control |
| P3 | 42, dyslexia | Reading difficulties | Text-to-speech, high contrast |
| P4 | 67, low digital confidence | Anxiety, memory issues | None (needs simple interface) |
| P5 | 29, deaf | Hearing impairment | None (visual focus) |
| P6 | 45, cognitive impairment | Processing difficulties | None (needs clear structure) |
| P7 | 52, colour blindness | Visual distinction issues | None (needs non-colour cues) |
| P8 | 38, no declared needs | Control group | Standard setup |

**Recruitment approach:**
- Partnered with RNIB, Scope, and Dyslexia Action
- Used accessibility-focused recruitment agencies
- Offered £75 thank-you payment (higher due to additional time/access needs)
- Provided options for remote or in-person testing
- Sent prototype link in advance for assistive tech setup

### Testing Environment

**For remote sessions:**
- Zoom with screen sharing
- UserTesting.com for unmoderated elements
- Participants used their own devices and assistive tech

**For in-person sessions:**
- Quiet room with adjustable lighting
- Range of devices (desktop, tablet, mobile)
- Assistive technology available (screen reader, magnifier)
- Observer room with live video feed

---

## Test Script

### Session Structure (60 minutes)

```
USABILITY TEST: "Report a Change" Prototype

Introduction (5 mins)
- Welcome and thanks
- Explain purpose: "We're testing the service, not you"
- Consent and recording permission
- "Please think aloud as you go"

Background Questions (5 mins)
- Tell me about your experience using digital services
- What assistive technology do you use day-to-day?
- Have you ever reported a change to your benefits online?

Task Scenarios (35 mins)

Task 1: Report a change of address
"Imagine you've just moved to a new flat. Your rent has increased from £500 to £650 per month. Please use this prototype to report this change to Universal Credit."

[Observe: Can they find "report a change"? Do they understand the questions?]

Task 2: Upload evidence
"The service is asking you to upload proof of your new rent. Please upload this document [provided]."

[Observe: Is upload process clear? Do they understand file requirements?]

Task 3: Review and submit
"Please review what you've entered and submit your change."

[Observe: Can they review successfully? Do they understand what happens next?]

Follow-up Questions (10 mins)
- What was the easiest part of that process?
- What was the most difficult?
- How would you rate the overall experience? (1-5)
- Any suggestions for improvement?

Closing (5 mins)
- Thank participant
- Confirm payment
- Offer to share findings
```

### Assistive Tech Specific Prompts

**For screen reader users:**
- "Please navigate to the 'report a change' link using your screen reader"
- "What does your screen reader tell you about this page?"
- "Were there any points where you got lost or confused?"

**For keyboard-only users:**
- "Please complete the task using only your keyboard"
- "Was everything reachable using Tab key?"
- "Did you notice any keyboard traps?"

---

## Findings

### Overall Success Rate

| Task | Completion Rate | Avg Time | Issues Found |
|------|-----------------|----------|--------------|
| Find "report a change" | 7/8 (88%) | 45 seconds | 1 critical |
| Complete change form | 6/8 (75%) | 4 minutes | 2 critical, 3 major |
| Upload evidence | 5/8 (63%) | 3 minutes | 2 critical, 2 major |
| Review and submit | 8/8 (100%) | 1 minute | 1 minor |

**Overall SUS Score:** 72/100 (Above average, but room for improvement)

---

### Critical Issues (Must Fix Before Release)

#### Issue 1: Screen Reader Users Cannot Access "Report a Change" Link

**Severity:** Critical  
**Impact:** Screen reader users cannot start the task

**What happened:**
- P1 (JAWS user) could not locate the "report a change" link
- The link was implemented as a `<div>` with JavaScript click handler
- Screen reader did not announce it as interactive

**Participant quote:**
> *"I'm tabbing through but I can't find where to report a change. It says 'Manage your account' but I don't hear anything about reporting changes."*

**WCAG Violation:** 4.1.2 Name, Role, Value (Level A)

**Recommendation:**
- Change `<div>` to proper `<a>` or `<button>` element
- Ensure proper ARIA labels
- Test with multiple screen readers (JAWS, NVDA, VoiceOver)

---

#### Issue 2: Error Messages Do Not Explain How to Fix the Problem

**Severity:** Critical  
|Impact:** Users don't know what to do when they make mistakes

**What happened:**
- P4 entered an invalid date format ("yesterday" instead of DD/MM/YYYY)
- Error message said: "Invalid date"
- No guidance on correct format
- Participant tried 3 different formats before giving up

**Participant quote:**
> *"It just says invalid. Invalid what? What should I put? I've tried everything I can think of."*

**WCAG Violation:** 3.3.1 Error Identification (Level A), 3.3.3 Error Suggestion (Level AA)

**Recommendation:**
- Error message: "Enter the date in this format: DD/MM/YYYY. For example: 15/06/2024"
- Provide inline validation with examples
- Consider date picker as alternative

---

#### Issue 3: Evidence Upload Does Not Accept Alternative Formats

**Severity:** Critical  
**Impact:** Users without digital documents cannot complete the task

**What happened:**
- P6 had a paper letter from landlord but no scanner
- Service only accepted PDF, JPG, PNG
- No option to post evidence or provide details verbally
- Participant could not complete the task

**Participant quote:**
> *"I've got the letter right here, but I don't know how to get it on the computer. Can't I just tell you what's in it?"*

**Recommendation:**
- Add option: "I cannot upload a file"
- Provide alternative: postal address, phone callback, or text description
- Consider photo upload from mobile as alternative

---

### Major Issues (Should Fix Before Release)

#### Issue 4: Progress Indicator is Unclear

**Severity:** Major  
**Impact:** Users don't know how long the process will take

**What happened:**
- 5/8 participants asked "how many more questions?"
- Progress bar showed "Step 2 of 4" but didn't explain what the steps were
- Users felt uncertain about time commitment

**Recommendation:**
- Add step names: "1. What changed → 2. Details → 3. Evidence → 4. Review"
- Show estimated time: "This takes about 5 minutes"

---

#### Issue 5: Language is Still Too Complex

**Severity:** Major  
**Impact:** Users with cognitive differences or low literacy struggle

**What happened:**
- P3 (dyslexia) struggled with "circumstances" and "declaration"
- P6 (cognitive impairment) didn't understand "supporting evidence"
- Reading level tested at 14 years, not target 9 years

**Examples:**
- "Change in circumstances" → "What has changed?"
- "Supporting evidence" → "Proof of the change"
- "Declaration" → "Confirm this is true"

**Recommendation:**
- Run all content through Hemingway Editor
- Aim for reading age 9-11
- User test simplified content

---

### Minor Issues (Fix If Time Allows)

#### Issue 6: Confirmation Page Does Not Explain What Happens Next

**Severity:** Minor  
**Impact:** Users uncertain about next steps

**What happened:**
- Confirmation page said "Change reported" but didn't explain timeline
- P5 asked: "When will I hear back? Will my money change?"

**Recommendation:**
- Add: "We'll review your change within 5 working days"
- Add: "You don't need to do anything else. We'll contact you if we need more information"

---

## Accessibility Audit Results

### WCAG 2.1 AA Compliance Check

| Criterion | Status | Notes |
|-----------|--------|-------|
| 1.1.1 Non-text Content | ❌ Fail | Upload icon has no alt text |
| 1.3.1 Info and Relationships | ❌ Fail | Progress steps not programmatically determined |
| 1.4.3 Contrast (Minimum) | ✅ Pass | All text meets 4.5:1 ratio |
| 2.1.1 Keyboard | ❌ Fail | "Report a change" not keyboard accessible |
| 2.4.3 Focus Order | ✅ Pass | Logical tab order |
| 3.3.1 Error Identification | ❌ Fail | Errors not clearly identified |
| 3.3.2 Labels or Instructions | ✅ Pass | Form fields have labels |
| 4.1.2 Name, Role, Value | ❌ Fail | Custom components lack ARIA |

**Overall Compliance:** 4/8 criteria passed (50%) - **Does not meet WCAG 2.1 AA**

---

## Recommendations Summary

### Before Beta Release (Must Do)

1. **Fix keyboard/screen reader access** - Change custom components to semantic HTML
2. **Rewrite error messages** - Provide specific guidance on how to fix errors
3. **Add alternative evidence options** - Support users who cannot upload files
4. **Fix alt text and ARIA labels** - Ensure all non-text content is accessible

### Before Live Release (Should Do)

5. **Improve progress indicator** - Show step names and estimated time
6. **Simplify language** - Reduce reading level to 9-11 years
7. **Add confirmation details** - Explain what happens next and when

### Nice to Have (Could Do)

8. **Add inline help** - Contextual guidance for complex questions
9. **Save and return** - Allow users to complete later
10. **Video demonstration** - Show how to upload evidence

---

## Research Outputs Delivered

| Output | Purpose | Format |
|--------|---------|--------|
| **Test plan** | Document approach, participants, script | PDF |
| **Test script** | Consistent session structure | Word doc |
| **Findings report** | Detailed issues and evidence | 15-slide deck |
| **Priority matrix** | Visualise issue severity | Excel/Miro |
| **Accessibility audit** | WCAG compliance check | Spreadsheet |
| **Recommendations deck** | Actionable next steps | 10-slide deck |
| **Video highlights** | Show real user struggles | 3-min clip |

---

## Reflection

### What I Learned

This simulated usability testing project reinforced:

- **Accessibility is not a checklist** - WCAG compliance is necessary but not sufficient; real user testing reveals issues automated tools miss
- **Assistive technology users are expert users** - They know their tools well; when they struggle, it's the service that's broken
- **Error messages are critical** - They can make or break the experience, especially for anxious users
- **Alternative paths matter** - Not everyone can use the "standard" route; inclusive design means options

### Skills Demonstrated

This project showcases:

- **Usability testing planning** - Designing a test with clear objectives and tasks
- **Accessibility expertise** - Testing with assistive technologies, WCAG knowledge
- **Inclusive recruitment** - Prioritising users with access needs
- **Issue prioritisation** - Using severity and impact to prioritise fixes
- **Clear communication** - Presenting findings in actionable formats
- **GDS alignment** - Following government usability testing standards

---

## Tools Used

- **Prototype:** Figma (built by design team)
- **Testing platform:** Zoom, UserTesting.com
- **Note-taking:** Word templates
- **Analysis:** Thematic coding, spreadsheet tracking
- **Reporting:** PowerPoint
- **Accessibility audit:** WAVE, axe DevTools

---

*This is a simulated usability testing project demonstrating user research skills and accessibility expertise. It is based on GDS usability testing standards and WCAG requirements, not actual government work.*
