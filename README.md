# lua-pro
# CentOS 7中安装Lua
## 1.CentOS7默认已经安装了5.1.4
①查看当前lua版本号：
 ```
# lua -v
```
Lua 5.1.4  Copyright (C) 1994-2008 Lua.org, PUC-Rio

②查看lua和luac的位置：
```
which lua luac
```
/usr/bin/lua

/usr/bin/luac

## 2.安装最新Lua版本（5.3.5）
① 官网下载：http://www.lua.org/download.html
```
curl -R -O http://www.lua.org/ftp/lua-5.3.5.tar.gz
tar zxf lua-5.3.5.tar.gz
cd lua-5.3.5
make linux
make install
```
cd src && mkdir -p /usr/local/bin /usr/local/include /usr/local/lib /usr/local/man/man1 /usr/local/share/lua/5.3 /usr/local/lib/lua/5.3

cd src && install -p -m 0755 lua luac /usr/local/bin

cd src && install -p -m 0644 lua.h luaconf.h lualib.h lauxlib.h lua.hpp /usr/local/include

cd src && install -p -m 0644 liblua.a /usr/local/lib

cd doc && install -p -m 0644 lua.1 luac.1 /usr/local/man/man1


可以看到，lua和luac被安装到了/usr/local/bin中

④lua -v查看版本，发现还是旧的版本，那我们就将/usr/bin中的lua和luac删除，
然后将/usr/local/bin中的lua和luac创建一个ln到/usr/bin中即可

②创建软链接
```
cd /usr/bin
rm -rf lua luac
ln -s /usr/local/bin/lua /usr/bin/lua
ln -s /usr/local/bin/luac /usr/bin/luac
lua -v
```
Lua 5.3.3  Copyright (C) 1994-2016 Lua.org, PUC-Rio
