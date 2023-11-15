# SHOW PROCESSLIST

## 功能

展示当前服务器内运行线程执行的操作。当前版本仅支持展示查询任务。

## 语法

```SQL
SHOW [FULL] PROCESSLIST
```

## 参数说明

| 参数 | 必选 | 说明                                          |
| ---- | ---- |---------------------------------------------|
| FULL | 否   | 如果不指定该参数，则列出 SQL 语句的前 100 个字符。如果指定该参数，则列出完整 SQL 语句。 |

## 返回

| 返回                | 说明                           |
| ------------------- | ------------------------------ |
| Id                  | 连接ID                         |
| User                | 线程所属用户名                 |
| Host                | 发出语句的客户端的主机名       |
| Db                  | 线程所属数据库名               |
| Command             | 线程执行的命令类型             |
| ConnectionStartTime | 连接开始时间                   |
| Time                | 线程处于其当前状态的时间（单位：秒） |
| State               | 线程运行状态                   |
| Info                | 线程正在执行的语句             |

## 注意事项

如果当前用户为 `root`，则列出所有用户正在运行的线程；否则，仅列出当前用户运行的线程。

## 示例

示例一：通过 `root` 用户查看正在运行的线程。

```Plain
SHOW PROCESSLIST;

+------+------+---------------------+-------+---------+---------------------+------+-------+------------------+
| Id   | User | Host                | Db    | Command | ConnectionStartTime | Time | State | Info             |
+------+------+---------------------+-------+---------+---------------------+------+-------+------------------+
|  0   | root | x.x.x.x:xxxx        | tpcds | Query   | 2022-10-09 19:58:25 |    0 | OK    | SHOW PROCESSLIST |
+------+------+---------------------+-------+---------+---------------------+------+-------+------------------+
```