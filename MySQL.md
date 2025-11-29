# 命令

```mysql
mysql -hlocalhost -P3306 -uroot -p            > 启动 MySQL 服务器，进入 MySQL 交互模式
mysql -uroot<path                             > 启动 MySQL 提交 sql 脚本命令

SHOW DATABASES;                               > 显示所有数据库
USE 库名;                                     > 进入数据库
SHOW TABLES;                                  > 显示所有的表名
DESC 表名;                                    > 描述表结构
quit;                                         > 退出 MySQL 交互模式
```

# DDL 语句

```mysql
# 数据定义语句
SET NAMES utf8;                                                > 设置客户端连接服务器端的编码为 UTF8
DROP DATABASE IF EXISTS 库名;                                   > 如果存在此数据库，则丢弃
CREATE DATABASE 库名 CHARSET=utf8;                              > 创建数据库并设置服务器端编码为 UTF8
USE 库名;                                                       > 进入数据库
CREATE TABLE 表名(列名 列类型 列约束 自增列,...);                   > 创建表
DROP TABLE 表名;                                                > 如果存在此表，则丢弃

# 数据操作语句
INSERT INTO 表名 VALUES('值',...);                              > 往表中插入数据
UPDATE 表名 SET 列名='新值',... WHERE 列名='值';                  > 往表中更新数据
DELETE FROM 表名 WHERE 列名='值';                                > 删除表中对应的列

# 数据查询语句
SELECT DISTINCT 列名+计算公式 别名,... from 表名 关键字 where 条件 order by 列名 asc/desc;  > 查询数据
SELECT DISTINCT 列名 ...;                                       > 去重查询
SELECT 列名,... FROM 表名 LIMIT M,D;                             > 分页查询 M：起始值 D：数量值
SELECT 列名,... FROM 表名 GROUP BY 列名;                         > 分组查询，分组查询只能查询分组条件和聚合函数
SELECT 列名,... FROM 表名1 INNER JOIN 表名2 ON 外键列名=主键列名;  > 内连接多表查询：所查询的值有NULL的话是自动排除
SELECT 列名,... FROM 表名1 LEFT JOIN 表名2 ON 外键列名=主键列名;   > 左连接多表查询：左侧表中所有记录都显示
SELECT 列名,... FROM 表名1 RIGHT JOIN 表名2 ON 外键列名=主键列名;  > 右连接多表查询：右侧表中所有记录都显示
SELECT 列名,... FROM 表名 WHERE 列名 LIKE '%_';                  > 模糊查询
SELECT 列名,... FROM 表名 WHERE 条件 ORDER BY 列名 ASC/DESC;      > 升降序
SELECT 列名,... FROM 表名 WHERE 条件 AND 条件;                    > 并且
SELECT 列名,... FROM 表名 WHERE 条件 OR 条件;                     > 或
SELECT 列名,... FROM 表名 WHERE 列名 BETWEEN M AND D;            > 查询 M 与 D 之间的数据
SELECT 列名,... FROM 表名 WHERE 列名 NOT BETWEEN M AND D;        > 查询不是 M 与 D 之间的数据
SELECT 列名,... FROM 表名 WHERE 列名 IN(M,D);                    > 查询 M 和 D 的数据
SELECT 列名,... FROM 表名 WHERE 列名 NOT IN(M,D);                > 查询不是 M 和 D 的数据
SELECT 列名,... FROM 表名 WHERE 列名 IS NULL;                    > 查询 NULL 的数据
SELECT 列名,... FROM 表名 WHERE 列名 IS NOT NULL;                > 查询不是 NULL 的数据
SELECT 列名,... FROM 表名 WHERE 列名=(SELECT 语句);               > 子查询
```

# 列类型/列约束

```mysql
# 列类型
CHAR(M)                                           > 定长字符串型（M 的最大值 255，可能会浪费存储空间，响应速度相对快）
VARCHAR(M)                                        > 变长字符串型（M 的最大值 6535，几乎不会浪费存储空间，响应速度相对慢）
TEXT(M)                                           > 大型变长字符串型（M 的最大值能达到 2G）
TINYINT                                           > 微整型（范围：-128 ~ 127）
SMALLINT                                          > 小整型（范围：-32768 ~ 32767）
INT                                               > 整型（范围：-2147483648 ~ 2147483647）
BIGINT                                            > 大整型（范围：-9223372036854775808 ~ 9223372036854775807）
DECIMAL(M,D)                                      > 大整型（范围：-9223372036854775808 ~ 9223372036854775807）
FLOAT                                             > 单精度浮点型（范围比 int 大的多，精度会受到影响）
DOUBLE                                            > 双精度浮点型
BOOLEAN                                           > 布尔型（使用后会自动转成 tinyint 类型）
DATE                                              > 日期型（0000-00-00）
TIME                                              > 时间型（00:00:00）
DATETIME                                          > 日期时间型（0000-00-00 00:00:00）

#列约束
PRIMARY KEY AUTO_INCREMENT                        > 主键约束+自增列（不允许插入重复的值，id 为 null 就会获取最大值+1并插入）
FOREIGN KEY(外键列名) REFERENCES 主键表名(主键列名)  > 外键约束（外键列名值和对应的主键列名值以及列类型要保持一致）
UNIQUE                                            > 唯一约束（不允许出现重复的值，允许插入NULL，甚至多个NULL）
DEFAULT                                           > 默认值约束（1. 使用 default 关键字作为值设置默认值 2. 未输入值的是默认值）
NOT NULL                                          > 非空约束（禁止插入NULL） 
```

