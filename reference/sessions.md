---
title: Sessions & Pools
description: Session and pool reference for void_crawl v0.1.3
---

> Generated from void_crawl `v0.1.3`. Only symbols in `__all__` are listed.

## `BrowserPool` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/0.1.3/void_crawl/__init__.py#L269" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

Pool of reusable browser tabs across one or more Chrome processes.

Manages a semaphore-bounded set of recycled tabs.  Tabs are navigated
to ``about:blank`` on release rather than closed, making subsequent
acquires near-instant.  Tabs are hard-recycled after
`PoolConfig.tab_max_uses` navigations and evicted after
`PoolConfig.tab_max_idle_secs` of inactivity.
**Args:**

- `config` `PoolConfig` — Pool sizing and browser launch options.

### `acquire` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/0.1.3/void_crawl/__init__.py#L324" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`acquire() -> _AcquireContext`

Check out a tab from the pool as an async context manager.

The tab is automatically returned to the pool when the context
exits, even on exception.
**Returns:** `_AcquireContext` — An async context manager yielding a `PooledTab`.

### `warmup` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/0.1.3/void_crawl/__init__.py#L340" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`warmup() -> None`

Pre-open tabs across all browser sessions.

Call after entering the pool context to eliminate cold-start
latency on the first `acquire` calls.

## `BrowserSession` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/0.1.3/void_crawl/__init__.py#L185" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

Async context manager wrapping a single Chromium instance via CDP.

Use as an ``async with`` block.  On entry the browser is launched (or
connected to, if `BrowserConfig.ws_url` is set); on exit the
process is terminated and resources are freed.
**Args:**

- `config` `BrowserConfig | None` — Browser launch options.  Defaults to
``BrowserConfig()`` (headless + stealth).

### `close` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/0.1.3/void_crawl/__init__.py#L248" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`close() -> None`

Shut down the browser process immediately.

Called automatically on ``__aexit__``; only needed if you want
to close the browser without leaving the ``async with`` block.

### `new_page` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/0.1.3/void_crawl/__init__.py#L227" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`new_page(url: str) -> Page`

Open a new tab and navigate to *url*.
**Args:**

- `url` `str` — The URL to load in the new tab.

**Returns:** `Page` — The new tab handle.

### `version` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/0.1.3/void_crawl/__init__.py#L239" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`version() -> str`

Return the browser version string (e.g. ``"Chrome/126.0.6478.126"``).
**Returns:** `str` — The Chrome/Chromium product version reported by the browser.

## `Page` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/0.1.3/void_crawl/_ext.pyi#L247" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

A single browser tab created via `BrowserSession.new_page`.

Provides navigation, content extraction, JavaScript evaluation,
media capture, DOM queries, user-interaction helpers, and low-level
CDP input dispatch.

### `click_element` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/0.1.3/void_crawl/_ext.pyi#L347" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`click_element(selector: str) -> None`

Click the first element matching *selector*.
**Args:**

- `selector` `str` — CSS selector string.

### `close` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/0.1.3/void_crawl/_ext.pyi#L440" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`close() -> None`

Close this tab and release its resources.

### `content` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/0.1.3/void_crawl/_ext.pyi#L277" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`content() -> str`

Return the full page HTML (``document.documentElement.outerHTML``).
**Returns:** `str` — The complete outer HTML of the document element.

### `dispatch_key_event` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/0.1.3/void_crawl/_ext.pyi#L422" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`dispatch_key_event(event_type: str, key: str | None = None, code: str | None = None, text: str | None = None, modifiers: int | None = None) -> None`

Send a low-level CDP ``Input.dispatchKeyEvent``.
**Args:**

- `event_type` `str` — ``"keyDown"``, ``"keyUp"``, ``"rawKeyDown"``, or ``"char"``.
- `key` `str | None` — DOM ``KeyboardEvent.key`` value (e.g. ``"Enter"``).
- `code` `str | None` — Physical key code (e.g. ``"KeyA"``).
- `text` `str | None` — Character to insert (e.g. ``"a"``).
- `modifiers` `int | None` — Bit field for modifier keys.

### `dispatch_mouse_event` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/0.1.3/void_crawl/_ext.pyi#L397" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

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

### `evaluate_js` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/0.1.3/void_crawl/_ext.pyi#L298" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`evaluate_js(expression: str) -> object`

Evaluate a JavaScript *expression* and return the result.

The return value is deserialised to a native Python type
(``dict``, ``list``, ``str``, ``int``, ``float``, ``bool``, or ``None``).
**Args:**

- `expression` `str` — JavaScript expression or IIFE string.

**Returns:** `object` — The deserialised result of the expression.

### `goto` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/0.1.3/void_crawl/_ext.pyi#L255" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`goto(url: str, timeout: float = 30.0) -> str | None`

Navigate to *url* and wait for network idle in one shot.
**Args:**

- `url` `str` — The URL to load.
- `timeout` `float` — Maximum seconds to wait for network idle.

**Returns:** `str | None` — ``"networkIdle"`` or ``"networkAlmostIdle"`` on success, `str | None` — ``None`` on timeout.

### `navigate` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/0.1.3/void_crawl/_ext.pyi#L267" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`navigate(url: str) -> None`

Navigate to *url* without waiting for any load event.
**Args:**

- `url` `str` — The URL to load.

### `pdf_bytes` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/0.1.3/void_crawl/_ext.pyi#L318" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`pdf_bytes() -> bytes`

Render the page as a PDF and return the raw bytes.

Only works in headless mode.
**Returns:** `bytes` — Raw PDF file data.

### `query_selector` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/0.1.3/void_crawl/_ext.pyi#L327" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`query_selector(selector: str) -> str | None`

Return the inner HTML of the first element matching *selector*, or ``None``.
**Args:**

- `selector` `str` — CSS selector string.

**Returns:** `str | None` — Inner HTML string of the matched element, or ``None`` if no match.

### `query_selector_all` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/0.1.3/void_crawl/_ext.pyi#L337" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`query_selector_all(selector: str) -> list[str]`

Return the inner HTML of every element matching *selector*.
**Args:**

- `selector` `str` — CSS selector string.

**Returns:** `list[str]` — List of inner HTML strings, one per matched element.

### `screenshot_png` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/0.1.3/void_crawl/_ext.pyi#L311" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`screenshot_png() -> bytes`

Capture a full-page screenshot as PNG bytes.
**Returns:** `bytes` — Raw PNG image data.

### `set_headers` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/0.1.3/void_crawl/_ext.pyi#L362" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`set_headers(headers: dict[str, str]) -> None`

Set extra HTTP headers for all subsequent requests from this page.
**Args:**

- `headers` `dict[str, str]` — Header name-value pairs.

### `title` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/0.1.3/void_crawl/_ext.pyi#L284" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`title() -> str | None`

Return the document title, or ``None``.
**Returns:** `str | None` — The ``document.title`` string, or ``None`` if unavailable.

### `type_into` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/0.1.3/void_crawl/_ext.pyi#L354" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`type_into(selector: str, text: str) -> None`

Focus the first element matching *selector* and type *text*.
**Args:**

- `selector` `str` — CSS selector string.
- `text` `str` — The text to type.

### `url` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/0.1.3/void_crawl/_ext.pyi#L291" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`url() -> str | None`

Return the current page URL, or ``None``.
**Returns:** `str | None` — The page URL as a string, or ``None`` if unavailable.

### `wait_for_navigation` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/0.1.3/void_crawl/_ext.pyi#L274" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`wait_for_navigation() -> None`

Block until the current navigation completes.

### `wait_for_network_idle` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/0.1.3/void_crawl/_ext.pyi#L386" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`wait_for_network_idle(timeout: float = 30.0) -> str | None`

Wait for network activity to settle.
**Args:**

- `timeout` `float` — Maximum seconds to wait.

**Returns:** `str | None` — ``"networkIdle"`` or ``"networkAlmostIdle"`` on success, `str | None` — ``None`` on timeout.

### `wait_for_stable_dom` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/0.1.3/void_crawl/_ext.pyi#L369" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`wait_for_stable_dom(timeout: float = 10.0, min_length: int = 5000, stable_checks: int = 5) -> bool`

Wait until the DOM stabilises (stops changing).

Polls the HTML length repeatedly and resolves once it stays
constant across *stable_checks* consecutive checks.
**Args:**

- `timeout` `float` — Maximum seconds to wait.
- `min_length` `int` — Minimum HTML length before checking stability.
- `stable_checks` `int` — Consecutive unchanged polls required.

**Returns:** `bool` — ``True`` if the DOM stabilised, ``False`` on timeout.

## `PooledTab` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/0.1.3/void_crawl/_ext.pyi#L8" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

A tab checked out from a `void_crawl.BrowserPool`.

Exposes the same page-interaction methods as `Page` but must
not be closed manually — return it to the pool via the async context
manager or `void_crawl.BrowserPool.release`.
**Attributes:**

- `use_count` `int` — How many times this tab has been acquired (0 on first use).

### `click_element` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/0.1.3/void_crawl/_ext.pyi#L104" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`click_element(selector: str) -> None`

Click the first element matching *selector*.
**Args:**

- `selector` `str` — CSS selector string.

### `content` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/0.1.3/void_crawl/_ext.pyi#L43" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`content() -> str`

Return the full page HTML (``document.documentElement.outerHTML``).
**Returns:** `str` — The complete outer HTML of the document element.

### `dispatch_key_event` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/0.1.3/void_crawl/_ext.pyi#L179" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`dispatch_key_event(event_type: str, key: str | None = None, code: str | None = None, text: str | None = None, modifiers: int | None = None) -> None`

Send a low-level CDP ``Input.dispatchKeyEvent``.
**Args:**

- `event_type` `str` — ``"keyDown"``, ``"keyUp"``, ``"rawKeyDown"``, or ``"char"``.
- `key` `str | None` — DOM ``KeyboardEvent.key`` value (e.g. ``"Enter"``).
- `code` `str | None` — Physical key code (e.g. ``"KeyA"``).
- `text` `str | None` — Character to insert (e.g. ``"a"``).
- `modifiers` `int | None` — Bit field for modifier keys.

### `dispatch_mouse_event` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/0.1.3/void_crawl/_ext.pyi#L154" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

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

### `evaluate_js` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/0.1.3/void_crawl/_ext.pyi#L64" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`evaluate_js(expression: str) -> object`

Evaluate a JavaScript *expression* and return the result.

The return value is deserialised to a native Python type
(``dict``, ``list``, ``str``, ``int``, ``float``, ``bool``, or ``None``).
**Args:**

- `expression` `str` — JavaScript expression or IIFE string.

**Returns:** `object` — The deserialised result of the expression.

### `goto` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/0.1.3/void_crawl/_ext.pyi#L21" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`goto(url: str, timeout: float = 30.0) -> str | None`

Navigate to *url* and wait for network idle in one shot.
**Args:**

- `url` `str` — The URL to load.
- `timeout` `float` — Maximum seconds to wait for network idle.

**Returns:** `str | None` — ``"networkIdle"`` or ``"networkAlmostIdle"`` on success, `str | None` — ``None`` on timeout.

### `navigate` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/0.1.3/void_crawl/_ext.pyi#L33" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`navigate(url: str) -> None`

Navigate to *url* without waiting for any load event.
**Args:**

- `url` `str` — The URL to load.

### `query_selector` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/0.1.3/void_crawl/_ext.pyi#L84" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`query_selector(selector: str) -> str | None`

Return the inner HTML of the first element matching *selector*, or ``None``.
**Args:**

- `selector` `str` — CSS selector string.

**Returns:** `str | None` — Inner HTML string of the matched element, or ``None`` if no match.

### `query_selector_all` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/0.1.3/void_crawl/_ext.pyi#L94" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`query_selector_all(selector: str) -> list[str]`

Return the inner HTML of every element matching *selector*.
**Args:**

- `selector` `str` — CSS selector string.

**Returns:** `list[str]` — List of inner HTML strings, one per matched element.

### `screenshot_png` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/0.1.3/void_crawl/_ext.pyi#L77" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`screenshot_png() -> bytes`

Capture a full-page screenshot as PNG bytes.
**Returns:** `bytes` — Raw PNG image data.

### `set_headers` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/0.1.3/void_crawl/_ext.pyi#L119" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`set_headers(headers: dict[str, str]) -> None`

Set extra HTTP headers for all subsequent requests from this tab.
**Args:**

- `headers` `dict[str, str]` — Header name-value pairs.

### `title` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/0.1.3/void_crawl/_ext.pyi#L50" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`title() -> str | None`

Return the document title, or ``None``.
**Returns:** `str | None` — The ``document.title`` string, or ``None`` if unavailable.

### `type_into` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/0.1.3/void_crawl/_ext.pyi#L111" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`type_into(selector: str, text: str) -> None`

Focus the first element matching *selector* and type *text*.
**Args:**

- `selector` `str` — CSS selector string.
- `text` `str` — The text to type.

### `url` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/0.1.3/void_crawl/_ext.pyi#L57" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`url() -> str | None`

Return the current page URL, or ``None``.
**Returns:** `str | None` — The page URL as a string, or ``None`` if unavailable.

### `wait_for_navigation` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/0.1.3/void_crawl/_ext.pyi#L40" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`wait_for_navigation() -> None`

Block until the current navigation completes.

### `wait_for_network_idle` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/0.1.3/void_crawl/_ext.pyi#L143" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`wait_for_network_idle(timeout: float = 30.0) -> str | None`

Wait for network activity to settle.
**Args:**

- `timeout` `float` — Maximum seconds to wait.

**Returns:** `str | None` — ``"networkIdle"`` or ``"networkAlmostIdle"`` on success, `str | None` — ``None`` on timeout.

### `wait_for_stable_dom` <a href="https://github.com/CascadingLabs/VoidCrawl/blob/0.1.3/void_crawl/_ext.pyi#L126" target="_blank" rel="noopener noreferrer" title="View source on GitHub"><svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="14" xmlns="http://www.w3.org/2000/svg" style="vertical-align:-2px;display:inline-block"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg></a>

`wait_for_stable_dom(timeout: float = 10.0, min_length: int = 5000, stable_checks: int = 5) -> bool`

Wait until the DOM stabilises (stops changing).

Polls the HTML length repeatedly and resolves once it stays
constant across *stable_checks* consecutive checks.
**Args:**

- `timeout` `float` — Maximum seconds to wait.
- `min_length` `int` — Minimum HTML length before checking stability.
- `stable_checks` `int` — Consecutive unchanged polls required.

**Returns:** `bool` — ``True`` if the DOM stabilised, ``False`` on timeout.

