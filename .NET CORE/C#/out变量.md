C# **6**
```c#
string n="42";
int result;
if(string.TryParse(n,out result))
{
    console.writeLine($"successful:{result}");
}
```

C# **7**
```c#
string n="42";
if(string.TryParse(n,out var result))
{
    console.writeLine($"successful:{result}");
}
```