

### Controller的使用

| @Controller         | 处理http请求                                                 |
| ------------------- | ------------------------------------------------------------ |
| **@RestController** | **Spring4之后新加的注解，原来返回json需要@ResponseBody配合@Controller** |
| **@RequestMapping** | **配置url映射**                                              |



| **@PathVariable** | **获取url中的数据**  |
| ----------------- | -------------------- |
| **@RequestParam** | **获取请求参数的值** |
| **@GetMapping**   | **组合注解**         |



```
@controller类上面除了注解@Controller以外还可以用什么注解代替？
@RestController


在Spring中，很多注解在用法上是相似的，也有很多的注解命名上很相似，稍不注意就会让人误用，今天就给大家说一下@Controller注解和@RestController这两个注解的用法和区别。
首先，这两个注解的使用位置上都是用在Controller层，作用是用来标注Controller层的组件。相当于Struts中的Action。当然，在作用上，还有@Component，@Respository和@Service这几个注解，他们在应用中是等效，当然，在以后的发展与Spring的版本更新中可能会有区别，这一点暂且不说。
对于今天的重点，@Controller和@RestController的区别，其实@RestController的作用相当与@Controller注解和@ResponseBody注解的同时使用的作用，倘若我们只是使用@RestController注解Controller，则controller中的方法无法返回jsp页面配置的试图解析器。当返回的是对象的时候，通过适应的HttpMessageContext转化为指定格式后，写入到Response对象的Body的数据区中进行返回

```



```
@Component
（把普通pojo实例化到spring容器中，相当于配置文件中的<bean id="" class=""/>）
```











---

---

---

------------------------------------------------------------------------------



## **spring @component的作用详细介绍**

1、@controller 控制器（注入服务）

2、@service 服务（注入dao）

3、@repository dao（实现dao访问）

4、@component （把普通pojo实例化到spring容器中，相当于配置文件中的<bean id="" class=""/>）

　  @Component,@Service,@Controller,@Repository注解的类，并把这些类纳入进spring容器中管理。 

下面写这个是引入component的扫描组件 

```
<context:component-scan base-package=”com.mmnc”> 
```

 其中base-package为需要扫描的包（含所有子包） 

1、@Service用于标注业务层组件 
2、@Controller用于标注控制层组件(如struts中的action) 
3、@Repository用于标注数据访问组件，即DAO组件. 
4、@Component泛指组件，当组件不好归类的时候，我们可以使用这个注解进行标注。    

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
@Service
public class UserServiceImpl implements UserService {

} 

@Repository
public class UserDaoImpl implements UserDao {

} 
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

getBean的默认名称是类名（头字母小写），如果想自定义，可以@Service(“***”)这样来指定，这种bean默认是单例的，如果想改变，可以使用

```
@Service(“beanName”)
@Scope(“prototype”)
public class User {

} 
```

来改变。可以使用以下方式指定初始化方法和销毁方法（方法名任意）：

```
@PostConstruct
public void init() {

}
```