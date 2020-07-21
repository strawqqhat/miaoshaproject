#### UserController

#### BaseController

#### CommonError

#### EmBusinessError

#### BusinessException

#### CommonReturnType


1. 首先定义CommonReturnType,用对应status加data的方式返回所有json序列化方式的固定的对象，供前端解析使用。摒弃了使用http status code加内嵌Tomcat自带error页的方式去处理。

2. 定义BusinessError统一管理错误码

3. 在BaseController中定义一个通用的exceptionHandler类解决未被controller层吸收的exception。使用统一的erCode+errMsg吸收所有的异常。