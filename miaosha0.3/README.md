#### otp短信获取
#### otp注册用户
#### 用户手机登录
```
//需要按照一定的规则生成otp验证码
Random random = new Random();
int randomInt = random.nextInt(99999);
randomInt += 10000;
String otpCode = String.valueOf(randomInt);

//将otp验证码同对应用户的手机号关联,使用httpsession的方式绑定手机号和otpcode
httpServletRequest.getSession().setAttribute(telphone, otpCode);

//将otp验证码通过短信通道发送给用户，暂且省略
System.out.println("telphone = " + telphone + " & otpCode = " + otpCode);

return CommonReturnType.create(null);
```