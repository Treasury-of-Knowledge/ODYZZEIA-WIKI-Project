---
title: 安卓termux手动部署-無脚本
description: 
published: true
date: 2026-03-05T13:23:38.285Z
tags: 
editor: markdown
dateCreated: 2026-03-05T13:23:38.285Z
---

# 安卓termux手动部署-無脚本
## 本教學將說明如何在 Android 裝置上使用 Termux 部署 SillyTavern。

## 1. 安裝 Termux
不建議直接在 Google Play 版
Google Play 上的 Termux 版本已停止維護，請改用：
- [F-Droid](https://f-droid.org/zh_Hant/packages/com.termux/) 
- [github](https://github.com/termux/termux-app)
然後安裝 APK，打開 Termux

## 2. 初始化 Termux（換源 + 更新）

### 更新termux内置的套件
```bash
pkg update && pkg upgrade
```
---
## 3. 安裝依賴

```bash
pkg install -y curl unzip git nodejs jq
```

說明：
- `git`：用於下載與更新 SillyTavern

---

## 4. 安裝 SillyTavern（選擇分支）

SillyTavern 常見分支：
- `release`：相對穩定，適合一般使用
- `staging`：更新較快，可能有新功能但也可能不穩

### 建議安裝1.13.4/1.14.0/或者1.16.0 不過當中的1.16.0渲染壓力很大
```bash
git clone https://github.com/SillyTavern/SillyTavern -b 1.14.0
```
```bash
git clone https://github.com/SillyTavern/SillyTavern -b 1.13.4
```
```bash
git clone https://github.com/SillyTavern/SillyTavern -b 1.16.0
```


---

## 5. 啟動 SillyTavern

進入資料夾並執行啟動腳本：
```bash
cd ~/SillyTavern
bash start.sh
```

首次啟動會自動安裝/更新部分依賴，請耐心等待。

### 5.1 在手機瀏覽器打開
啟動後終端通常會顯示本機網址（常見類似）：
- `http://127.0.0.1:8000`
- 或 `http://localhost:8000`

用手機瀏覽器打開該網址即可使用。

> 若你想用同一個 Wi‑Fi 下的電腦訪問，通常需要額外設定config.yaml

---

## 6. 更新 SillyTavern（推薦方式）

在 Termux 執行：
```bash
cd ~/SillyTavern
git pull --rebase --autostash
```
更新前建議備份 SillyTavern
更新後建議重啟 SillyTavern（停止後重新執行 `bash start.sh`）。

---

