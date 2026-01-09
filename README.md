#Charles流程
1.導出 Charles 的證書
2.使用openssl 查出 Charles 證書的名稱
2-2.openssl x509 -subject_hash_old -in “xxx.pem”
3.修改 Charles 導出的證書名稱 為 xxxxxxx.0


模擬器流程
1.將證書放置模擬器的資料夾中
2.執行模擬器 以及 在資料夾內打開命令字元
3.執行代碼

adb root
adb remount
adb push 5f1828fc.0 /system/etc/security/cacerts

adb shell
su
mount -o remount,rw /system
chmod 644 /system/etc/security/cacerts/5f1828fc.0
chown root:root /system/etc/security/cacerts/5f1828fc.0
exit

adb reboot