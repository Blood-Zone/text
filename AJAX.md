# AJAX

- AJAX需要运行在网站环境下



### node.js安装

![image-20201001222734670](C:\Users\86139\AppData\Roaming\Typora\typora-user-images\image-20201001222734670.png)



**命令行工具 Windows PowerShell**



![image-20201001223120499](C:\Users\86139\AppData\Roaming\Typora\typora-user-images\image-20201001223120499.png)

查看当前安装的node版本



### AJAX运行原理

![image-20201001093824828](C:\Users\86139\AppData\Roaming\Typora\typora-user-images\image-20201001093824828.png)

由AJAX帮助浏览器向服务端发送请求，由AJAX帮助浏览器接受响应到服务端的数据。接受到响应的数据后，用DOM方法将服务器端发送过来的数据内容，添加到网页当中，这样子就可以实现用户边浏览网站，边向服务器端请求数据，并实现页面无刷新更新数据。





#### AJAX的实现步骤

- 创建AJAX对象

- ~~~JavaScript
    var xhr = new XMLHttpPequest();
    JavaScript的内置构造函数XMLHttpPequest()，创建此构造函数的实例对象，就是在创建Ajax对象
    
    XML：服务器端与客户端传输内容的数据格式；
    （现在服务器端返回给客户端一般都是JSON格式）
    HttpPequest：HTTP请求；
    ~~~

- 告诉Ajax请求地址以及**请求方式**（服务器端对应的路由请求地址）

    ~~~JavaScript
    xhr.open('get/post','url');
    xhr.open('get','http://www.example.com');
    ~~~

- 发送请求

    ~~~javas
    xhr.send();
    ~~~

- 获取服务器端给客户端的响应数据

    ~~~JavaScript
    xhr.onload = function(){
        console.log(xhr.responseText);
    }
    ~~~

    由于请求受网络速度快慢的影响，是需要一定的时间才能完成的，这个时间是一个不确定的时间。所以我们不能在send()方法的后面直接获取请求的结果，我们需要对xhr对象下的onload事件，添加事件处理函数。

    当服务器端对客户端做出了响应，浏览器就会自动调用xhr下面的onload事件对应的事件处理函数，在事件处理函数中，我们就可以获取服务器端响应给客户端的数据了。我们可以通过xhr对象下的responseText属性获取服务器端响应的数据。



先开启网站服务器，这样我们才可以以域名的方式访问静态资源文件

Ajax代码也属于js代码，也要写在<script></script>标签内部



向服务器端发送Ajax请求

![image-20201001111018424](C:\Users\86139\AppData\Roaming\Typora\typora-user-images\image-20201001111018424.png)



####  06、请求参数传递

~~~JavaScript
//GET请求方式
xhr.open('get','http://www.example.com?name=zhangsan&age=20');

//POST请求方式
xhr.setRequestHeader('Content-Type','application/x-www-form-urlencoded')
xhr.send('name=zhangsan&age=20');

~~~



#### 07、请求报文

- 在HTTP请求和响应的过程中传递的数据块就叫<font color="red">报文</font>，包括要传送的数据和一些附加信息，这些数据和信息要遵守规定好的格式

![image-20201001151048886](C:\Users\86139\AppData\Roaming\Typora\typora-user-images\image-20201001151048886.png)



#### 08、请求参数的格式

~~~JavaScript
//1、application/x-www-form-urlencoded
name=zhangsan&age=20&sex=男

//2、application/json
{name: 'zhangsan', age: '20', sex: '男'}
~~~

- 在请求头中指定Content-Type属性的值是application/json，告诉服务器端当前请求参数的格式是json；



~~~JavaScript
JSON.stringify()	//将json对象转换为json字符串
JSON.parse()	//将json字符串转换为json对象
~~~



#### 09、获得服务器端的响应

- **Ajax状态码**

    - 在创建Ajax对象，配置Ajax对象，发送请求，以及接收完服务器端响应数据，这个过程中的每一步骤都会对应一个数值，这个数值就是Ajax状态码；
    - 0：请求未初始化（还未调用open()）

    - 1：请求已经建立，但还没有发送（调用了open()，但还没有调用send()）

    - 2：请求已经发送（已调用send()方法）

    - 3：请求正在处理中，通常响应中已经有部分数据可以用了

    - 4：响应已经完成，可以获取并使用服务器的响应了

    ~~~JavaScript
    xhr.readyState	//获取Ajax状态码
    ~~~

- **onreadystatechange事件**

    - 当Ajax状态码发生变化时将自动触发该事件

    ~~~javascript
    //当Ajax状态码发生变化的时候触发
    xhr.onreadystatechange = function(){
    	console.log(xhr.readyState);
    }
    ~~~

    

![image-20201001153758613](C:\Users\86139\AppData\Roaming\Typora\typora-user-images\image-20201001153758613.png)

~~~JavaScript
function getAjaxDate() {
	let xhr = new XMLHttpRequest();
    xhr.open("get", "a.txt", false);
    xhr.onreadystatechange = function () {
    if (xhr.readyState == 4 && xhr.status == 200) {
    	let date = xhr.responseText;
        document.body.innerHTML = date;
    	}
    }
        xhr.send();
}
getAjaxDate();
~~~



#### 10、AJAX错误处理

- status方法
    - status(状态码)
    - ![image-20201002165913705](C:\Users\86139\AppData\Roaming\Typora\typora-user-images\image-20201002165913705.png)

500：服务器端错误

- Ajax状态码：表示Ajax请求的过程状态，是Ajax对象返回的；
- HTTP状态码：表示请求的处理结果，是服务器端返回的；



#### 12、Ajax异步编程

- 同步：一行代码执行后，才能执行下一行代码，代码逐步执行；

    ![image-20201002170748186](C:\Users\86139\AppData\Roaming\Typora\typora-user-images\image-20201002170748186.png)

- 异步：![image-20201002170721597](C:\Users\86139\AppData\Roaming\Typora\typora-user-images\image-20201002170721597.png)

使用<font color="red">Ajax发送请求是异步代码</font>，当请求发送以后，程序不会等待请求发送的结果，而是直接取执行请求下面的代码，当执行完下面的代码后，再返回看请求的结果；



事件处理函数也是回调函数的一种



### Ajax 封装

![image-20201002171801430](C:\Users\86139\AppData\Roaming\Typora\typora-user-images\image-20201002171801430.png)

- type：请求方式；
- url：请求地址；
- success：代表请求成功后，处理请求结果的函数，在其中，形参data就是请求结果；

![image-20201002172430665](C:\Users\86139\AppData\Roaming\Typora\typora-user-images\image-20201002172430665.png)

![image-20201002172902335](C:\Users\86139\AppData\Roaming\Typora\typora-user-images\image-20201002172902335.png)





## <font color="red">$.ajax()</font>

#### $.ajax()方法概述

- 作用：发送Ajax请求；
- ![image-20201002173215545](C:\Users\86139\AppData\Roaming\Typora\typora-user-images\image-20201002173215545.png)
- 属性：
    - **type**：请求方式（get / post）
    - **url**：请求地址
    - **data**：向服务器端发送的请求参数，可以是对象，也可以是字符串；
    - **contentType**：你想向服务器端传递的参数的格式类型：
        - 默认值“application/x-www-form-urlencoded”；
        - json格式是“application/json”；
    - **beforeSend**：允许在请求发送之前做的事情；
    - **success**：在请求成功，服务器端返回数据之后，这个函数会被调用，函数内部的形参，就是返回的数据；
    - **error**：在请求失败后，执行的函数，我们可以在这个对象中获取错误信息，并且根据此信息进行错误处理；

//$.ajax 会自动将格式转换为json格式

![image-20201002174257604](C:\Users\86139\AppData\Roaming\Typora\typora-user-images\image-20201002174257604.png)



- 请求地址写法：
    - 域名、协议、端口相同的情况下，前面的“http://localhost:5500”可以省略



### <font color="red">serialize()方法</font>

- **作用**：将表单中的数据自动拼接成字符串类型的参数

- ~~~javascript
    var params = $('#form').serialize();
    //name=zhangsan&age=33
    ~~~



类似formData

![image-20201005155512117](C:\Users\86139\AppData\Roaming\Typora\typora-user-images\image-20201005155512117.png)



#### 自定义封装函数（将表单中用户输入的内容转换为对象类型）

~~~html
<--! HTML Part -->
<form id="formtext">
    <input type="text" name="username"/>
    <input type="password" name="password"/>
	<input type="submit" value="提交"/>
</form>
<br/><br/>
<script src="../jQuery.js"></script>
~~~



~~~javascript
//JavaScript Part
$("#formtext").on('submit',function(){
	serializeObject($(this));
    console.log(serializeObject($(this)));
    return false;
});

//将表单中用户输入的内容转换为对象类型
function serializeObject(obj){
    //处理结果对象
	var result = {};
    //name即是<input>里name属性所对应的值
    /*[{name:'username', value:'用户输入的内容'}
    {name:'password', value:'用户输入的内容'},]*/
    var params = obj.serializeArray();

    //$.each()用来循环数组或者对象的，index当前循环的索引（从零开始），value为当前循环的元素
    //循环数组 将数组转换为对象类型
    $.each(params,function(index,value)
    {
    	result[value.name] = value.value;
    });
    	//将处理的结果返回到函数外部（谁调用此函数，就返回给谁）
        return result;
}
~~~



<img src="C:\Users\86139\AppData\Roaming\Typora\typora-user-images\image-20201005163012638.png" alt="image-20201005163012638" style="zoom:60%;float:left;" />



### $.get() 方法

- 作用：用于发送get请求



### $.post() 方法

- 作用：用于发送post请求



![image-20201005163944922](C:\Users\86139\AppData\Roaming\Typora\typora-user-images\image-20201005163944922.png)



![image-20201005164149665](C:\Users\86139\AppData\Roaming\Typora\typora-user-images\image-20201005164149665.png)



#### ToDoList

![image-20201005164925737](C:\Users\86139\AppData\Roaming\Typora\typora-user-images\image-20201005164925737.png)

![image-20201005165119876](C:\Users\86139\AppData\Roaming\Typora\typora-user-images\image-20201005165119876.png)







#### 腾坤提出的注意点

在浏览网页的时候你们可以学习一下他们的url是怎么写的：

比如B站的 https://www.bilibili.com/video/BV1J4411877m?p=420

然后因为url中出现中文会乱码 所以基本都会转码成16进制的，以%开头

mysql点赞表和评论表设计 ==>

mysql%E7%82%B9%E8%B5%9E%E8%A1%A8%E5%92%8C%E8%AF%84%E8%AE%BA%E8%A1%A8%E8%AE%BE%E8%AE%A1

转码的话js用一个encodeURIComponent(string)函数就够了











 

![image-20201001132641961](C:\Users\86139\AppData\Roaming\Typora\typora-user-images\image-20201001132641961.png)



- <font color="red">**VScode**</font>：放在JavaScript.json里的快捷方式

~~~javascript
"ajax快捷方式": {
		"prefix": "ajax",
		"body": [
			"//其他参数:beforeSend在发送之前可以使用return false取消,timeout超时时间,error,async同步还是异步",
			"$.ajax({",
    		"\ttype:'$1',//get或post",
    		"\turl:'$2',//请求的地址",
    		"\tdata:{},//如果不需要传，则注释掉 请求的参数，a=1&b=2或{a:1,b:2}或者jq中的serialize方法，或者formData收集",
    		"\tdataType:'json',//text,json,xml,jsonp",
			"\tsuccess:function(res){//成功的回调函数",
			"\t\tconsole.log(res)",
			"\t}",
			"})"
		]
	}
~~~







