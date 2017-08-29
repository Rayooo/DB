http://www.postgres.cn/docs/9.6/index.html
方括号[]表示可选的部分，花括号{}和|表示必须选取一个候选点，点(...)表示前面的元素可以重复

视图
CREATE VIEW myView AS SELECT xxx FROM xxx WHERE xxx=xxx;

事务
BEGIN;
xxxx
SAVEPOINT my_savepoint;
xxxx
-- ROLLBACK TO my_savepoint;
xxx
COMMIT;


不懂
4.2值表达式
