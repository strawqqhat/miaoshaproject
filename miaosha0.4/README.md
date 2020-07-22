#### 获取验证码getotp
- 首先在UserController中天下url路径，通过random生成，将生成的验证码同对应用户的手机号关联，使用HTTP session的方式绑定(分布式应用使用Redis最合适)。
#### 注册
***UserController***
- 在UserController中添加url路径，传入参数包括手机，验证码，用户名，用户性别，年龄，密码信息。inSessionOtpCode是从session中获取的otpCode，将其同传入参数进行对比以校验验证码是否正确。
- 注册过程中，新建userModel，并将对应属性值set一下，最后调用userService中的register方法。返回正确状态。

***userService/impl***
- 传入参数为userModel，首先判断userModel是否为空，若空则抛出参数异常。接着判断传入参数的各个属性(姓名，年龄等)是否为空，若空则同样抛出异常。
- 注册时，新建userDO对象，因为实际与数据库通信的是dataobject，其中构造了一个转换方法convertFromModel，userDOMapper.insertSelective(userDO);将userDO插入数据库中，不要忘记还要把密码插入到数据库中。
- 这过程中有一个跨域访问的问题，解决方法是userController中添加：@CrossOrigin(allowCredentials = "true", allowedHeaders = "*")。对应的html页面中加上xhrFields:{withCredentials:true},
#### 登录
- 在userController上加入url路径，传入参数为手机号和密码。首先验证非空，接着校验用户登录是否合法，service层创建validateLogin方法。
- 登录成功后将登录凭证加入到用户登录成功的session中。
```
UserVO userVO = convertFromMode(userModel);
this.httpServletRequest.getSession().setAttribute("IS_LOGIN",true);
this.httpServletRequest.getSession().setAttribute("LOGIN_USER",userModel);
```