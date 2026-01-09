# Charles 證書安裝與模擬器 HTTPS 抓包流程

本指南介紹如何將 Charles 證書導入 Android 模擬器系統層級，以實現 HTTPS 抓包。

## 🛠 Charles 證書處理流程

1. **導出證書**：從 Charles 導出 `.pem` 或 `.cer` 格式的證書。
2. **獲取 Hash 名稱**：
   使用 OpenSSL 查出證書在 Android 系統中所需的特定名稱。
   ```bash
   openssl x509 -subject_hash_old -in "你的證書名稱.pem"

# 取得 root 權限並掛載系統分區
 ```bash
adb root
adb remount
# 將證書推送到系統憑證路徑
adb push 5f1828fc.0 /system/etc/security/cacerts
adb shell
su
# 重新掛載為讀寫模式 (若 remount 失敗時使用)
mount -o remount,rw /system
# 修正權限 (644) 與擁有者 (root)
chmod 644 /system/etc/security/cacerts/5f1828fc.0
chown root:root /system/etc/security/cacerts/5f1828fc.0
exit
# 重啟模擬器生效
adb reboot