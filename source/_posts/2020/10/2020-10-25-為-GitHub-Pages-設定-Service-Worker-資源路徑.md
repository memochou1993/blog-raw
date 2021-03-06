---
title: 為 GitHub Pages 設定 Service Worker 資源路徑
permalink: 為-GitHub-Pages-設定-Service-Worker-資源路徑
date: 2020-10-25 16:40:59
tags: ["程式設計", "JavaScript", "PWA", "GitHub", "GitHub Pages"]
categories: ["程式設計", "JavaScript", "PWA"]
---

## 做法

修改 `manifest.json` 檔的 `start_url` 參數：

```JSON
{
  "start_url": "/<REPOSITORY>/index.html"
}
```

修改 `service-worker.js` 檔的資源路徑：

```JS
self.addEventListener("install", (e) => {
  e.waitUntil(
    caches.open("store").then((cache) => {
      return cache.addAll([
        "/<REPOSITORY>/",
        "/<REPOSITORY>/index.html",
        "/<REPOSITORY>/images/cover.png",
        "/<REPOSITORY>/css/app.css",
        "/<REPOSITORY>/js/app.js",
      ]);
    })
  );
});
```

## 除錯

打開 Chrome 開發者工具，點選 Lighthouse 頁籤，將 Progressive Web App 打勾後，點選「Generate report」，即可查看當前的網站是否符合 PWA 的規範。
