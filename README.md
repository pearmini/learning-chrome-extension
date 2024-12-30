# Learning Chrome Extension

My notes, examples, and experiments with Chrome Extension. The tutorial is [here](https://developer.chrome.com/docs/extensions/get-started).

## Extensions

- [tabs-manager](./tabs-manager/)
- [focus-mode](./focus-mode/)
- [reading-time](./reading-time/)
- [hello-world](./hello-world/)

## Tabs Manager (2024/12/30)

> https://developer.chrome.com/docs/extensions/get-started/tutorial/popup-tabs-manager

- Collect tabs:

```js
const tabs = await chrome.tabs.query({
  url: ["https://github.com/*"],
});
```

- Group tabs:

```js
const tabIds = tabs.map(({ id }) => id);
if (tabIds.length) {
  const group = await chrome.tabs.group({ tabIds });
  await chrome.tabGroups.update(group, { title: "Repos" });
}
```

- Permission

```json
{
  "host_permissions": ["https://github.com/*"],
  "permissions": ["tabGroups"]
}
```

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
| ![off](./focus-mode/off.png) | ![on](./focus-mode/on.png) |

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
| ![off](./reading-time/off.png) | ![on](./reading-time/on.png) |

## Hello World (2024/11/12)

> https://developer.chrome.com/docs/extensions/get-started/tutorial/hello-world

- `mainifest.json` is like `package.json` in Node project, which describes the extension's capabilities and configurations.
- A popup has its own DevTools.
