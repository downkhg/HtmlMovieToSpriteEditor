---
name: file-based-testing
description: >-
  Detailed guidelines for testing the HtmlMovieToSprite generator locally by opening the HTML files directly via the file:// protocol in the browser, bypassing server setups and resolving local iframe policy blocks.
---

# Local File-Based Testing Skill

## Overview
This skill outlines how to run and verify UI/UX behaviors in the HtmlMovieToSprite application locally by opening files directly (file://) in the browser, rather than relying on local web server commands (e.g. http-server, python http.server). It covers bypassing browser security limitations (such as iframe blocking on file://) by automatically using browser popup window fallbacks.

## Quick Start
To test the Video State Sprite Creator:
1. Open the file `file:///c:/Users/downk.KHG-HOME/source/repos/HtmlMovieToSprite/HtmlPageSamples/VideoStateSpriteCreator.html` directly in the browser.
2. Verify visual layouts and controls (Timeline, Storyboard, Settings).
3. Click "⚙️ 프롬프트 매니저" (Prompt Manager) to open the configurator as a popup window, and verify synchronization.
 
## Workflow
### 1. Load local HTML pages
- Construct the absolute URL using the `file:///` scheme and the absolute path to the HTML files.
  Example: `file:///c:/Users/downk.KHG-HOME/source/repos/HtmlMovieToSprite/HtmlPageSamples/VideoStateSpriteCreator.html`
- Use the browser agent to open this URL directly.

### 2. Verify Prompt Manager popup
- Click "⚙️ 프롬프트 매니저" to open the Manager.
- On the `file://` protocol, this automatically launches a standard browser popup window instead of an iframe (due to Chrome's local resource security policies).
- Verify the popup contents load and sync changes dynamically with the parent page.

### 3. Click "✕ 닫기" to close
- Verify that clicking "✕ 닫기" in the Prompt Manager window successfully focuses the parent window and closes the popup.

## Common Mistakes
- **Running HTTP servers**: Avoid starting python or node web servers for testing unless explicitly requested, as the project is fully functional as static pages under the `file://` protocol.
- **Iframe errors on file://**: Do not try to load `2DSpritePromptAStateManager.html` inside an iframe on `file://` environments, as modern browsers block cross-origin subresources on local files.
