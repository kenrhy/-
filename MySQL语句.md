##### 视图
CREAT VIEW *viewname* AS *select语句* <br>
##### case用法
[mysql操作查询结果case when then else end用法举例](https://www.cnblogs.com/clphp/p/6256207.html)<br>
1.简单case函数：CASE *colum* WHEN *value1* THEN *result-value1* WHEN *value2* THEN *result-value2* ELSE *result-value* END
2.case搜索函数：CASE WHEN *colum-value满足1* THEN *result-value1* WHEN *colum-value满足2* THEN *result-value2* ELSE *result-value* END
##### 全链接（FULL OUT JOIN）
MySQL没有全链接函数，可以使用**union**+左右（left right）外连完成，需要考虑主键选择，多表需要多个主键的union。<br>
例如：3个表数据融合 select t1.nid, case when t1.value is null then 0 else t1.value end as value1, case when t2.value is null then 0 else t2.value end as value2, case when t3.value is null then 0 else t3.value end as value3 from t1 **left** join t2 on t1.nid = t2.nid **left** join t3 on t2.nid = t3.nid <br>
union <br>
select t2.nid, case when t1.value is null then 0 else t1.value end as value1, case when t2.value is null then 0 else t2.value end as value2, case when t3.value is null then 0 else t3.value end as value3 from t1 **right** join t2 on t1.nid = t2.nid **left** join t3 on t2.nid = t3.nid <br>
union <br>
select t3.nid, case when t1.value is null then 0 else t1.value end as value1, case when t2.value is null then 0 else t2.value end as value2, case when t3.value is null then 0 else t3.value end as value3 from t1 **right** join t2 on t1.nid = t2.nid **right** join t3 on t2.nid = t3.nid ;<br>
##### 执行sql脚本
1.terminal命令行：mysql -h${HOSTNAME}  -P${PORT}  -u${USERNAME} -p${PASSWORD} ${DBNAME} <{sql脚本文件路径} **[-e "SQL语句"]** >{输出文件路径}<br>
例如：[zkpk@master mysqltest]$ mysql -u root -D test < fulljoin.sql >out <br>
2.MySQL控制台：Mysql>source 【sql脚本文件的路径全名】 或 Mysql>\. 【sql脚本文件的路径全名】<br>
例如：mysql> source /home/zkpk/mysqltest/fulljoin.sql <br>
##### 数据导入导出
1.导入：<br>
（1）terminal命令行：[mysqlimport — A Data Import Program](https://dev.mysql.com/doc/refman/8.0/en/mysqlimport.html)<br>
shell> mysqlimport [options] db_name textfile1 [textfile2 ...] *文件名*需要和已存在的*表名***一致**<br>
例如：[zkpk@master mysqltest]$ mysqlimport -u root --local test t1.csv <br>
（2）MySQL控制台：[LOAD DATA INFILE Syntax](https://dev.mysql.com/doc/refman/8.0/en/load-data.html)<br>
LOAD DATA [LOW_PRIORITY | CONCURRENT] [LOCAL] INFILE 'file_name' [REPLACE | IGNORE] INTO TABLE tbl_name ... <br>
例如：mysql> load data local infile '/home/zkpk/mysqltest/t1.csv' into table t1;<br>
2.导出：<br>
（1）terminal命令行：见执行sql脚本。<br>
（2）MySQL控制台：<br>
方法1：命令into outfile<br>
例如：mysql> select * from testv into outfile '/home/zkpk/mysqltest/out';<br>
报错：ERROR 1 (HY000): Can't create/write to file '/data/test.xls' (Errcode: 13)<br>
但是如果仅在当前目录下输出：select * from testv  into outfile **'out.csv'** FIELDS TERMINATED BY '\t' LINES TERMINATED BY '\n';则可以导出，如果没有在配置文件/etc/my.cnf文件中指定tmpdir，则导出到datadir中。
方法2：pager cat > '/home/zkpk/mysqltest/out' 输出到指定文件。以表的形式overwrite输出。 nopager（\n）取消。<br>
方法3：tee(\T) 可以指定输出文件，append形式输出命令和结果。notee（\t）取消。<br>
##### 杂项
[Mysql高并发优化](https://www.cnblogs.com/wangchaozhi/p/5061378.html)<br>
[知乎：MySQL 学习路线是怎样的？有哪些学习资料或网站推荐？](https://www.zhihu.com/question/20931204)<br>
