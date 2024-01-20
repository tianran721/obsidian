brew install mysql@8.0

#### installed your MySQL database without a root password. To secure it run:
    mysql_secure_installation
#### To connect run:

    mysql -u root

#### in your PATH, run:

  echo 'export PATH="/usr/local/opt/mysql@8.0/bin:$PATH"' >> ~/.zshrc

#### system service 

```
brew services start mysql@8.0
brew services stop mysql@8.0
brew services restart mysql
```

-h
-p
-u
-p
exit; = \q = quit