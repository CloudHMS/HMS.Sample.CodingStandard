## Coding Practices
1. **Single** class **single** file.
2. **Single** file contribute **single** namespace.
3. **Avoid** files with more than **500 lines** (except auto-generated).
4. **Avoid** methods with more than **200 lines**.
5. **Avoid** methods with more than **5 arguments**. Use structures for passing multiple arguments.
6. Lines should **not** exceed **120 characters**.
7. **NO** editing **auto-generated** manually. Use partial classes instead.
8. Avoid comments that explain the obvious. Code should be self-explanatory. 
> Good code with readable variable and method names should not require comments.
9. Document only operational assumptions, algorithm insights, and so on.
10. Avoid method-level documentation.
- Use extensive external documentation for API documentation.
- Use method-level comments only as tool tips for other developers.
11. Never hard-code a concrete value; always declare a **constant** instead.
12. Use the **const** directive only on natural constants such as the number of days of the week.
13. Avoid using const on read-only variables. For that, use the readonly directive.
```csharp
public class MyClass
{   
    public const int DAYS_OF_WEEK = 7;
    public readonly int Number;
    
    public MyClass(int someValue)   
    {
        Number = someValue;   
    }
}
```
14. In general, prefer overloading to default parameters:
```csharp
//Correct
class MyClass{
    void MyMethod()   
    {
        MyMethod(123);
    }
    
    void MyMethod(int number)
    {...}
}
//Avoid
class MyClass{
    void MyMethod(int number = 123)   
    {...}
}
```
15. When using default parameters, restrict them to natural immutable constants such as **null, false, or 0**
```csharp
void MyMethod(int number = 0)
{...}
void MyMethod(string name = null)
{...}
void MyMethod(bool flag = false)
{...}
```
16. Every line of code should be walked through in a "white box" testing manner
17. Catch only exceptions for which you have explicit handling.
18. In acatch statement that throws an exception, always throw the original exception(or another exception constructed from the original exception) to maintain the stack location of the original error
```csharp
catch(Exception exception)
{
    MessageBox.Show(exception.Message);
    throw;
}
```
19. Avoid error codes as method return values (except for the return of a part of API result).
20. When defining custom exceptions:
- Derive the custom exception from Exception.
- Provide custom serialization.
21. Avoid multiple **Main()** methods in a single assembly.
22. Make only the most necessary types **public**, mark others as **internal**.
23. Avoid friend assemblies as they increase inter-assembly coupling.
24. Minimize code in application assemblies (EXE client assemblies). Use class libraries instead to contain business logic.
> **IMPORTANT**.
25. Providing explicit values for enums
```csharp
// Correct
public enum Color
{
    Red= 1,
    Green =2,
    Blue=3
}
// Avoid
public enum Color
{
    Red,
    Green,
    Blue
}
```
> This rule is different with original iDesign
26. Avoid specifying a type for an enum.
```csharp
// Avoid
public enum Color : long
{
    Red,
    Green,
    Blue
}
```
27. Always use a curly brace scope in an if statement, even if it conditions a single statement.
28. Using the ternary conditional operator.
> This rule is different with original iDesign.
29. Avoid explicit code exclusion of method calls (#if...#endif). Use conditional methods instead
```csharp
[Conditional("MySpecialCondition")]
public void MyMethod()
{...}
```
30. Avoid function calls in Boolean conditional statements. Assign into local variablesand check on them.
```csharp
bool IsEverythingOK()
{...}
// Correct
bool ok = IsEverythingOK();
if (ok)
{...}
// Avoid
if(IsEverythingOK())
{...}
```
31. Always use zero-based arrays.
32. With indexed collection, use zero-based indexes.
33. Always explicitly initialize an array of reference types using a for loop.
```csharp
public class MyClass
{...}

const int ArraySize = 100;
MyClass[] array = new MyClass[ArraySize];
for (int index = 0;index < array.Length;index++)
{
    array[index] = new MyClass();
}
```
34. Do not provide public or protected member variables. Use properties instead.
35. Avoid explicit properties that do nothing except access a member variable. Use automatic properties instead
```csharp
// Correct
class MyClass
{
    public int Number { get; set; }
}
// Avoid
class MyClass
{
    int m_Number;
    
    public int Number  
    {
        get 
        {
            return m_Number;
        }
        set 
        {
            m_Number = value;      
        }
   }
}
```
36. Avoid using the new inheritance qualifier. Use override instead.
37. Never use unsafe code, except when using interop.
38. Avoid explicit casting. Use the as operator to defensively cast to a type.
```csharp
Dog dog = new GermanShepherd();
GermanShepherd shepherd = dog as GermanShepherd;if (shepherd != null)
{...}
```
39. Always check a delegate fornull before invoking it.
> **IMPORTANT**.