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
