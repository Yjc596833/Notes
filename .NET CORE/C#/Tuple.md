[博客](https://www.cnblogs.com/unity3ds/p/11641582.html)

``` c#
static void WriteStudentInfo(Object student)
{
    var studentInfo = student as Tuple<string, int, uint>;
    Console.WriteLine($"Student Information: Name [{studentInfo.Item1}], Age [{studentInfo.Item2}], Height [{studentInfo.Item3}]");
}
```