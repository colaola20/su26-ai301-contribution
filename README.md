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

- **Commit showing reproduction:** [[Link to commit in your fork]](https://github.com/colaola20/Aroha)  
- **Screenshots/logs:** 
https://github.com/user-attachments/assets/bc30c95a-b374-4d14-9cd5-ea215ddf3855

- **My findings:** I was able to confirm that an issue exists just as it's described in issue's description.  

---

## Solution Approach

### Analysis

In src/app/page.tsx quate is set to hardcoded value "Focus is not about saying yes to the things you have to do. It's about saying no to the hundreds of other good ideas that there are." instead of null. Before useEffect fetches a random values, the hardcoded one is being displayed causing a glitch. The fetching of the quate depennds on todayISO which is also being redered using useEffect delaying quate's fetching time even further. Another problem is that quate logic lives in page-local component state which mounts/unmount on every tab navigation, so quate's fetching re-runs everytime, changing the quate.

### Proposed Solution

- move all quate fetching logic into src/context/TasksContext.tsx, so it will render only once and will be preserved through tab navigation.  
- initialize quate with null instaed of hardcoded value, so the React will know that it's not fetched yet.  
- Since fetching a quate is connected to todayISO value, all its setting logic needs to be moved to src/context/TasksContext.tsx as well.  
- in src/app/page.tsx instead of fetching quate, it will be pulled from useTasks() from src/context/TasksContext.tsx  
- When Today page is rendered and quate is null, an empty string will be shown until the random quate is fetched.  

### Implementation Plan

Using UMPIRE framework (adapted):

**Understand:** 
On loading/refreshing the Today tab, a hardcoded quote ("Focus is not about saying yes…") flashes for a half second before a fetched random quote replaces it, which looks glitchy. The user should see exactly one quote — a skeleton/blank while it loads, then the real quote.  

**Match:** 
TasksContext.tsx already centralizes shared state with the useState + useEffect + localStorage pattern and exposes it via useTasks(). The quote should follow that same provider-owned pattern so it persists across navigation, just like tasks and userProfile.  

**Plan:** 
- in TasksContext.tsx, add a quote state initialized to null  
- fetch it once in a useEffect([todayISO]), and expose it through the provider  
- In page.tsx, remove the local useState (:11) and quote useEffect (:63-74)  
- read quote from useTasks() and render an empty string while it's null  

**Implement:** [Link to your branch/commits as you work]

**Review:** 
No CONTRIBUTING.md exists in the repo, so I'll follow the conventions visible in git log — short, lowercase, imperative summaries describing the fix (e.g. "logout issue fixed", "time save fix"), and reference issue #10 in the PR. I'll self-check that no hardcoded quote can ever render and that the page still works when quote is null.  

**Evaluate:**
There's no test framework configured (no test script, no jest/vitest/playwright), so verification will be manual: hard-refresh the Today tab and switch tabs repeatedly, confirming only one quote ever appears (skeleton → quote, no flash, no re-fetch). 

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
