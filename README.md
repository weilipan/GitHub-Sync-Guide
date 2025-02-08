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

## **4. 拉取遠端變更，確保本機與遠端同步**
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

## **5. 提交並推送變更到 GitHub**
### **5.1 新增檔案至 Git**
```bash
git add .
```

### **5.2 提交變更**
```bash
git commit -m "更新說明"
```

### **5.3 推送至 GitHub**
```bash
git push origin main
```

如果出現 `rejected (non-fast-forward)` 錯誤，請先執行：
```bash
git pull origin main --rebase
```
解決衝突後再推送。

---

## **6. 從 GitHub 克隆（Clone）專案到本機**
如果你想下載遠端 GitHub 專案到本機，請執行：
```bash
git clone https://github.com/你的GitHub帳號/你的Repository名稱.git
```

這會在本機建立一個與 GitHub 同步的專案資料夾。

---

## **7. 使用 GitHub Token 進行身份驗證**
GitHub 不再支援使用密碼進行驗證，你需要使用 **Personal Access Token (PAT)**。

### **7.1 生成 GitHub Token**
1. 登入 GitHub → 點擊 **你的頭像** → **Settings**（設定）。
2. 進入 **Developer settings** → **Personal access tokens**。
3. 點擊 **Generate new token**，選擇 `repo` 權限。
4. 產生 Token，並**記住這組 Token**。

### **7.2 設定 Git 使用 Token**
```bash
git remote set-url origin https://your-token@github.com/你的GitHub帳號/你的Repository名稱.git
```
這樣下次推送時，就不會再要求輸入密碼。

---

## **8. 常見錯誤處理**
如果遇到 Git 錯誤，請參考 [`troubleshooting.md`](troubleshooting.md)。

---

這份指南完整涵蓋了 GitHub 專案的同步流程，希望能幫助你順利操作 Git！🚀

