---
title: Debug
description: Debug and replay reference for voidcrawl v0.2.3
---

> Generated from voidcrawl `v0.2.3`. Only symbols in `__all__` are listed.

## `DebugSession` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/0.2.3/voidcrawl/debug.py#L219" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

Interactive step debugger for browser actions.

Queue actions via `add` (or `add_flow`), then call
`start` to execute them with an interactive debug control.
**Args:**

- `tab` `Tab` — The page or pooled tab to run actions against.
- `start_url` `str | None` — URL to navigate to when rewinding.  Required for
back/restart — if omitted those commands are disabled.
- `stepping` `bool` — If ``True`` (default), pause before every action.
If ``False``, run freely and only pause at breakpoints.
- `step_delay` `float` — Seconds to wait after each action in non-stepping
mode (ignored when paused at a prompt). Defaults to ``0.3``.
- `highlight` `bool` — Flash a CSS outline on selector-targeted elements
before executing the action. Defaults to ``True``.
- `nav_settle_secs` `float` — Seconds to wait after triggering a rewind
navigation before replaying actions.  Increase if pages
are slow to load. Defaults to ``0.5``.

### `add` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/0.2.3/voidcrawl/debug.py#L269" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`add(action: ActionNode) -> DebugSession`

Append a single action to the execution queue.
**Args:**

- `action` `ActionNode` — The action to enqueue.

**Returns:** `DebugSession` — This session, for chaining.

### `add_flow` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/0.2.3/voidcrawl/debug.py#L281" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`add_flow(flow: Flow) -> DebugSession`

Append every action from a `Flow` to the queue.
**Args:**

- `flow` `Flow` — The flow whose actions to enqueue.

**Returns:** `DebugSession` — This session, for chaining.

### `start` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/0.2.3/voidcrawl/debug.py#L295" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`start() -> FlowResult`

Run the queued actions with interactive debug control.

Prints a command prompt before each action (or only at
breakpoints, depending on *stepping*).  The user can type:

- **n** / **Enter** — execute the current action and advance
- **c** — continue running until the next breakpoint
- **b** — rewind one step (re-navigates and replays)
- **r** — restart from the beginning
- **l** — list all queued actions with position marker
- **h** — show history of executed actions and results
- **q** — quit the session early
**Returns:** `FlowResult` — Aggregated results collected so far.

## `vc_breakpoint` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/0.2.3/voidcrawl/debug.py#L148" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`vc_breakpoint() -> _T`

Mark an action class as a debugger breakpoint.

When a `DebugSession` encounters an action whose class is
marked with this decorator, it pauses execution regardless of
whether stepping mode is active.
**Args:**

- `cls` `_T` — The action class to mark.

**Returns:** `_T` — The same class, with an internal marker attribute set.

