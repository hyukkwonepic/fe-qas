---
title: React Internals Deep Dive
---

## [The Overview of React internals](https://jser.dev/2023-07-11-overall-of-react-internals)

### [What are the four main phases of React internals as described in the overview?](https://jser.dev/2023-07-11-overall-of-react-internals#3-the-overview-of-react-internals)

The overview describes four main phases of React internals: Trigger, Schedule, Render, and Commit. These phases represent the high-level process of how React updates and renders components.

### [What happens in the "Trigger" phase of React internals?](https://jser.dev/2023-07-11-overall-of-react-internals#3-the-overview-of-react-internals)

The Trigger phase initiates all work in React, whether it's an initial mount or a re-render caused by a state hook. During this phase, React runtime is informed about which parts of the app need rendering. A task is created and ultimately sent to the Scheduler. This phase essentially creates a task that tells React what needs to be updated and how.

### [What is the purpose of the "Schedule" phase in React internals?](https://jser.dev/2023-07-11-overall-of-react-internals#3-the-overview-of-react-internals)

The Schedule phase revolves around the React Scheduler, which functions as a Priority Queue for processing tasks based on their priority. In this phase, various tasks such as rendering or running effects are scheduled. The Scheduler then executes these tasks using its internal mechanisms, ensuring that high-priority updates are processed first.

### [What occurs during the "Render" phase of React internals?](https://jser.dev/2023-07-11-overall-of-react-internals#3-the-overview-of-react-internals)

The Render phase is where the scheduled task is executed. This phase involves calculating a new Fiber Tree to represent the current state of the application and determining the necessary updates to apply to the host DOM. Due to concurrent mode, this phase can be interrupted and resumed, which adds to its complexity. It's like a process of figuring out what changes need to be made without actually making them yet.

### [What happens in the "Commit" phase of React internals?](https://jser.dev/2023-07-11-overall-of-react-internals#3-the-overview-of-react-internals)

The Commit phase is where the updates derived from the Render phase are applied to the host DOM. This includes actual DOM manipulation. Additionally, various types of Effects are processed during this phase. The Commit phase finalizes all changes and makes them visible to the user, completing the update process. This is the phase where the calculated changes are actually implemented and become visible.

---
