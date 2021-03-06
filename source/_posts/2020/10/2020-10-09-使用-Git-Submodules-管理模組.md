---
title: 使用 Git Submodules 管理模組
permalink: 使用-Git-Submodules-管理模組
date: 2020-10-09 23:04:05
tags: ["版本控制", "Git"]
categories: ["版本控制"]
---

## 指令

### 新增子模組

```BASH
git submodule add <REPOSITORY> <PATH>
```

### 更新子模組

```BASH
git submodule foreach --recursive git pull origin master
```

### 下載遺失的子模組

```BASH
git submodule update --init --recursive
```

- 參數 `init` 將 `.gitmodules` 中的資訊註冊到 `.git/config` 內。
- 參數 `update` 將根據 `.git/config` 內的資訊進行更新。

### 下載包含子模組的專案

```BASH
git clone --recursive <REPOSITORY>
```

### 刪除子模組

```BASH
git submodule deinit <PATH>
git rm --cached <PATH>
rm -rf <PATH>
rm -rf .git/modules/<PATH>
```

## 參考資料

- [Git Tools - Submodules](https://git-scm.com/book/en/v2/Git-Tools-Submodules)
