#### 优化校验规则
- 新建validator包
- 新建ValidationResult文件
- 新建ValidatorImpl文件，传入参数是bean，如果不符合相应规则，constraintViolationSet就会变为非空。当非空时，就要遍历这个set，这里使用了java8中的lambda表达式，取出errMsg和错误路径，返回errMessageMap。
- 在userModel中通过添加注解可以进行校验
- 在userServiceImpl中进行优化，通过validate方法就可以取代之前复杂的校验