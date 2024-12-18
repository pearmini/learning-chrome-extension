# Learning Chrome Extension

My notes, examples, and experiments with Chrome Extension. The tutorial is [here](https://developer.chrome.com/docs/extensions/get-started).

## Extensions

- [hello_world](./hello_world/)
- [reading_time](./reading_time/)
- [focus_mode](./focus_mode/)

## Focus Mode (2024/12/05)

> https://developer.chrome.com/docs/extensions/get-started/tutorial/scripts-activetab

- Inject CSS:

```js
await chrome.scripting.insertCSS({
  files: ["focus-mode.css"],
  target: { tabId: tab.id },
});
```

- Permission

```json
{
  "permissions": ["activeTab", "scripting"]
}
```

| Off                          | ON                         |
| ---------------------------- | -------------------------- |
| ![off](./focus_mode/off.png) | ![on](./focus_mode/on.png) |

## Reading Time (2024/11/22)

> https://developer.chrome.com/docs/extensions/get-started/tutorial/scripts-on-every-tab

- declare the content script:

```json
"content_scripts": [
  {
    "js": ["scripts/content.js"],
    "matches": [
      "https://developer.chrome.com/docs/extensions/*",
      "https://developer.chrome.com/docs/webstore/*"
    ]
  }
]
```

| Off                            | ON                           |
| ------------------------------ | ---------------------------- |
| ![off](./reading_time/off.png) | ![on](./reading_time/on.png) |

## Hello World (2024/11/12)

> https://developer.chrome.com/docs/extensions/get-started/tutorial/hello-world

- `mainifest.json` is like `package.json` in Node project, which describes the extension's capabilities and configurations.
- A popup has its own DevTools.
