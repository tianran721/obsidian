```
brew update 升级
```

通过Homebrew 安装的软件通常被安装在 **/usr/local/Cellar 目录下**

#### homebrew CRUD
卸载brew
```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/uninstall.sh)" 
```


```
安装 
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

卸载依赖
```
brew remove openjava@11
```

```
brew services list
```

#### Java
java jdk 
```
/usr/local/opt/openjdk@17/libexec/openjdk.jdk
```

#### Mysql
```
database location :
/usr/local/var/mysql
```