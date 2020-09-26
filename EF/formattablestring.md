**利用FormattableString 重载或者传递参数化变量来防止SQL注入**

- EG:

``` C#
    using (var context=new EFCoreDbContext())
    {
        var searchString="Mr ye";
        FormattableString sql = $@"SELECT Id,Name FROM dbo.Blogs Where Name={searchString}";

        var blogs=context.Blogs
            .FromSql<Blog>(sql)
            .include(d=>d.Posts)
            .ToList();
    }
```
