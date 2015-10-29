# 一个简单的例子

jQuery Validation 是一个基于`jQuery`的表单验证插件，它封装了常见表单输入的验证。

下面看一个简单的例子： 

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>jQuery Validation 简单Demo</title> 
</head>
<body>
    <h1>jQuery Validation 简单Demo</h1>
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
                   },
                   address:{
                        required: function(rule, form){
                            return "地址不能为空";
                        }
                   }
            }        
        });
    </script>
</body>
</html>
```

上面有用户名和邮箱字段，并设置了用户名和邮箱都不能为空，并且邮箱要符合邮箱格式。并且为每种错误情况都设置了对应的自定义提示信息。其中：

- `rules`选项表示设置规则，`messages`表示设置自定义提示信息。 

你可以在[这里](http://chanshuyi.github.io/jquery_validation_notebook/demo/00_a_simple_demo.html)看到这个Demo。
