# Contribution #1: Bug: Double Quote Flash on "Today" Tab load  


**Contribution Number:** 1  
**Student:** Olha Sorych  
**Issue:** [[GitHub issue link] ](https://github.com/MittalKeshav/Aroha/issues/10)  
**Status:** Phase I  Complete  
******* Phase II Complete 
******* Phase III In Progress  
******* Phase IV In Progress  

---

## Why I Chose This Issue

The issue and the final expectations are clear. Additionally, the author specified two different approaches on how a bug could be fixed. The tech stack is familiar to me or I worked with it in the past. The documentation is partially present and include information about the app, and some steps how to start with installation. The amout of work seams to be managebla with the duration of the assignment. The issue is new and was posted few hours ago, so nobody has claimed it yet. The author seams to be activly working on the project.  

---

## Understanding the Issue
Fix the bug where when "Today" page is rendered for a half a second a harcoded quate is shown ("Focus is not about saying yes...") before a randomly generated quate is loaded.  

### Problem Description

It's a bug where "Today" page shows hardcoded quate first before the random quate is loaded.  

### Expected Behavior

The random generated quate is shown once and is preserved when a user switches between different tabs.  

### Current Behavior

Currently the "Today" page shows harcoded quate before the random one when the page is loaded first time and not preserving the quate when a user switches to a different tabs.  

### Affected Components

src/app/page.tsx  
src/context/TasksContext.tsx  

---

## Reproduction Process

### Environment Setup

I forked and than cloned the repository. Than I followed the instranction from Readme file. It was missing steps for setting Firebase web app env variables, so when I run - npm run dev I got a FirebaseError. After I created a web project on Firebase, I got authontefication error. I enabled authentification though email/password, anonimus, and Google, and after that everything worked.

### Steps to Reproduce

1. Set up the project enviroment and run the project localy.
2. Sign up (since the app is only for authorized users)
3. Open Today tab
4. I observed that Today page renders hardcoded quate first before fetching a random quate.

### Reproduction Evidence

- **Commit showing reproduction:** [Link to commit in your fork]
- **Screenshots/logs:** <img width="1512" height="982" alt="Screenshot 2026-06-16 at 9 44 14 PM" src="https://github.com/user-attachments/assets/9ce3f886-338e-4538-b392-4f6b7e4eef62" />

- **My findings:** [What you discovered during reproduction]

---

## Solution Approach

### Analysis

[Your analysis of the root cause - what's causing the issue?]

### Proposed Solution

[High-level description of your fix approach]

### Implementation Plan

Using UMPIRE framework (adapted):

**Understand:** [Restate the problem]

**Match:** [What similar patterns/solutions exist in the codebase?]

**Plan:** [Step-by-step implementation plan]
1. [Modify file X to do Y]
2. [Add function Z]
3. [Update tests]

**Implement:** [Link to your branch/commits as you work]

**Review:** [Self-review checklist - does it follow the project's contribution guidelines?]

**Evaluate:** [How will you verify it works?]

---

## Testing Strategy

### Unit Tests

- [ ] Test case 1: [Description]
- [ ] Test case 2: [Description]
- [ ] Test case 3: [Description]

### Integration Tests

- [ ] Integration scenario 1
- [ ] Integration scenario 2

### Manual Testing

[What you tested manually and results]

---

## Implementation Notes

### Week [X] Progress

[What you built this week, challenges faced, decisions made]

### Week [Y] Progress

[Continue documenting as you work]

### Code Changes

- **Files modified:** [List]
- **Key commits:** [Links to important commits]
- **Approach decisions:** [Why you chose certain approaches]

---

## Pull Request

**PR Link:** [GitHub PR URL when submitted]

**PR Description:** [Draft or final PR description - much of the content above can be adapted]

**Maintainer Feedback:**
- [Date]: [Summary of feedback received]
- [Date]: [How you addressed it]

**Status:** [Awaiting review / Iterating / Approved / Merged]

---

## Learnings & Reflections

### Technical Skills Gained

[What you learned technically]

### Challenges Overcome

[What was hard and how you solved it]

### What I'd Do Differently Next Time

[Reflection on your process]

---

## Resources Used

- [Link to helpful documentation]
- [Tutorial or Stack Overflow post that helped]
- [GitHub issues or discussions that helped]
