<!--
 * @Author: your name
 * @Date: 2020-09-27 09:40:19
 * @LastEditTime: 2020-09-27 15:08:06
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: \Notes\EF\formattablestring.md
-->
**利用FormattableString 重载或者传递参数化变量来防止SQL注入**

- ## core2.0 EG:

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
- ## core3.0 EG:


如果连接和内插的字符串 ($"") 带有用户提供的未经验证的值，则切勿将其传递到 
FromSqlRaw或ExecuteSqlRaw.
通过 $\color{red}{FromSqlInterpolated}$和$\color{red}{ExcuteSqlInterpolaterd}$方法，可采用一种能抵御SQL注入攻击的方式使用**字符串内插语法**
