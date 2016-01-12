
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
