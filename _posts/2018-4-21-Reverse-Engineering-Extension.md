---
layout: post
title: "Reverse Engineering an Extension"
categories: hackingthebrowser
---
I'm reverse engineering the [Tab Snooze](https://chrome.google.com/webstore/detail/tab-snooze/pdiebiamhaleloakpcgmpnenggpjbcbm) extension. This extension lets you "close unnecessary tabs and make them magically reappear when you need them."

Here is the file system for this extension. I downloaded the files using [Chrome Extension Source Viewer](https://chrome.google.com/webstore/detail/chrome-extension-source-v/jifpbeccnghkjeaalbbjmodiffmgedin/related?hl=en).
![alt text](https://raw.githubusercontent.com/jirrian/jirrian.github.io/master/images/hackingthebrowser/tabsnoozefiles.png)

Looking in the `manifest.json` file, it requires the following permissions:
```json
"permissions": [
        "tabs",
        "alarms",
        "storage",
        "notifications",
        "idle",
        "<all_urls>"
    ]
```
It has a browser action which 'snoozes' the current tab and background script 'background.js' that uses the jquery and moment.js libraries. The `content-script.js` creates an angular.js app (which I don't know anything about) that handles the majority of the extension's functionality. I believe the `background.js` script has functions that deal with getting info from or changing the browser. It contains functions such as getting all existing tabs or creating a new tab.

The `manifest.json` also includes the [commands API](https://developer.chrome.com/extensions/commands) which lets you create keyboard commands. Each command references a function defined in `background.js`. 
```json
"commands": {
        "_execute_browser_action": {
            "suggested_key": {
                "default": "Alt+S"
            },
            "description": "Snooze active tab"
        },
        "repeat_last_snooze": {
            "suggested_key": {
                "default": "Alt+Shift+S"
            },
            "description": "Repeat last snooze action"
        },
        "open_snoozed_list": {
            "suggested_key": {
                "default": "Alt+Shift+L"
            },
            "description": "Open snoozed tabs list"
        },
        "new_todo_page": {
            "suggested_key": {
                "default": "Ctrl+Shift+1"
            },
            "description": "New todo tab",
            "global": true
        }
    }
```
