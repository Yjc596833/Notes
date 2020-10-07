[微软官网](https://docs.microsoft.com/zh-cn/aspnet/core/mvc/views/view-components?view=aspnetcore-3.1)

```
public class PriorityList : ViewComponent
{
    public IViewComponentResult Invoke(int maxPriority, bool isDone)
    {
        var items = new List<string> { $"maxPriority: {maxPriority}", $"isDone: {isDone}" };
        return View(items);
    }
}

```