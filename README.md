1.导出chaeles证书 
1-1.hash证书得到名称(需要安装openssl)
openssl x509 -subject_hash_old -in “xxx.pem”

1-2.改名称 c146f3b1.0 = 改成自己的证书名称



2.把证书丢到模拟器资料夹里

系统管理员下执行cmd
cmd在模拟器资料夹下 操作以下

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