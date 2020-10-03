[博文](https://www.cnblogs.com/guojian/p/3760989.html)

IActionFilter提供的两种方法： **OnActionExecuting 在调用操作方法前调用**  。OnActionExecuted 在调用操作方法后调用。

IResultFilter提供的两种方法：OnResultExecuting 在执行由操作方法返回的操作结果前调用。OnResultExecuted 在执行由操作方法返回的操作结果后调用。

IAuthorizationFilter是一个用于身份验证的Filter。只提供了一个void OnAuthorization(AuthorizationContext filterContext)方法。

IExceptionFilter会在出现异常的时候调用，也是只提供一个void OnException(ExceptionContext filterContext)的方法；

而4个接口的方法执行顺序如下：IAuthorizationFilter -> IActionFilter - >IResultFilter ->IExceptionFilter
