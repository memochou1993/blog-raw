---
title: 在 MacOS 校正 Laradock 環境時間
permalink: 在-MacOS-校正-Laradock-環境時間
date: 2019-08-26 22:07:08
tags: ["環境部署", "Docker", "Laradock"]
categories: ["環境部署", "Laradock"]
---

## 步驟

修改 `.env` 檔，開啟 SSH 連線。

```ENV
WORKSPACE_INSTALL_WORKSPACE_SSH=true
```

修改 `insecure_id_rsa` 檔的權限。

```BASH
chmod 0600 workspace/insecure_id_rsa
```

修改 `docker-compose.yml` 檔

```YML
workspace:
  ...
  privileged: true
```

重建 `workspace` 容器。

```BASH
docker-compose build workspace
```

校正時間。

```BASH
ssh -p 2222 -i workspace/insecure_id_rsa root@localhost date -u $(date +%m%d%H%M%Y)
```
