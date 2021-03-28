# Xcode


## 报错解决


**xcrun: error: invalid active developer path (/Library/Developer/CommandLineTools), missing xcrun at: /Library/Developer/CommandLineTools/usr/bin/xcrun**

参考链接: https://blog.csdn.net/qq_33375598/article/details/103819418

原因: 系统更新

解决:
 ```
 xcode-select --install
 ```
