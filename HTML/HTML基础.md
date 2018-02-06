# HTML基础

## HTML标签

### ``Meta`` 标签

用法

- 指定页面编码格式

  ```html
  <meta charset="UTF-8">
  ```

- 设置网页关键字

  ```html
  <meta name="Keywords" content="html基础">
  ```

​       **注意**  :该标签中的关键字不是给用户看的,是给搜索引擎提供的.

- 设置网页描述信息

  ```html
  <meta name="description" content="描述信息">
  ```

- 网页重定向

  ```html
  <meta http-equiv="refresh" content="3; http://www.baidu.com">
  ```

  以上代码表示页面载入后3秒跳转至百度首页.

### ``link`` 标签

用法:

- 设置网页标题

  ```html
  <link rel="icon" href="favicon.ico">
  ```

  **注意** :最好将图标放到网页根目录下

- 设置引用外部样式表

  ```html
  <link rel="stylesheet" type="text/css" href="base.js">
  ```

### 列表标签

#### 无序列表``ul`` 

```html
  <ul>
       	<li>吃</li>
       	<li>喝</li>
       	<li>玩</li>
       </ul>

```

**注意** :

1. 无序列表中的列表项``(li)`` 可以包含任何标签
2. 用于在网页中展示信息

#### 有序列表``ol`` 

```html
 <ol>
       	<li>吃</li>
       	<li>喝</li>
       	<li>玩</li>
</ol>
```

#### 自定义列表``dl`` 

```html
<dl>
	<dt>标题</dt>
	<dd>列表项</dd>
	<dd>列表项</dd>
</dl>

```

**注意** : 

1. ``dt`` 标签中智能包含行内元素(``span`` ,``a`` )
2. ``dd`` 标签中可以包含所有的标签
3. 一般网页结尾处的列表使用自定义列表,如[小米商城](https://www.mi.com/minote/) 

#### 表格``table`` 

1. 组成

   ```html
   行    tr
   列    td
   表格  table		
   ```

2. 作用

   - 显示数据
   - 网页布局

3. 属性

   - border   设置边框
   - width     设置宽度
   - height    设置高度
   - cellspacing   设置td与td之间的距离
   - align    left|center|right   设置对齐方式

   **注意** :

   1. 如果给``table`` 标签设置``align`` 属性，只能让整个标签居中，内容不会居中
   2. 给``tr`` 或者``td`` 设置``align`` 属性，可以让其内容居中

4. 表格中的标签介绍

   - 设置表头`` <th> </th>``  用法与``td`` 相同

   - 设置表格标题

     ```html
     <caption>人员录入表</caption>
     ```

   - 表格结构

     ```html
     <thead></thead>
     <tbody></tbody>
     <tfoot></tfoot>
     ```

   - 合并单元格

     1. 横向合并    ``colspan`` 
     2. 纵向合并    `` rowspan`` 

5. 实例

   ```html
     <table border="1" cellspacing="0" cellpadding="5">
          	<caption>人员录入表</caption>
          	<tr>
          		<td>姓名</td>
          		<td>性别</td>
          		<td>年龄</td>
          	</tr>
          	<tr>
          		<td>wenjian</td>
          		<td>男</td>
          		<td>25</td>
          	</tr>
          	<tr>
          		<td>hello</td>
          		<td>nv</td>
          		<td>23</td>
          	</tr>
          </table>

   ```

### 表单

作用 : 收集用户信息

组成 : 

- 提示信息
- 表单控件(重点)
- 表单域

#### 表单域

```html
    <form action="1.php" method="POST">
       	
    </form>
```

- action: 设置后台处理数据的后台程序
- method: 提交数据给后台程序的方式
  - get提交数据: 会将数据显示在地址栏中
  - post提交数据: 会通过后台提交数据(更加安全)

#### 表单控件

- 文本输入框

  ```html
  <input type="text" name="search">
  ```

  属性 :

  - maxlength             设置最大长度
  - readonly                 设置控件为只读
  - disabled                  禁止用户输入
  - value                        设置默认值(可用``h5`` 新属性``placeholder`` 代替,体验效果更好)
  - name                       控件名称
  - id                              控件编号

  ```HTML
  <input type="text" name="search" maxlength="10" placeholder="请输入搜索关键字" id="s1">
  ```

- 密码输入框

  ```html
  <input type="password" name="psd">
  ```

  属性和文本输入框一致

- 单选控件

  ```html
  <input  type="radio">
  ```

  **注意** : 该控件实现单选效果需要给控件设置相同的name属性

  checked 设置控件默认选中项

  ```html
  	<input type="radio" name="gender" checked="true"> 男

      <input type="radio" name="gender"> 女
  ```

- 下拉列表

  ```html
  	<select>
         		<option>湖南</option>
         		<option>湖北</option>
         		<option>山东</option>
         		<option>山西</option>
      </select>
  ```

  属性 :

  - selected       设置默认选中项

    ```html
    	<select>
           		<option>湖南</option>
           		<option>湖北</option>
           		<option selected>山东</option>
           		<option>山西</option>
           	</select>
    ```

  - multiple        实现多选效果

    ```html
    	<select multiple="true">
           		<option>湖南</option>
           		<option>湖北</option>
           		<option selected>山东</option>
           		<option>山西</option>
        </select>
    ```

  - 分组

    ```html
    <select multiple="true">
           		<optgroup label="湖南">
           		<option>长沙</option>
           		<option>衡阳</option>
           		<option selected>邵阳</option>
           		<option>株洲</option>
           		</optgroup>

           		<optgroup label="广东">
           			<option>深圳</option>
           			<option>广州</option>
           			<option>珠海</option>
           			<option>汕头</option>
           		</optgroup>
           	</select>
    ```

- 多选控件

  ```html
  <input type=”checkbox”>
  ```

  属性 :   checked    设置默认选中项 

  ```html
  	<input type="checkbox" >看书
      <input type="checkbox" checked="true">学习
      <input type="checkbox" >旅游
      <input type="checkbox" >玩游戏
  ```

- 资源上传控件

  ```html
  <input type="file">
  ```

- 文本域

  ```html
  <textarea></textarea>
  ```

- 隐藏控件

  ```html
  <input type="hidden"  value="123">
  ```

- 按钮

  - 提交按钮 

    ```html
    <input type="submit">
    ```

    提交表单数据

  - 普通按钮

    ```HTML
    <input type=”button”>
    ```

    不能提交表单数据

  - 重置按钮

    ```html
    <input type="reset">
    ```

    将数据恢复到默认值

  - 图片提交按钮

    ```html
    <input type="image" src="按钮.jpg">
    ```

    提交表单数据

- 分组控件和标题

  ```html
     	<fieldset>
         		<legend>注册</legend>

         		<input type="text" name="" placeholder="请输入姓名">
         		<br>
         		<br>
         		<input type="password" name="" placeholder="请输入密码">
         		<br>
         		<br>
         		<input type="submit" name="" value="注册">
         	</fieldset>
  ```

### 标签语义化

- 概念:

  根据内容的结构化（内容语义化），选择合适的标签（代码语义化）

- 含义:

  1. 网页结构合理
  2. 有利于seo:和搜索引擎建立良好沟通，有了良好的结构和语义你的网页内容自然容易被搜索引擎抓取
  3. 方便其他设备解析（如屏幕阅读器、盲人阅读器、移动设备）
  4. 便于团队开发和维护

- 注意事项:

  - 尽可能少的使用无语义的标签``div`` 和``span`` ；
  - 在语义不明显时，既可以使用``div`` 或者``p`` 时，尽量用``p`` 。要使用有语义的标签。
  - 不要使用纯样式标签，如：``b`` 、``font`` 、``u`` 等，改用``css`` 设置。
  - 需要强调的文本，可以包含在``strong`` 或者``em`` 标签中``strong`` 默认样式是加粗（不要用``b`` ），``em`` 是斜体（不用``i`` );

​          



​        













  



