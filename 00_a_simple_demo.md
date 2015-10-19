# 一个简单的`jQuery Validation`例子

`jQuery Validation`是一个基于`jQuery`的表单验证插件，它封装了常见表单输入的验证。

下面看一个简单的例子：

```
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0, user-scalable=no">
	<title>表单模块</title>
    <link rel="stylesheet" href="css/reset.css"> 
    <link rel="stylesheet" href="css/form.css">
</head>
<body>
	<form id="demo" name="demo" class="m-form">
         <div class="normalInput">
            <input id="username" name="username" type="text" placeholder="用户名">
         </div>
         <div class="normalInput">
            <input id="email" name="email" type="text" placeholder="常用邮箱">
         </div>
         <div class="normalInput">
            <input class="ignore" id="address" name="address" type="text" placeholder="居住地址">
         </div>
         <div id="tips" class="tips">提示信息</div>   
         <button class="btn">提&nbsp;交</button>
    </form>
    <script src="js/jquery.min.js"></script>
    <script src="js/jquery.validate.min.js"></script>
    <script> 
    var validator = $("#demo").validate({ 
    		//设置验证规则
	    	rules:{ 
	                   username:{ 
	                        required: true 
	                   },
	                   email:{
	                        required: true,
	                        email: true
	                   },
	                   address:{
	                        required: true
	                   }
	            },
	         //设置提示信息
             messages: {
                    username:{ 
                        required: "用户名不能为空" 
                   },
                   email:{
                        required: "邮箱不能为空",
                        email: "邮箱格式错误"
                   }
            },
            errorPlacement: function(error, element) {
                var msg = error.text();
                console.log(msg);
                $("#tips").html(msg);
                console.log("***********"); 
            }  
        });
    </script>
</body>
</html>
```

- 加入`reset.css form.css`
- `rules`选项表示设置规则，`messages`表示设置自定义提示信息。
- `errorPlacement`不是必须的，它可以用来设置提示信息的位置。这里我们将所有的提示信息都放在了一个地方。

你可以在demo/a_simple_demo.html中看到这个例子
