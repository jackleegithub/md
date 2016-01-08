#GridView配置QueryString的值
添加asp:HyperLinkFiled控件，设置DataTextFiled或DataNavigateUrlFields 属性获取数据字段,DataTextField 只能设置为单个数据字段。但 DataNavigateUrlFields 可以设置为一个逗号分隔的数据字段列表。我们经常需要将文本或 URL 赋值为当前行中数据字段值和某个静态标记的组合。

为了生成一个包含静态值和数据驱动值的组合，使用 DataTextFormatString 和 DataNavigateUrlFormatString 属性。在这两个属性中，根据需要输入静态标记，然后在你希望出现字段值的(这个字段值是由DataTextField 或 DataNavigateUrlFields 属性指定的)位置使用标记 {0}。如果 DataNavigateUrlFields 属性有多个指定的字段，则在希望插入第一个字段值的位置使用 {0}，希望插入第二个字段值的位置使用 {1}，依此类推。

#DetailsView简介
* DetailsView控件是一个数据绑定控件，一次只能显示一条记录，很多操作与GridView相似。
* 通过设置`AllowPaging="true"`可以以分页的形式显示多个数据。
* SqlDataSource中有一个属性**FilterExpression**和**FilterParameters**，可以缓存数据，减少从数据库服务器多次存取大量数据。