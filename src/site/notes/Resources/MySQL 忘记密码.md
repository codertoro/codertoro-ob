---
{"type":"quick_note","tags":["quick_note"],"author":"codertoro","establish":"2025-05-15 08：50：23","update":"2025/05/15 08:50","dg-publish":true,"permalink":"/Resources/MySQL 忘记密码/","dgPassFrontmatter":true,"created":"2025-05-15T08:50:23.535+08:00","updated":"2025-05-15T08:51:02.353+08:00"}
---

MySQL 忘记密码时，可以通过“**跳过权限表**”的方式重置 root 密码。下面是操作步骤（适用于 MySQL 8.x）：

---

## ✅ 步骤一：停止 MySQL 服务

- **Linux**：
    
    ```bash
    sudo systemctl stop mysql
    ```
    
- **Windows**：  
    打开“服务”，找到 **MySQL**，点击右键选择“停止”。
    

---

## ✅ 步骤二：以“跳过权限表”的方式启动 MySQL

- **Linux**：
    
    ```bash
    sudo mysqld --skip-grant-tables --skip-networking &
    ```
    
- **Windows**：  
    找到 `mysqld.exe` 所在目录，在命令行执行：
    
    ```cmd
    mysqld --console --skip-grant-tables --skip-networking
    ```
    
    > ⚠️ 注意：此时不要关闭命令行窗口。
    

---

## ✅ 步骤三：另开一个终端，登录 MySQL

```bash
mysql -u root
```

由于跳过了密码验证，这时可以直接进入。

---

## ✅ 步骤四：修改 root 密码（MySQL 8.x）

```sql
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY '新密码';
FLUSH PRIVILEGES;
```

例如：

```sql
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY '123456';
```

---

## ✅ 步骤五：退出并重启 MySQL

先关闭跳过权限表的 MySQL 进程，再正常重启服务：

- **Linux**：
    
    ```bash
    sudo systemctl stop mysql
    sudo systemctl start mysql
    ```
    
- **Windows**：  
    在任务管理器中结束 mysqld 进程，然后从“服务”中重新启动 MySQL。
    

---

## ✅ 步骤六：验证登录

```bash
mysql -u root -p
```

输入刚设置的新密码。

---

如有需要，我也可以帮你写成 Obsidian 里的格式（支持 callout、代码块、注释等），是否需要？