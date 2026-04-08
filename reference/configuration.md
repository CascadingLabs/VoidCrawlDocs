---
title: Configuration
description: Configuration reference for voidcrawl v0.2.3
---

> Generated from voidcrawl `v0.2.3`. Only symbols in `__all__` are listed.

## `BrowserConfig` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/0.2.3/voidcrawl/__init__.py#L92" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

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

### `model_dump` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/0.2.3/voidcrawl/__init__.py#L97" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`model_dump() -> dict[str, object]`

## `PoolConfig` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/0.2.3/voidcrawl/__init__.py#L151" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

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

### `from_docker` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/0.2.3/voidcrawl/__init__.py#L230" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

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

### `from_env` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/0.2.3/voidcrawl/__init__.py#L307" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

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

### `from_profile` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/0.2.3/voidcrawl/__init__.py#L194" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

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

### `model_dump` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/0.2.3/voidcrawl/__init__.py#L142" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`model_dump() -> dict[str, object]`

