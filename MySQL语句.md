##### 视图
CREAT VIEW *viewname* AS *select语句* <br>
##### case用法
[mysql操作查询结果case when then else end用法举例](https://www.cnblogs.com/clphp/p/6256207.html)<br>
1.简单case函数：CASE *colum* WHEN *value1* THEN *result-value1* WHEN *value2* THEN *result-value2* ELSE *result-value* END
2.case搜索函数：CASE WHEN *colum-value满足1* THEN *result-value1* WHEN *colum-value满足2* THEN *result-value2* ELSE *result-value* END
##### 全链接（FULL OUT JOIN）
MySQL没有全链接函数，可以使用**union**+左右（left right）外连完成，需要考虑主键选择，多表需要多个主键的union。<br>
##### 杂项
[Mysql高并发优化](https://www.cnblogs.com/wangchaozhi/p/5061378.html)
