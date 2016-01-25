#Security
* 对窗体变量、查询字符串和Cookie值执行参数验证。验证包括两个方面，一方面是转换成所需的类型（如整数，日期），另一方面进行数据范围或格式的验证。例如例用Int32.Tryparse检查应为整数的窗体变量，并检查是否在所需的范围内。
* 将值写回响应时，对字符串输出应用HTML编码——HtmlEncode(string)。这将确保输出的字符串以静态文本的形式呈现在浏览器中，而不是可执行脚本。
* 检查输入文本是否含有特殊字符：<!，<?，</。
* 为了防止SQL语句注入，决不能使用串联字符串创建查询语句，相反应该使用参数化查询并将用户输入传递给参数对象。
* 始终对一组预期值执行窗体输入验证以及字符串格式设置/类型验证。
#ASP.NET编译
`aspnet_compiler -v / -p phypath targpath`

#Repeater控件

##CType(e.item.dataitem,**datatype**).item("id")
由于Repeater控件的DataSource属性可以接受任何System.Collections.IEnumerable对象，例如用于访问数据库的System.Data.DataView、System.Collections.ArrayList、System.Collections.Hashtable、数组或IListSource对象，所以在操作DataItem的转型时，首先要弄清楚数据源的类型。如果是把DataTable.DefaultView作为数据源，那么DataItem转型的类型就是DataRowView；如果是把DataReader作为数据源，那么DataItem转型的类型就是System.Data.Common.DbDataRecord。这种转型通常发生在Repeater控件的DataItemBound处理事件中。
##获取控件
CType(e.item.Controls.Item(0), system.Web.UI.DataboundLiteralControl)是一个只读的控件，如果要修改控件必须添加服务器控件，WEB服务器控件或者HTML服务器空间，然后使用如下语句引用控件:CType(e.Item.FindControl("id"), System.Web.UI.HTMLControls.HTMLTableCell)。
普通的控件如`<span runat="server" id="span"`，CType（e.item.findControl("span"),System.Web.UI.HTMLControls.HtmlGenericControl)。

##分页
1. 从数据库提取分页后需要的数据，关键技术有Row_Number() OVER(ORDER BY *column* DESC|ASC) AS RowNumber和派生表（SELECT ...FROM(SELECT ...FROM ...) AS PaiShengBiao WHERE ...)。

2. sqldatasource使用参数，例如QueryString。
3. repeater布局，table thead tbody tfoot，利用bootstrap中的pagination和glyphicon字体。
4. 利用window.location.search传递参数。

#SqlDataSource
##Inserting Event Handle
这个事件在调用Insert（）方法之前发生，调用Insert()方法之后发生Inserted事件。这个事件有一个SqlDataSourceCommandEventArgs类型的传入参数e。
* 控制参数的数值：e.Command.Parameters("@pmName").Value = pmValue

#GridView控件

##RowDataBound事件
* 数据对象：e.Row.DataItem，转型为System.Data.DataRowView，即dr = Ctype(e.Row.DataItem,System.Data.DataRowView)，然后就可以通过dr("id")来访问每一行的字段的数据。
* 控件对象：e.Row.Cells(index)可以访问每一行的某一个控件。
* 行类型：e.Row.RowType

##GridView配置QueryString的值
添加asp:HyperLinkFiled控件，设置DataTextFiled或DataNavigateUrlFields 属性获取数据字段,DataTextField 只能设置为单个数据字段。但 DataNavigateUrlFields 可以设置为一个逗号分隔的数据字段列表。我们经常需要将文本或 URL 赋值为当前行中数据字段值和某个静态标记的组合。

为了生成一个包含静态值和数据驱动值的组合，使用 DataTextFormatString 和 DataNavigateUrlFormatString 属性。在这两个属性中，根据需要输入静态标记，然后在你希望出现字段值的(这个字段值是由DataTextField 或 DataNavigateUrlFields 属性指定的)位置使用标记 {0}。如果 DataNavigateUrlFields 属性有多个指定的字段，则在希望插入第一个字段值的位置使用 {0}，希望插入第二个字段值的位置使用 {1}，依此类推。

##GridView的SelectedRow
* 设置`AutoGenerateSelectButton="true"`或者`<asp:CommandField ShowSelectButton ="true" HeaderText="Select" />`来生产Selected按钮，选择按钮每次被选中，都会一发一次回传，并且GridView的属性SelectedRow被更新。
* SelectedIndex返回选定行的索引。
* SelectedValue返回GridView的DataKeyNames属性的第一个值。
* SelectedDataKey返回GridView选中行的DataKey对象，其中包括该行主键字段的所有值。
* 属性DataKeyNames设置唯一标示GirdView每一行的主键值，常用于通过每个 GridView 行唯一标识底层数据的属性，可以是一个，也可以是多个，多个用逗号隔开。这是**GirdView**属性，可以与数据库的主键字段不同，但如果不同意义不大。

#DetailsView简介
* DetailsView控件是一个数据绑定控件，一次只能显示一条记录，很多操作与GridView相似。
* 通过设置`AllowPaging="true"`可以以分页的形式显示多个数据。
* SqlDataSource中有一个属性**FilterExpression**和**FilterParameters**，可以缓存数据，减少从数据库服务器多次存取大量数据。

#ClientScript以编程方式添加JavaScript
**page.ClientScript.RegisterStartupScript**是把脚本放在**form**的末尾，而**不是body的末尾**。
