
#表的名称分类
|名称|说明|
|:---|:---|
|工作表|普通的表，存储在用户数据库中，是关系型数据库的主要对象。|
|临时表|* 可以创建全局临时表和本地临时表，全局临时表所有回话都可见，有两个#，本地临时表只在当前会话中可见，表名有一个#。CREATE TABLE #temp_table_name，存储在tempdb数据库中。除非使用DROP TABLE显示删除临时表，否则临时表在推出其作用域时由系统自动删除。建议使用表变量而不是临时表，表变量更有效的查询处理。临时表用在显示创建索引，或者多个存储过程或函数使用表值时，临时表才更有效。|
|table变量|table 变量的行为类似于局部变量，有明确定义的作用域。这就是在其中声明该变量的函数、存储过程或批处理。在存储过程中使用 table 变量与使用临时表相比，减少了存储过程的重新编译量。DELCARE @tb TABLE ( { column_definition | table_constraint } [ ,...n ] ) |
|派生表|派生表是结果集，用作查询的源。|
# DBNull类
DBNull类表示数据库中的NULL字段表示的对象，可以通过DBNull.Value.Equals(object)来判断字段是否为空，其它方法包括 Visual Basic 的 IsDBNull 函数、Convert.IsDBNull 方法、DataTableReader.IsDBNull 方法和 IDataRecord.IsDBNull 方法。

Eval("column_name")返回值的数据类型是System.Object。在将Eval("column_name")作为参数时，需要判断数据库字段是否为NULL。

#SELECT语句的从句和执行顺序
##SELECT语句
```sql
SELECT column_list
FROM table_list
WHERE condition
  [INNER | OUTER] JOIN other_table ON condition
GROUP BY expression
HAVING group_by_condition
ORDER BY order_contition
```
##执行顺序:以下步骤显示 SELECT 语句的处理顺序。
1. FROM
2. ON
3. JOIN
4. WHERE
5. GROUP BY
6. HAVING
7. SELECT
8. DISTINCT
9. ORDER BY
10. TOP

#AdventureWorks销售和营销方案
##客户类型
作为自行车生产公司，Adventure Works Cycles 拥有两种客户：
* 个人。即，从 Adventure Works Cycles 在线商店购买产品的消费者。
* 商店。即，从 Adventure Works Cycles 销售代表处购买产品后进行转售的零售店或批发店。
位客户在 Customer 表中都有一条记录。CustomerType 列指示客户是个人消费者 (CustomerType= 'I') 还是商店 (CustomerType= 'S')。这些客户类型所特有的数据分别在 Individual 和 Store 表中进行维护。
