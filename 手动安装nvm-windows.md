# 手动安装nvm-windows

### 下载免安装包  
[下载免安装包nvm-noinstall.zip](nvm-noinstall.zip), 解压至：C:\Users\<username>\AppData\Roaming\nvm  

### 添加环境变量
1. 添加环境变量NVM_HOME：C:\Users\<username>\AppData\Roaming\nvm （安装路径） 
2. 添加环境变量NVM_SYMLINK，为NVM_SYMLINK制定一个不存在的目录。这个目录会被nvm自动创建和维护。
3. 修改系统环境变量Path，添加%NVM_HOME%;%NVM_SYMLINK%至末尾。
4. 修改用户变量Path，添加%NVM_HOME%;%NVM_SYMLINK%至末尾。

### 创建settings.txt
在安装目录新建settings.txt
```
root: nvm安装路径
path： NVM_SYMLINK指定的路径
proxy: none
arch: 64
```

### 参考
https://github.com/coreybutler/nvm-windows/wiki#manual-installation
