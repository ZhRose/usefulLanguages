# HTML

- 音频标签：<  audio src="" control="" autioplay="" loop>

- 视屏标签：<  video src="" control="" autioplay=""muted loop>,部分浏览器配备muted（表示静音）可以实现自动播放

- 超链接标签：< a href="完整网址或者文件路径" target="_black 或_self">前者新开网页标签，后者覆盖原标签

- 列表标签：
	        无序列表：< /ul>该标签中只能添加< li>标签，而< li>标签中可以添加任何内容
	        有序列表：< ol>为起始标签，内容与无序一样
	        自定义列表：< dl>为起始标签，其中只能包裹< dt>和< dd>标签，< dt>为标签标题,< dd>为标签内容，后两者中都可以存放任意内容

- 表格标签
	       表格标签：< table>为起始标签，表格的每行用<tr表示>，每一行中的每一格用< td>表示，三者关系从大到小，表格中的属性boder(边框宽度)，width和height表示表格宽高。表头单元格(每一列的小标题)，用< th>来表示，放在tr里面，表格整体大标题用< caption>表示放在table里面。

	​       表格的结构化：将各个部分内容放在各自标签中，有< thead>< tbody>< tfoot>三种，< tfoot>表示表格底部。

	​       表格的合并：左上原则保留最左边或者最上边的元素，删除其他的，并在相应的标签中添加rowspan跨行标签或者colspan跨列标签。数值为你想合并几个格子数值就为几.

	

	>  表单标签

	应用场景：网页注册和登录界面，以及搜索框

	输入框标签：以< input>标签为起始标签，通过改变其中的type属性达到不同的效果
	type选项：text 基础文本，可以输入任意内容
	         password  密码输入，内容不可见
	         radio  单线框，所选一，通过name属性是否相同来制造单选效果，通过checked表示默认值
	        checkbox  多选框用于多选多
	        file  用于文件选择，上传文件，添加multiple，可以同时上传多个文件
	        submit  提交按钮
	        reset  重置按钮
	        button 默认按钮无功能，通过js添加
	通过添加占位符，达到输入框中有提示文字效果，该属性名为placeholder

	通过在按钮中添加value属性改变按钮上显示的文字，如果需要按钮生效需要整体添加form标签，其中标签中的action属性是提交发送的地址值。

​      下拉菜单标签：以< select>标签为起始标签，select 标签里可以添加任意多个<option>选项，selected为默认选项，添加在option属性里。
​      文本域标签：以< textarea>为起始标签，通过cols和rows设置宽高
​      label标签：绑定内容与标签的关系，用< label>标签将内容包裹，给表单加id属性，给label添加for属性，属性值为id。或者直接将表单标签写进label标签里面，去掉for属性即可
语义标签

> < span>和< div>标签都是无语义的标签
> 有语义的标签，手机端网页制作< header>< nav>< footer>< aside>< section>< article>
> HTML嵌套规范：p标签内尽量不要使用div，p，h等标签，浏览器解析时会自动给你改错，
> a标签里不能嵌套a标签