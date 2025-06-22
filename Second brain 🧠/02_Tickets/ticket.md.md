---
ticket: CD-1234
tags: [jira, bug, frontend]
status: in-progress
---

# 🎫 CD-1234 – Tooltip Not Displaying

## Summary
Tooltip disappears when hovering over the icon in modal popups.

## Hypothesis
Tooltip lifecycle might be getting cut off when DOM is re-rendered.

## Fix Ideas
- Delay destroy event using `requestAnimationFrame`
- Use `onMouseOver` event binding instead of hover pseudo class

## Result
Fixed by deferring state cleanup in `useEffect`.

## Links
- PR: https://github.com/org/repo/pull/123
- Jira: https://clickdimensions.atlassian.net/browse/CD-1234
