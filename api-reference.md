---
title: API Reference
description: Full API reference for voidcrawl v0.2.2
version: v0.2.2
---

# API Reference

> Generated from voidcrawl `v0.2.2`. Only symbols in `__all__` are listed.

# Configuration

## `BrowserConfig` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/__init__.py#L92" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

Configuration for launching or connecting to a single browser instance.

Controls headless/headful mode, stealth patches, proxy routing, and
custom Chrome flags.  Pass an instance to `BrowserSession` or
embed one inside `PoolConfig`.
**Attributes:**

- `headless` `bool` — Run Chrome without a visible window. Defaults to ``True``.
- `stealth` `bool` — Apply anti-detection patches (navigator overrides, etc.).
Defaults to ``True``.
- `no_sandbox` `bool` — Disable the Chrome sandbox. Required in some Docker
environments. Defaults to ``False``.
- `proxy` `str | None` — Upstream HTTPS proxy URL, e.g. ``"http://proxy:8080"``.
- `chrome_executable` `str | None` — Path to a custom Chrome/Chromium binary.
When ``None``, the bundled Chromium discovery is used.
- `extra_args` `list[str]` — Additional command-line flags forwarded to Chrome.
- `ws_url` `str | None` — Connect to an **already-running** Chrome instance via its
WebSocket debugger URL instead of launching a new one.
- `debug` `bool` — Wrap pages in an interactive step-debugger.  When ``True``,
`BrowserSession.new_page` returns a
`voidcrawl.debug.DebugPage` and
`voidcrawl.actions.Flow.run` automatically pauses before
each action.  Requires the ``debug`` extra
(``uv add 'voidcrawl[debug]'``). Defaults to ``False``.
- `stepping` `bool` — Pause before every action when ``debug=True``.
Set to ``False`` to run freely without stopping.
Defaults to ``True``.
- `highlight` `bool` — Flash a red CSS outline on targeted elements when
``debug=True``. Defaults to ``True``.
- `step_delay` `float` — Seconds to wait between actions in non-stepping mode
when ``debug=True``. Defaults to ``0.3``.

### `model_dump` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/__init__.py#L97" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`model_dump() -> dict[str, object]`

## `PoolConfig` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/__init__.py#L151" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

Configuration for a pool of reusable browser tabs.

Controls how many Chrome processes to launch, how many concurrent tabs
each process may hold, and when tabs are recycled or evicted.
**Attributes:**

- `browsers` `int` — Number of Chrome processes in the pool. Defaults to ``1``.
- `tabs_per_browser` `int` — Maximum concurrent tabs **per** Chrome process.
Defaults to ``4``.
- `tab_max_uses` `int` — Hard-recycle a tab after this many navigations.
Prevents memory leaks in long-running crawls. Defaults to ``50``.
- `tab_max_idle_secs` `int` — Evict a tab that has been idle longer than this
many seconds. Defaults to ``60``.
- `acquire_timeout_secs` `int` — Maximum seconds to wait in
`BrowserPool.acquire` when all tabs are checked out.
``0`` means wait indefinitely. Defaults to ``30``.
- `chrome_ws_urls` `list[str]` — Pre-existing Chrome WebSocket debugger URLs.  When
non-empty, the pool connects to these instead of launching
new processes, and *browsers* is ignored.
- `browser` `BrowserConfig` — Shared `BrowserConfig` applied to every Chrome
process launched by the pool.

### `from_docker` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/__init__.py#L230" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`from_docker(headful: bool = False, host: str = 'localhost', ports: list[int] | None = None, tabs_per_browser: int = 4, check: bool = True) -> PoolConfig`

Build a `PoolConfig` for a VoidCrawl Docker container.

Selects the correct default ports for headless or headful mode and
optionally probes the Chrome endpoints before returning so you get
a clear error message if the container is not running.
**Args:**

- `headful` `bool` — Connect to the headful Docker container (ports
19222/19223).  Defaults to ``False`` (headless, ports
9222/9223).
- `host` `str` — Hostname where the Docker container is reachable.
Defaults to ``"localhost"``.
- `ports` `list[int] | None` — Override the default port list.  When ``None``, uses
``[9222, 9223]`` for headless or ``[19222, 19223]`` for
headful.
- `tabs_per_browser` `int` — Max concurrent tabs per Chrome process.
Defaults to ``4``.
- `check` `bool` — Probe each Chrome endpoint before returning and raise
`RuntimeError` with a setup hint if unreachable.
Defaults to ``True``.

**Returns:** `PoolConfig` — class:`PoolConfig` with ``chrome_ws_urls`` pre-populated.

**Raises:**

- `RuntimeError` — When ``check=True`` and a Chrome endpoint is
unreachable.  The error message includes the ``docker``
command needed to start the container.

### `from_env` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/__init__.py#L307" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`from_env() -> PoolConfig`

Build a `PoolConfig` from environment variables.

Reads the following variables (all optional):

+------------------------+---------------------------------+---------+
| Variable               | Description                     | Default |
+========================+=================================+=========+
| ``CHROME_WS_URLS``     | Comma-separated ws/http URLs    | —       |
+------------------------+---------------------------------+---------+
| ``BROWSER_COUNT``      | Chrome processes to launch      | 1       |
+------------------------+---------------------------------+---------+
| ``TABS_PER_BROWSER``   | Max concurrent tabs per browser | 4       |
+------------------------+---------------------------------+---------+
| ``TAB_MAX_USES``       | Hard recycle threshold          | 50      |
+------------------------+---------------------------------+---------+
| ``TAB_MAX_IDLE_SECS``  | Idle eviction timeout           | 60      |
+------------------------+---------------------------------+---------+
| ``ACQUIRE_TIMEOUT_SECS``| Max seconds for acquire()      | 30      |
+------------------------+---------------------------------+---------+
| ``CHROME_NO_SANDBOX``  | Set to ``"1"`` to disable       | —       |
+------------------------+---------------------------------+---------+
| ``CHROME_HEADLESS``    | Set to ``"0"`` for headful      | 1       |
+------------------------+---------------------------------+---------+
| ``AUTO_EVICT``         | Set to ``"0"`` to disable       | 1       |
+------------------------+---------------------------------+---------+
**Returns:** `PoolConfig` — A fully-populated `PoolConfig`.

### `from_profile` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/__init__.py#L194" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`from_profile(profile: ScaleProfile = 'balanced', env: str = 'auto') -> PoolConfig`

Build a `PoolConfig` from a resource-aware scale profile.

Measures current system resources and returns a pool configuration
tuned to the requested aggressiveness level.
**Args:**

- `profile` `ScaleProfile` — One of ``"minimal"``, ``"balanced"`` (default), or
``"advanced"``.
- `env` `str` — Environment hint passed to
`voidcrawl.scale.compute_scale`. ``"auto"`` (default)
detects automatically from system facts.

**Returns:** `PoolConfig` — class:`PoolConfig` sized for the detected resources.

**Raises:**

- `` — exc:`~voidcrawl.scale.InsufficientResourcesError`: When the
machine lacks the minimum resources to launch Chrome.

### `model_dump` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/__init__.py#L142" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`model_dump() -> dict[str, object]`

# Sessions & Pools

## `BrowserPool` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/__init__.py#L484" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

Pool of reusable browser tabs across one or more Chrome processes.

Manages a semaphore-bounded set of recycled tabs.  Tabs are navigated
to ``about:blank`` on release rather than closed, making subsequent
acquires near-instant.  Tabs are hard-recycled after
`PoolConfig.tab_max_uses` navigations and evicted after
`PoolConfig.tab_max_idle_secs` of inactivity.
**Args:**

- `config` `PoolConfig` — Pool sizing and browser launch options.

### `acquire` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/__init__.py#L546" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`acquire() -> _AcquireContext`

Check out a tab from the pool as an async context manager.

The tab is automatically returned to the pool when the context
exits, even on exception.
**Returns:** `_AcquireContext` — An async context manager yielding a `PooledTab`.

### `warmup` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/__init__.py#L563" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`warmup() -> None`

Pre-open tabs across all browser sessions.

Call after entering the pool context to eliminate cold-start
latency on the first `acquire` calls.

## `BrowserSession` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/__init__.py#L379" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

Async context manager wrapping a single Chromium instance via CDP.

Use as an ``async with`` block.  On entry the browser is launched (or
connected to, if `BrowserConfig.ws_url` is set); on exit the
process is terminated and resources are freed.
**Args:**

- `config` `BrowserConfig | None` — Browser launch options.  Defaults to
``BrowserConfig()`` (headless + stealth).

### `close` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/__init__.py#L463" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`close() -> None`

Shut down the browser process immediately.

Called automatically on ``__aexit__``; only needed if you want
to close the browser without leaving the ``async with`` block.

### `new_page` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/__init__.py#L421" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`new_page(url: str) -> Page`

Open a new tab and navigate to *url*.

When `BrowserConfig.debug` is ``True``, returns a
`voidcrawl.debug.DebugPage` wrapper that automatically
triggers interactive step-debugging when passed to
`voidcrawl.actions.Flow.run`.
**Args:**

- `url` `str` — The URL to load in the new tab.

**Returns:** `Page` — The new tab handle (or a debug wrapper when ``debug=True``).

### `version` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/__init__.py#L453" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`version() -> str`

Return the browser version string (e.g. ``"Chrome/126.0.6478.126"``).
**Returns:** `str` — The Chrome/Chromium product version reported by the browser.

## `Page` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/_ext.pyi#L280" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

A single browser tab created via `BrowserSession.new_page`.

### `click_element` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/_ext.pyi#L316" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`click_element(selector: str) -> None`

Click the first element matching *selector*.

### `close` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/_ext.pyi#L380" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`close() -> None`

Close this tab and release its resources.

### `content` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/_ext.pyi#L292" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`content() -> str`

Return the full page HTML.

### `delete_cookie` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/_ext.pyi#L340" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`delete_cookie(name: str, domain: str | None = None, path: str | None = None) -> None`

Delete a cookie by name, optionally scoped to a domain and path.

### `dispatch_key_event` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/_ext.pyi#L370" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`dispatch_key_event(event_type: str, key: str | None = None, code: str | None = None, text: str | None = None, modifiers: int | None = None) -> None`

Send a low-level CDP ``Input.dispatchKeyEvent``.

### `dispatch_mouse_event` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/_ext.pyi#L357" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`dispatch_mouse_event(event_type: str, x: float, y: float, button: str = 'left', click_count: int = 1, delta_x: float | None = None, delta_y: float | None = None, modifiers: int | None = None) -> None`

Send a low-level CDP ``Input.dispatchMouseEvent``.

### `evaluate_js` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/_ext.pyi#L301" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`evaluate_js(expression: str) -> object`

Evaluate a JavaScript *expression* and return the result.

### `get_cookies` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/_ext.pyi#L325" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`get_cookies() -> list[dict[str, Any]]`

Return all cookies matching the current page URL.

### `goto` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/_ext.pyi#L283" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`goto(url: str, timeout: float = 30.0) -> PageResponse`

Navigate to *url* and wait for network idle in one shot.

### `navigate` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/_ext.pyi#L286" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`navigate(url: str) -> None`

Navigate to *url* without waiting for any load event.

### `pdf_bytes` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/_ext.pyi#L307" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`pdf_bytes() -> bytes`

Render the page as a PDF and return the raw bytes.

### `query_selector` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/_ext.pyi#L310" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`query_selector(selector: str) -> str | None`

Return inner HTML of the first matching element.

### `query_selector_all` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/_ext.pyi#L313" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`query_selector_all(selector: str) -> list[str]`

Return inner HTML of every matching element.

### `screenshot_png` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/_ext.pyi#L304" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`screenshot_png() -> bytes`

Capture a full-page screenshot as PNG bytes.

### `set_cookie` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/_ext.pyi#L328" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`set_cookie(name: str, value: str, domain: str | None = None, path: str | None = None, secure: bool | None = None, http_only: bool | None = None) -> None`

Set a cookie on the current page.

### `set_headers` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/_ext.pyi#L322" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`set_headers(headers: dict[str, str]) -> None`

Set extra HTTP headers for subsequent requests.

### `title` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/_ext.pyi#L295" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`title() -> str | None`

Return the document title, or ``None``.

### `type_into` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/_ext.pyi#L319" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`type_into(selector: str, text: str) -> None`

Focus and type *text* into the first matching element.

### `url` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/_ext.pyi#L298" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`url() -> str | None`

Return the current page URL, or ``None``.

### `wait_for_navigation` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/_ext.pyi#L289" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`wait_for_navigation() -> None`

Block until the current navigation completes.

### `wait_for_network_idle` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/_ext.pyi#L354" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`wait_for_network_idle(timeout: float = 30.0) -> str | None`

Wait for network activity to settle.

### `wait_for_stable_dom` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/_ext.pyi#L349" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`wait_for_stable_dom(timeout: float = 10.0, min_length: int = 5000, stable_checks: int = 5) -> bool`

Wait until the DOM stabilises (stops changing).

## `PooledTab` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/_ext.pyi#L26" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

A tab checked out from a `voidcrawl.BrowserPool`.

Exposes the same page-interaction methods as `Page` but must
not be closed manually — return it to the pool via the async context
manager or `voidcrawl.BrowserPool.release`.
**Attributes:**

- `use_count` `int` — How many times this tab has been acquired (0 on first use).

### `click_element` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/_ext.pyi#L94" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`click_element(selector: str) -> None`

Click the first element matching *selector*.
**Args:**

- `selector` `str` — CSS selector string.

### `content` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/_ext.pyi#L61" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`content() -> str`

Return the full page HTML (``document.documentElement.outerHTML``).

### `delete_cookie` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/_ext.pyi#L144" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`delete_cookie(name: str, domain: str | None = None, path: str | None = None) -> None`

Delete a cookie by name, optionally scoped to a domain and path.
**Args:**

- `name` `str` — Cookie name.
- `domain` `str | None` — Cookie domain.
- `path` `str | None` — Cookie path.

### `dispatch_key_event` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/_ext.pyi#L212" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`dispatch_key_event(event_type: str, key: str | None = None, code: str | None = None, text: str | None = None, modifiers: int | None = None) -> None`

Send a low-level CDP ``Input.dispatchKeyEvent``.
**Args:**

- `event_type` `str` — ``"keyDown"``, ``"keyUp"``, ``"rawKeyDown"``, or ``"char"``.
- `key` `str | None` — DOM ``KeyboardEvent.key`` value (e.g. ``"Enter"``).
- `code` `str | None` — Physical key code (e.g. ``"KeyA"``).
- `text` `str | None` — Character to insert (e.g. ``"a"``).
- `modifiers` `int | None` — Bit field for modifier keys.

### `dispatch_mouse_event` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/_ext.pyi#L187" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`dispatch_mouse_event(event_type: str, x: float, y: float, button: str = 'left', click_count: int = 1, delta_x: float | None = None, delta_y: float | None = None, modifiers: int | None = None) -> None`

Send a low-level CDP ``Input.dispatchMouseEvent``.
**Args:**

- `event_type` `str` — One of ``"mousePressed"``, ``"mouseReleased"``,
``"mouseMoved"``, or ``"mouseWheel"``.
- `x` `float` — Horizontal page coordinate.
- `y` `float` — Vertical page coordinate.
- `button` `str` — ``"left"``, ``"right"``, or ``"middle"``.
- `click_count` `int` — Number of clicks (usually ``1``).
- `delta_x` `float | None` — Horizontal scroll delta (``mouseWheel`` only).
- `delta_y` `float | None` — Vertical scroll delta (``mouseWheel`` only).
- `modifiers` `int | None` — Bit field for modifier keys (Ctrl=1, Shift=2, etc.).

### `evaluate_js` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/_ext.pyi#L70" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`evaluate_js(expression: str) -> object`

Evaluate a JavaScript *expression* and return the result.
**Args:**

- `expression` `str` — JavaScript expression or IIFE string.

### `get_cookies` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/_ext.pyi#L116" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`get_cookies() -> list[dict[str, Any]]`

Return all cookies matching the current page URL.

Each cookie is a dict with keys: ``name``, ``value``, ``domain``,
``path``, ``expires``, ``size``, ``httpOnly``, ``secure``, ``session``, etc.

### `goto` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/_ext.pyi#L39" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`goto(url: str, timeout: float = 30.0) -> PageResponse`

Navigate to *url* and wait for network idle in one shot.
**Args:**

- `url` `str` — The URL to load.
- `timeout` `float` — Maximum seconds to wait for network idle.

**Returns:** `PageResponse` — class:`PageResponse` with HTML, final URL, status code, `PageResponse` — and redirect flag.

### `navigate` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/_ext.pyi#L51" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`navigate(url: str) -> None`

Navigate to *url* without waiting for any load event.
**Args:**

- `url` `str` — The URL to load.

### `query_selector` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/_ext.pyi#L80" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`query_selector(selector: str) -> str | None`

Return the inner HTML of the first element matching *selector*, or ``None``.
**Args:**

- `selector` `str` — CSS selector string.

### `query_selector_all` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/_ext.pyi#L87" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`query_selector_all(selector: str) -> list[str]`

Return the inner HTML of every element matching *selector*.
**Args:**

- `selector` `str` — CSS selector string.

### `screenshot_png` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/_ext.pyi#L77" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`screenshot_png() -> bytes`

Capture a full-page screenshot as PNG bytes.

### `set_cookie` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/_ext.pyi#L123" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`set_cookie(name: str, value: str, domain: str | None = None, path: str | None = None, secure: bool | None = None, http_only: bool | None = None) -> None`

Set a cookie on the current page.
**Args:**

- `name` `str` — Cookie name.
- `value` `str` — Cookie value.
- `domain` `str | None` — Cookie domain (default: current page domain).
- `path` `str | None` — Cookie path.
- `secure` `bool | None` — Mark as Secure.
- `http_only` `bool | None` — Mark as HttpOnly.

### `set_headers` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/_ext.pyi#L109" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`set_headers(headers: dict[str, str]) -> None`

Set extra HTTP headers for all subsequent requests from this tab.
**Args:**

- `headers` `dict[str, str]` — Header name-value pairs.

### `title` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/_ext.pyi#L64" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`title() -> str | None`

Return the document title, or ``None``.

### `type_into` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/_ext.pyi#L101" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`type_into(selector: str, text: str) -> None`

Focus the first element matching *selector* and type *text*.
**Args:**

- `selector` `str` — CSS selector string.
- `text` `str` — The text to type.

### `url` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/_ext.pyi#L67" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`url() -> str | None`

Return the current page URL, or ``None``.

### `wait_for_navigation` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/_ext.pyi#L58" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`wait_for_navigation() -> None`

Block until the current navigation completes.

### `wait_for_network_idle` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/_ext.pyi#L176" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`wait_for_network_idle(timeout: float = 30.0) -> str | None`

Wait for network activity to settle.
**Args:**

- `timeout` `float` — Maximum seconds to wait.

**Returns:** `str | None` — ``"networkIdle"`` or ``"networkAlmostIdle"`` on success, `str | None` — ``None`` on timeout.

### `wait_for_stable_dom` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/_ext.pyi#L159" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`wait_for_stable_dom(timeout: float = 10.0, min_length: int = 5000, stable_checks: int = 5) -> bool`

Wait until the DOM stabilises (stops changing).

Polls the HTML length repeatedly and resolves once it stays
constant across *stable_checks* consecutive checks.
**Args:**

- `timeout` `float` — Maximum seconds to wait.
- `min_length` `int` — Minimum HTML length before checking stability.
- `stable_checks` `int` — Consecutive unchanged polls required.

**Returns:** `bool` — ``True`` if the DOM stabilised, ``False`` on timeout.

# Action Framework

## `ActionNode` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/actions/_base.py#L92" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

Abstract base for all browser actions.

Subclass and implement `run` to create a custom action.  Use
`JsActionNode` when the action can be expressed as a single
JavaScript snippet; subclass ``ActionNode`` directly for CDP-level
actions that need `voidcrawl.actions.Tab.dispatch_mouse_event`
or `voidcrawl.actions.Tab.dispatch_key_event`.

### `run` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/actions/_base.py#L102" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`run(tab: Tab) -> object`

Execute this action against *tab*.
**Args:**

- `tab` `Tab` — Any object satisfying the `voidcrawl.actions.Tab`
protocol (e.g. `Page` or `PooledTab`).

**Returns:** `object` — The action result — type varies by action.

## `Flow` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/actions/_flow.py#L38" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

An ordered sequence of actions executed against a single tab.

Actions run sequentially in the order added; each result is captured
in the returned `FlowResult`.
**Args:**

- `actions` `list[ActionNode] | None` — Initial list of actions.  May be ``None`` or omitted to
start with an empty flow and use `add`.

### `add` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/actions/_flow.py#L72" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`add(action: ActionNode) -> Flow`

Append an action and return *self* for chaining.
**Args:**

- `action` `ActionNode` — The action to append.

**Returns:** `Flow` — This instance, for builder-style chaining.

### `run` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/actions/_flow.py#L90" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`run(tab: Tab) -> FlowResult`

Execute all actions sequentially against *tab*.

When *tab* is a `voidcrawl.debug.DebugPage` (i.e. the
session was started with ``BrowserConfig(debug=True)``), execution
is automatically routed through an interactive
`voidcrawl.debug.DebugSession` instead of running silently.
**Args:**

- `tab` `Tab` — Any object satisfying the ``Tab`` protocol.

**Returns:** `FlowResult` — One result per action.

## `FlowResult` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/actions/_flow.py#L20" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

Aggregated result of a `Flow` execution.
**Attributes:**

- `results` `list[object]` — Ordered list of return values, one per action.
- `last` `object` — The return value of the final action, or ``None`` for
empty flows (read-only property).

## `JsActionNode` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/actions/_base.py#L119" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

Action executed by evaluating a JavaScript snippet in the page.

Subclasses set the ``js`` class attribute (via `load_js` or
`inline_js`) and store their parameters as instance attributes
in ``__init__``.  At execution time, all instance attributes are
serialised to JSON and injected as the ``__params`` object visible
inside the snippet.

By default `params` returns ``vars(self)``; override it only
if you need to transform or filter attributes.

### `params` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/actions/_base.py#L146" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`params() -> dict[str, Any]`

Return the parameters injected as ``__params`` in the JS snippet.

Defaults to ``vars(self)``.  Override to transform, rename, or
filter attributes before they reach JavaScript.
**Returns:** `dict[str, Any]` — A JSON-serialisable dict of parameter names to values.

### `run` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/actions/_base.py#L157" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`run(tab: JsTab) -> object`

Evaluate the JS snippet in *tab* with the current `params`.
**Args:**

- `tab` `JsTab` — Any object satisfying `voidcrawl.actions.JsTab`.

**Returns:** `object` — The JSON-deserialised return value from the snippet.

## `JsSource` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/actions/_base.py#L21" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

Immutable wrapper around a JavaScript snippet string.

Created via `load_js` (file-based) or `inline_js`
(string literal).  Used as the ``js`` class attribute on
`JsActionNode` subclasses.
**Args:**

- `js` `str` — Raw JavaScript source code.

## `JsTab` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/actions/_protocol.py#L13" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

Minimal protocol for JavaScript-only actions.

Any object with an async ``evaluate_js`` method satisfies this
protocol — including `Page`, `PooledTab`, and test
mocks.  Used by `voidcrawl.actions.JsActionNode`.

### `evaluate_js` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/actions/_protocol.py#L22" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`evaluate_js(expression: str) -> object`

Evaluate a JavaScript *expression* in the page and return the result.
**Args:**

- `expression` `str` — JavaScript expression or IIFE string.

**Returns:** `object` — The JSON-deserialised return value from the browser.

## `Tab` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/actions/_protocol.py#L34" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

Full protocol covering JS evaluation **and** CDP input commands.

Both `Page` and `PooledTab` satisfy this protocol.
CDP-level actions (e.g. `voidcrawl.actions.CdpClick`) require
this protocol rather than the simpler `JsTab`.

### `dispatch_key_event` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/actions/_protocol.py#L69" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`dispatch_key_event(event_type: str, key: str | None = None, code: str | None = None, text: str | None = None, modifiers: int | None = None) -> None`

Send a low-level CDP ``Input.dispatchKeyEvent``.
**Args:**

- `event_type` `str` — ``"keyDown"``, ``"keyUp"``, ``"rawKeyDown"``, or
``"char"``.
- `key` `str | None` — DOM ``KeyboardEvent.key`` value (e.g. ``"Enter"``).
- `code` `str | None` — Physical key code (e.g. ``"KeyA"``).
- `text` `str | None` — Character to insert (e.g. ``"a"``).
- `modifiers` `int | None` — Bit field for modifier keys.

### `dispatch_mouse_event` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/actions/_protocol.py#L43" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`dispatch_mouse_event(event_type: str, x: float, y: float, button: str = 'left', click_count: int = 1, delta_x: float | None = None, delta_y: float | None = None, modifiers: int | None = None) -> None`

Send a low-level CDP ``Input.dispatchMouseEvent``.
**Args:**

- `event_type` `str` — One of ``"mousePressed"``, ``"mouseReleased"``,
``"mouseMoved"``, or ``"mouseWheel"``.
- `x` `float` — Horizontal page coordinate.
- `y` `float` — Vertical page coordinate.
- `button` `str` — Mouse button — ``"left"``, ``"right"``, or ``"middle"``.
- `click_count` `int` — Number of clicks (usually ``1``).
- `delta_x` `float | None` — Horizontal scroll delta (``mouseWheel`` only).
- `delta_y` `float | None` — Vertical scroll delta (``mouseWheel`` only).
- `modifiers` `int | None` — Bit field for modifier keys (Ctrl=1, Shift=2, etc.).

## `inline_js` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/actions/_base.py#L71" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`inline_js(code: str) -> JsSource`

Create a `JsSource` from an inline string literal.
**Args:**

- `code` `str` — Raw JavaScript source code.

**Returns:** `JsSource` — The wrapped JavaScript source.

## `load_js` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/actions/_base.py#L51" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`load_js(path: str | Path) -> JsSource`

Load JavaScript from a ``.js`` file on disk.

Absolute paths are used as-is.  Relative paths are resolved from the
**caller's** source file, so ``load_js("click_at.js")`` works when
the ``.js`` lives next to the calling ``.py``.
**Args:**

- `path` `str | Path` — Filesystem path to the ``.js`` file.

**Returns:** `JsSource` — The loaded JavaScript source.

# Built-in Actions

## `Attr` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/schema.py#L145" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`Attr(css: str, attr: str, sanitize: Callable[[str | None], str | None] | None = None) -> Any`

Declare a field extracted from an element attribute.

CSS selectors are validated at class-definition time; strings
containing ``<``, ``>``, or null bytes raise `ValueError`.
**Args:**

- `css` `str` — CSS sub-selector relative to the root element.  Pass
``""`` to target the root element itself.
- `attr` `str` — HTML attribute name (e.g. ``"href"``, ``"src"``).
- `sanitize` `Callable[[str | None], str | None] | None` — Optional callable applied to the extracted value
before Pydantic validation.  Use `safe_url` to block
dangerous URL schemes on link/image fields.

**Returns:** `Any` — A Pydantic ``FieldInfo`` carrying the selector, attribute, and `Any` — sanitizer metadata.

## `CdpClick` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/actions/builtin/click.py#L60" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

Click at ``(x, y)`` via CDP ``Input.dispatchMouseEvent``.

Sends a ``mousePressed`` followed by ``mouseReleased``.  More
realistic than JS-level clicks — useful for pages that inspect
event coordinates.
**Args:**

- `x` `float` — Horizontal page coordinate.
- `y` `float` — Vertical page coordinate.
- `button` `str` — Mouse button — ``"left"``, ``"right"``, or ``"middle"``.

### `run` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/actions/builtin/click.py#L78" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`run(tab: Tab) -> None`

Dispatch ``mousePressed`` then ``mouseReleased`` at ``(x, y)``.
**Args:**

- `tab` `Tab` — Tab-like object to send the click events to.

## `CdpClickAndHold` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/actions/builtin/click.py#L95" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

Mouse-down, hold for *duration_ms*, then mouse-up via CDP.

Useful for triggering long-press menus or drag initialisation.
**Args:**

- `x` `float` — Horizontal page coordinate.
- `y` `float` — Vertical page coordinate.
- `duration_ms` `int` — How long to hold the button, in milliseconds.
- `button` `str` — Mouse button — ``"left"``, ``"right"``, or ``"middle"``.

### `run` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/actions/builtin/click.py#L115" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`run(tab: Tab) -> None`

Press, hold for *duration_ms*, then release at ``(x, y)``.
**Args:**

- `tab` `Tab` — Tab-like object to send the mouse events to.

## `CdpHover` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/actions/builtin/hover.py#L32" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

Move the virtual mouse cursor to ``(x, y)`` via CDP.

Sends a ``mouseMoved`` event.  Unlike `Hover`, this moves
the actual CDP cursor position, which is needed for subsequent
`CdpClick` calls to land correctly.
**Args:**

- `x` `float` — Horizontal page coordinate.
- `y` `float` — Vertical page coordinate.

### `run` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/actions/builtin/hover.py#L48" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`run(tab: Tab) -> None`

Dispatch a ``mouseMoved`` event to ``(x, y)``.
**Args:**

- `tab` `Tab` — Tab-like object to send the hover event to.

## `CdpScroll` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/actions/builtin/scroll.py#L49" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

Scroll via a CDP ``mouseWheel`` event fired at ``(x, y)``.

For most use cases prefer the convenience subclasses
`CdpScrollDown`, `CdpScrollUp`,
`CdpScrollLeft`, and `CdpScrollRight`.
**Args:**

- `x` `float` — Horizontal page coordinate for the wheel event origin.
- `y` `float` — Vertical page coordinate for the wheel event origin.
- `delta_x` `float` — Horizontal scroll amount (positive = right).
- `delta_y` `float` — Vertical scroll amount (positive = down).

### `run` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/actions/builtin/scroll.py#L71" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`run(tab: Tab) -> None`

Dispatch a ``mouseWheel`` event at ``(x, y)``.
**Args:**

- `tab` `Tab` — Tab-like object to send the scroll event to.

## `CdpScrollDown` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/actions/builtin/scroll.py#L92" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

Scroll **down** by *pixels* at ``(x, y)`` via CDP.
**Args:**

- `pixels` `float` — Distance to scroll in pixels. Defaults to ``100``.
- `x` `float` — Horizontal origin for the wheel event.
- `y` `float` — Vertical origin for the wheel event.

## `CdpScrollLeft` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/actions/builtin/scroll.py#L140" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

Scroll **left** by *pixels* at ``(x, y)`` via CDP.
**Args:**

- `pixels` `float` — Distance to scroll in pixels. Defaults to ``100``.
- `x` `float` — Horizontal origin for the wheel event.
- `y` `float` — Vertical origin for the wheel event.

## `CdpScrollRight` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/actions/builtin/scroll.py#L124" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

Scroll **right** by *pixels* at ``(x, y)`` via CDP.
**Args:**

- `pixels` `float` — Distance to scroll in pixels. Defaults to ``100``.
- `x` `float` — Horizontal origin for the wheel event.
- `y` `float` — Vertical origin for the wheel event.

## `CdpScrollUp` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/actions/builtin/scroll.py#L108" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

Scroll **up** by *pixels* at ``(x, y)`` via CDP.
**Args:**

- `pixels` `float` — Distance to scroll in pixels. Defaults to ``100``.
- `x` `float` — Horizontal origin for the wheel event.
- `y` `float` — Vertical origin for the wheel event.

## `CdpTypeText` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/actions/builtin/input.py#L84" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

Type *text* character-by-character via CDP ``Input.dispatchKeyEvent``.

Each character produces a ``keyDown``/``keyUp`` pair.  This is more
realistic than `SetInputValue` and triggers per-keystroke
event listeners.
**Args:**

- `text` `str` — The string to type.

### `run` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/actions/builtin/input.py#L98" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`run(tab: Tab) -> None`

Dispatch ``keyDown``/``keyUp`` pairs for each character in *text*.
**Args:**

- `tab` `Tab` — Tab-like object to send the key events to.

## `ClearInput` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/actions/builtin/input.py#L44" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

Clear an input field and fire an ``input`` event via JS.
**Args:**

- `selector` `str` — CSS selector targeting the ``<input>`` or ``<textarea>``.

## `ClickAt` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/actions/builtin/click.py#L22" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

Click the element at page coordinates ``(x, y)`` via JS events.

Uses ``document.elementFromPoint`` to resolve the target and
dispatches synthetic mouse events.
**Args:**

- `x` `int` — Horizontal page coordinate (pixels from left).
- `y` `int` — Vertical page coordinate (pixels from top).

## `ClickElement` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/actions/builtin/click.py#L40" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

Click the first element matching a CSS *selector* via JS.

Raises a JS ``Error`` if no element matches.
**Args:**

- `selector` `str` — CSS selector string (e.g. ``"#submit-btn"``).

## `CollectNetworkRequests` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/actions/builtin/network.py#L48" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

Retrieve all network entries captured by `InstallNetworkObserver`.

Returns a list of dicts, each containing:

- ``name`` — the full URL of the request
- ``type`` — the initiator type (``"script"``, ``"img"``, ``"fetch"``, etc.)
- ``duration`` — round-trip time in milliseconds
- ``size`` — transfer size in bytes (0 if unavailable)

Pass ``clear=True`` to reset the log after collection.

## `GetAttribute` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/actions/builtin/dom.py#L21" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

Read an HTML attribute from the first matching element.

Returns ``None`` if the element is not found.  The result is
available as the return value of `run` (``str | None``).
**Args:**

- `selector` `str` — CSS selector targeting the element.
- `attr` `str` — Attribute name (e.g. ``"href"``, ``"data-id"``).

### `run` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/actions/builtin/dom.py#L26" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`run(tab: JsTab) -> str | None`

## `GetText` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/actions/builtin/dom.py#L43" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

Read ``textContent`` from the first matching element.

Returns ``None`` if the element is not found.  The result is
available as the return value of `run` (``str | None``).
**Args:**

- `selector` `str` — CSS selector targeting the element.

### `run` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/actions/builtin/dom.py#L37" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`run(tab: JsTab) -> str | None`

## `Hover` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/actions/builtin/hover.py#L16" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

Dispatch ``mouseenter`` + ``mouseover`` on an element via JS.

Triggers CSS ``:hover`` styles and JS hover handlers without
moving the CDP-level cursor.
**Args:**

- `selector` `str` — CSS selector targeting the element to hover.

## `InstallNetworkObserver` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/actions/builtin/network.py#L12" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

Install a ``PerformanceObserver`` that records network requests.

Call this **after** navigation completes (e.g. after
``wait_for_network_idle``). The observer uses ``buffered: true``
to retroactively capture all resource entries from the current
navigation, plus any future requests.

Use `CollectNetworkRequests` to retrieve the captured entries.

The observer stores entries on ``window.__vc_network_log``.

### `params` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/actions/builtin/network.py#L44" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`params() -> dict[str, object]`

## `PageResponse` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/_ext.pyi#L10" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

Result of `Page.goto` / `PooledTab.goto`.
**Attributes:**

- `html` `str` — Full outer HTML after network idle.
- `url` `str` — Final URL after any redirects.
- `status_code` `int | None` — HTTP status of the last response, or ``None``
when served from cache / service worker.
- `redirected` `bool` — ``True`` when at least one HTTP redirect occurred.

## `QueryAll` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/actions/builtin/dom.py#L63" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

Query all elements matching *selector* and extract fields from each.

Each entry in *fields* maps a result key to either:

* a CSS sub-selector string — the matched element's ``textContent``
  (trimmed) is returned, or ``None`` if nothing matches.
* a ``(sub_selector, attr)`` tuple — the named attribute of the
  matched element is returned, or ``None`` if nothing matches.

Pass an empty string ``""`` as the sub-selector to target the root
element itself rather than a descendant.

Pass a `voidcrawl.schema.Schema` subclass as *fields*
to receive typed model instances instead of raw dicts.
**Args:**

- `selector` `str` — CSS selector for the root elements to iterate over.
- `fields` `dict[str, str | tuple[str, str]] | type[Schema]` — Mapping of result key → sub-selector or
``(sub_selector, attribute)`` tuple, **or** a
`voidcrawl.schema.Schema` subclass whose field
declarations are used automatically.

Example — raw dicts::

    QueryAll(
        ".article",
        {"title": "h2", "url": ("a", "href"), "date": ".byline"},
    )

Example — typed Schema::

    class Article(vc.Schema):
        title: str = vc.Text("h2")
        url: str | None = vc.Attr("a", "href")


    QueryAll(".article", Article)

### `params` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/actions/builtin/dom.py#L147" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`params() -> dict[str, Any]`

### `run` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/actions/builtin/dom.py#L150" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`run(tab: JsTab) -> list[_T]`

## `ScaleReport` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/scale.py#L139" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

Computed pool recommendations for a profile and resource snapshot.

### `print_report` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/scale.py#L173" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`print_report() -> None`

Print a human-readable summary. Uses rich markup if available.

### `to_dict` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/scale.py#L169" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`to_dict() -> dict[str, object]`

Serialise to a JSON-compatible dict (for ``--json`` scripted mode).

### `to_pool_config` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/scale.py#L157" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`to_pool_config() -> PoolConfig`

Convert to a `voidcrawl.PoolConfig` ready for
`voidcrawl.BrowserPool`.

## `Schema` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/schema.py#L178" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

Base class for declarative DOM extraction models.

Subclass this and annotate fields with `Text` or `Attr`
to declare how each field is extracted from the DOM.  Pass the
subclass to `voidcrawl.actions.QueryAll` to receive typed
instances instead of raw dicts.

Example::

    class Article(Schema):
        headline: str = Text("h2")
        url: str | None = Attr("a", "href", sanitize=safe_url)
        excerpt: str | None = Text(".summary", sanitize=strip_tags)

## `ScrollBy` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/actions/builtin/scroll.py#L34" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

Scroll the window by a relative offset via ``window.scrollBy``.
**Args:**

- `dx` `int` — Horizontal delta in pixels (positive = right). Defaults to ``0``.
- `dy` `int` — Vertical delta in pixels (positive = down). Defaults to ``0``.

## `ScrollTo` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/actions/builtin/scroll.py#L19" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

Scroll the window to an absolute position via ``window.scrollTo``.
**Args:**

- `x` `int` — Horizontal scroll offset in pixels. Defaults to ``0``.
- `y` `int` — Vertical scroll offset in pixels. Defaults to ``0``.

## `SelectOption` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/actions/builtin/input.py#L63" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

Select a ``<select>`` option by value and fire a ``change`` event.
**Args:**

- `selector` `str` — CSS selector targeting the ``<select>`` element.
- `value` `str` — The ``value`` attribute of the ``<option>`` to select.

## `SetAttribute` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/actions/builtin/dom.py#L157" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

Set an HTML attribute on the first matching element.

Raises a JS ``Error`` if no element matches the selector.
**Args:**

- `selector` `str` — CSS selector targeting the element.
- `attr` `str` — Attribute name to set.
- `value` `str` — Attribute value to assign.

### `run` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/actions/builtin/dom.py#L91" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`run(tab: JsTab) -> None`

## `SetInputValue` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/actions/builtin/input.py#L18" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

Bulk-set an input's value and fire ``input``/``change`` events.

This does **not** simulate individual keystrokes — use
`CdpTypeText` for realistic per-character typing.
**Args:**

- `selector` `str` — CSS selector targeting the ``<input>`` or ``<textarea>``.
- `text` `str` — The value to assign.

## `Text` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/schema.py#L111" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`Text(css: str, sanitize: Callable[[str | None], str | None] | None = None) -> Any`

Declare a field extracted from an element's ``textContent``.

The *css* string is a sub-selector relative to the root element
matched by `voidcrawl.actions.QueryAll`'s ``selector``
argument.  Pass ``""`` to target the root element itself.

CSS selectors are validated at class-definition time; strings
containing ``<``, ``>``, or null bytes raise `ValueError`.
**Args:**

- `css` `str` — CSS sub-selector whose ``textContent`` (trimmed) is used
as the field value.  ``None`` is returned when no element
matches.
- `sanitize` `Callable[[str | None], str | None] | None` — Optional callable applied to the extracted value
before Pydantic validation.  Use `safe_url` or
`strip_tags`, or supply your own
``(str | None) -> str | None`` function.

**Returns:** `Any` — A Pydantic ``FieldInfo`` carrying the selector and sanitizer `Any` — metadata.

## `WaitForSelector` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/actions/builtin/wait.py#L16" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

Poll until a CSS selector matches an element, with timeout.

Polls at a short interval inside the browser context.  Resolves as
soon as ``document.querySelector(selector)`` is non-null, or throws
a JS ``Error`` when *timeout* seconds elapse.
**Args:**

- `selector` `str` — CSS selector to wait for.
- `timeout` `float` — Maximum wait time in seconds. Defaults to ``10.0``.

## `WaitForTimeout` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/actions/builtin/wait.py#L35" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

Sleep for *ms* milliseconds **inside the browser context**.

This pauses the JS execution inside the page, not the Python event
loop.  Useful for waiting on animations or debounced handlers.
**Args:**

- `ms` `int` — Delay in milliseconds.

## `safe_url` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/schema.py#L73" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`safe_url(value: str | None) -> str | None`

Return ``None`` for ``javascript:``, ``data:``, and ``vbscript:`` URLs.

Use this on any `Attr` field that extracts a URL (``href``,
``src``, ``action``, etc.) to prevent unsafe schemes from propagating.
**Args:**

- `value` `str | None` — Raw attribute value from the DOM, or ``None``.

**Returns:** `str | None` — The original value, or ``None`` if a dangerous scheme was detected.

## `strip_tags` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/schema.py#L90" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`strip_tags(value: str | None) -> str | None`

Strip HTML tag-like substrings from *value*.

Useful when a field may contain inline markup — removes anything that
looks like ``<tag>`` or ``</tag>`` using a simple regex.  Not a full
HTML sanitiser; use on plain-text fields that shouldn't contain markup.
**Args:**

- `value` `str | None` — Raw text value from the DOM, or ``None``.

**Returns:** `str | None` — The value with tag-like substrings removed, or ``None`` unchanged.

# Debug

## `DebugSession` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/debug.py#L219" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

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

### `add` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/debug.py#L269" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`add(action: ActionNode) -> DebugSession`

Append a single action to the execution queue.
**Args:**

- `action` `ActionNode` — The action to enqueue.

**Returns:** `DebugSession` — This session, for chaining.

### `add_flow` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/debug.py#L281" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`add_flow(flow: Flow) -> DebugSession`

Append every action from a `Flow` to the queue.
**Args:**

- `flow` `Flow` — The flow whose actions to enqueue.

**Returns:** `DebugSession` — This session, for chaining.

### `start` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/debug.py#L295" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

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

## `vc_breakpoint` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/v0.2.2/voidcrawl/debug.py#L148" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`vc_breakpoint() -> _T`

Mark an action class as a debugger breakpoint.

When a `DebugSession` encounters an action whose class is
marked with this decorator, it pauses execution regardless of
whether stepping mode is active.
**Args:**

- `cls` `_T` — The action class to mark.

**Returns:** `_T` — The same class, with an internal marker attribute set.

