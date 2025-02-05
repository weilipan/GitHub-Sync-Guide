# github-manual
# Git Bash 使用指南

Git Bash 是 Windows 上的一個命令列工具，提供類似 Unix Shell 的操作環境，讓開發者可以使用 Git 命令來管理專案。

## 1. 安裝 Git Bash
1. **下載 Git**
   - 前往 [Git 官方網站](https://git-scm.com/) 下載 Git。
   - 選擇 Windows 版本並安裝。
2. **啟動 Git Bash**
   - 安裝完成後，在 Windows 搜尋 **Git Bash** 並打開。

## 2. 設置 Git 環境
### 設定使用者資訊
```sh
git config --global user.name "你的名稱"
git config --global user.email "你的郵件"
```

### 檢查 Git 設定
```sh
git config --list
```

## 3. Git Bash 常用指令
### 初始化 Git 專案
```sh
git init
```

### 下載遠端專案
```sh
git clone <遠端倉庫網址>
```

### 查看目前狀態
```sh
git status
```

### 添加檔案到暫存區
```sh
git add <檔案名稱>
```
或添加所有變更：
```sh
git add .
```

### 提交變更
```sh
git commit -m "提交訊息"
```

### 查看提交歷史
```sh
git log
```

## 4. 分支管理
### 查看目前分支
```sh
git branch
```

### 創建新分支
```sh
git branch <分支名稱>
```

### 切換分支
```sh
git checkout <分支名稱>
```
或：
```sh
git switch <分支名稱>
```

### 合併分支
```sh
git merge <分支名稱>
```

## 5. 遠端倉庫操作
### 連結遠端倉庫
```sh
git remote add origin <遠端倉庫網址>
```

### 推送本地變更
```sh
git push origin <分支名稱>
```

### 拉取遠端變更
```sh
git pull origin <分支名稱>
```

## 6. 其他有用指令
### 刪除分支
```sh
git branch -d <分支名稱>
```

### 暫存變更
```sh
git stash
git stash pop
```

### 撤銷最近的提交
```sh
git reset --hard HEAD~1
```

## 7. Git Bash 額外技巧
### 清除畫面
```sh
clear
```
或：
```sh
Ctrl + L
```

### 查看當前目錄
```sh
pwd
```

### 列出資料夾內容
```sh
ls -al
```

### 切換目錄
```sh
cd <資料夾名稱>
```

### 建立新資料夾
```sh
mkdir <資料夾名稱>
```

### 刪除文件
```sh
rm <檔案名稱>
```

Git Bash 是一個強大的命令列工具，能夠有效幫助開發者進行版本控制與專案管理。

