# GitHub Sync Guide

這是一份 GitHub 新手指南，詳細說明如何使用 Git Bash 將本機端的專案同步到 GitHub。

## **1. 設定 Git 使用者資訊（僅需設定一次）**
如果你是第一次使用 Git，請執行以下指令來設定你的 GitHub 使用者資訊：

```bash
git config --global user.name "你的 GitHub 使用者名稱"
git config --global user.email "你的 GitHub 註冊信箱"
```

檢查設定是否成功：
```bash
git config --global --list
```

---

## **2. 建立或進入你的專案資料夾**
開啟 Git Bash，進入你的專案資料夾：
```bash
cd /path/to/your/project
```
如果你的專案還沒有 Git 初始化，請執行：
```bash
git init
```

---

## **3. 連結遠端 GitHub Repository**
先檢查是否已有遠端 GitHub 連結：
```bash
git remote -v
```
如果沒有，請執行：
```bash
git remote add origin https://github.com/你的GitHub帳號/你的Repository名稱.git
```

---

## **4.將 `master` 重新命名為 `main`（推薦）**
   ```bash
   git branch -M main
   git push -u origin main
   ```
---
## **5. 拉取遠端變更，確保本機與遠端同步**
如果遠端 repository 已有內容，請執行：
```bash
git pull origin main --rebase
```
**如果遇到衝突，請手動解決，然後執行：**
```bash
git add .
git rebase --continue
```

---

## **6. 提交並推送變更到 GitHub**
### **6.1 新增檔案至 Git**
```bash
git add .
```

### **6.2 提交變更**
```bash
git commit -m "更新說明"
```

### **6.3 推送至 GitHub**
```bash
git push origin main
```

如果出現 `rejected (non-fast-forward)` 錯誤，請先執行：
```bash
git pull origin main --rebase
```
解決衝突後再推送。

---

## **7. 從 GitHub 克隆（Clone）專案到本機**
如果你想下載遠端 GitHub 專案到本機，請執行：
```bash
git clone https://github.com/你的GitHub帳號/你的Repository名稱.git
```

這會在本機建立一個與 GitHub 同步的專案資料夾。

---

## **8. 使用 GitHub Token 進行身份驗證**
GitHub 不再支援使用密碼進行驗證，你需要使用 **Personal Access Token (PAT)**。

### **8.1 生成 GitHub Token**
1. 登入 GitHub → 點擊 **你的頭像** → **Settings**（設定）。
2. 進入 **Developer settings** → **Personal access tokens**。
3. 點擊 **Generate new token**，選擇 `repo` 權限。
4. 產生 Token，並**記住這組 Token**。

### **8.2 設定 Git 使用 Token**
```bash
git remote set-url origin https://your-token@github.com/你的GitHub帳號/你的Repository名稱.git
```
這樣下次推送時，就不會再要求輸入密碼。

---

## **9. 常見錯誤處理**
### Git `error: src refspec main does not match any` 錯誤解決方案

當你嘗試執行 `git push origin main` 時，可能會遇到以下錯誤：

```bash
error: src refspec main does not match any
```

這通常是因為 Git 無法找到 `main` 分支，可能的原因如下：

---

#### **1. 確保已經初始化 Git 並提交專案**

在你的專案目錄中執行：

```bash
git status
```

如果 Git 回應：

```bash
fatal: not a git repository (or any of the parent directories): .git
```

表示你還沒有初始化 Git，你需要執行：

```bash
git init
git add .
git commit -m "Initial commit"
```

這將初始化 Git 並提交你的專案。

---

#### **2. 檢查當前分支名稱**

執行：

```bash
git branch
```

如果輸出結果是：

```bash
* master
```

表示你的當前分支名稱是 `master`，但你在 `git push origin main` 時使用了 `main`，導致 Git 無法找到該分支。

#### **解決方法**
1. **將 `main` 改為 `master` 推送**
   ```bash
   git push origin master
   ```

2. **將 `master` 重新命名為 `main`（推薦）**
   ```bash
   git branch -M main
   git push -u origin main
   ```

---

#### **3. 確保遠端倉庫已正確設置**

執行以下命令來檢查遠端倉庫：

```bash
git remote -v
```

如果沒有遠端倉庫，則需要執行：

```bash
git remote add origin https://github.com/你的GitHub帳號/你的倉庫名稱.git
```

然後執行：

```bash
git push -u origin main
```

---

#### **4. 確保 GitHub 上的倉庫已經建立**

如果 GitHub 上沒有對應的 Repository，你需要：

1. **手動在 GitHub 上建立一個新的 Repository**
2. **然後執行以下命令**

```bash
git remote add origin https://github.com/你的GitHub帳號/你的倉庫名稱.git
git branch -M main
git push -u origin main
```

這樣應該可以解決問題。

---

#### **總結**

| 問題 | 解決方法 |
|------|---------|
| **未初始化 Git** | `git init`，然後 `git add .` 和 `git commit -m "Initial commit"` |
| **當前分支是 `master` 而不是 `main`** | 使用 `git branch -M main` 來重命名 |
| **遠端倉庫未設定** | 執行 `git remote add origin` 並正確推送 |
| **GitHub 上倉庫未建立** | 先手動建立倉庫，然後設定 `remote` 並推送 |

如果仍然遇到問題，可以提供 `git branch` 和 `git remote -v` 的輸出來進一步診斷！🚀


---

這份指南完整涵蓋了 GitHub 專案的同步流程，希望能幫助你順利操作 Git！🚀



