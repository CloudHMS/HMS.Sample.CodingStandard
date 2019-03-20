# CODING PRACTICES

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

11. Never hard-code a concrete value; always declare a `const` instead.

12. Use the `const` directive only on natural constants such as the number of days of the week.

13. Avoid using `const` on read-only variables. For that, use the `readonly` directive.
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
class MyClass 
{
    void MyMethod()
    {
        MyMethod(123);
    }

    void MyMethod(int number)
    {...}
}

//Avoid
class MyClass
{
    void MyMethod(int number = 123)
    {...}
}
```

15. When using default parameters, restrict them to natural immutable constants such as `null`, `false`, or `0`
```csharp
void MyMethod(int number = 0)
{...}

void MyMethod(string name = null)
{...}

void MyMethod(bool flag = false)
{...}
```

16. Every line of code should be walked through in a "white box" testing manner.

17. `catch` only exceptions for which you have explicit handling.

18. In acatch statement that throws an exception, always throw the original exception (or another exception constructed from the original exception) to maintain the stack location of the original error
```csharp
catch(Exception exception)
{
    MessageBox.Show(exception.Message);
    throw;
}
```

19. Avoid error codes as method return values (except for the return of a part of API result).

20. When defining custom exceptions:
- Derive the custom exception from `Exception`.
- Provide custom serialization.

21. Avoid multiple `Main()` methods in a single assembly.

22. Make only the most necessary types `public`, mark others as `internal`.

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

26. Avoid specifying a type for an `enum`.
```csharp
// Avoid
public enum Color : long
{
    Red,
    Green,
    Blue
}
```

27. **Always** use a curly brace `{}` scope in an if statement, even if it conditions a single statement.

28. Using the ternary conditional operator.
> This rule is different with original iDesign.

29. Avoid explicit code exclusion of method calls `#if...#endif`. Use conditional methods instead
```csharp
[Conditional("MySpecialCondition")]
public void MyMethod()
{...}
```

30. Avoid function calls in `Boolean` conditional statements. Assign into local variablesand check on them.
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

const int ARRAY_SIZE = 100;
MyClass[] array = new MyClass[ARRAY_SISZE];
for (int index = 0; index < array.Length; index++)
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

36. Avoid using the `new` inheritance qualifier. Use `override` instead.

37. Never use unsafe code, except when using interop.

38. Avoid explicit casting. Use the as operator to defensively cast to a type.

```csharp
Dog dog = new GermanShepherd();

GermanShepherd shepherd = dog as GermanShepherd;
if (shepherd != null)
{...}
```

39. Always check a delegate fornull before invoking it.

> **IMPORTANT**.

40. Avoid defining event-handling delegates. Use `EventHandler<T>` or `GenericEventHandler` instead.
> GenericEventHandleris defined inChapter 6 of Programming .NET Components 2nd Edition.

41. Avoid raising events explicitly. Use `EventsHelper` to publish events defensively.
> EventsHelper is presented in Chapter 6-8 of Programming .NET Components 2nd Edition.

47. Prefer use interfaces.
> See Chapters 1 and 3 in Programming .NET Components 2nd Edition. We agree it to "prefer" level, not "always"

48. Do not have more than **20** members per interface. **12** is probably the practical limit.

49. When using `abstract` classes, offer an `interface` as well.

50. Expose interfaces on class hierarchies.

51. Prefer using explicit `interface` implementation.

52. Never assume a type supports an `interface`. Defensively query for that interface.
```csharp
SomeType obj1;
IMyInterface obj2;

/* Some code to initialize obj1, then: */
obj2 = obj1 as IMyInterface;
if (obj2 == null)
{
    // Handle error in expected interface
}
else
{
    obj2.Method1();
}
```

53. Never hardcode strings that will be presented to end users. Use resources instead.

54. Never hardcode strings that might change based on deployment such as connectionstrings.
> **IMPORTANT**.

55. Use `string.Empty` instead of `""`:
```csharp
// Correct
string name = string.Empty;

// Avoid
string name = "";
```

56. When building a long string, use `StringBuilder`, not `string`.
Always provide a `static` constructor when providing `static` member variables.

57. Do not use late-binding invocation when early-binding is possible.

58. Use application logging and tracing.

58. Never use `goto` unless in a `switch` statement fall-through.

59. Always have a `default` case in a `switch` statement that asserts.
```csharp
int number = SomeMethod();

switch (number)
{
    case 1:
        Trace.WriteLine("Case 1:");
        break;
    case 2:
        Trace.WriteLine("Case 2:");
        break;
    default:
        Debug.Assert(false);
        break;
}
```

60. Do not use the `this` reference unless invoking another constructor from within a constructor.
```csharp
// Example of proper use of 'this'
public class MyClass
{
    public MyClass(stringmessage)
    {...}
    
    public MyClass() : this("Hello") 
    {...}
}
```

61. Do not use the `base` word to access base class members unless you wish to resolvea conflict with a subclasses member of the same name or when invoking a base class constructor.
```csharp
// Example of proper use of 'base'
public class Dog
{
    public Dog(string name)
    {..}

    virtual public void Bark(int howLong)
    {...}
}

public class GermanShepherd : Dog
{
    public GermanShepherd(string name) : base(name)
    {...}

    override public void Bark(int howLong)
    {
        base.Bark(howLong);
    }
}
```

62. Do not use `GC.AddMemoryPressure()`.

63. Do not rely on `HandleCollector`.

64. Implement `Dispose()` and `Finalize()` methods .
> The template in Chapter 4 of Programming .NET Components 2nd Edition.

65. Always run code `unchecked` by default (for the sake of performance), but explicitly in `checked` mode for overflow- or underflow-prone operations
```csharp
int CalcPower(int number, int power)
{
    int result = 1;
    
    for (int count = 1; count <= power; count++)
    {
        checked
        {
            result *= number;
        }
    }

    return result;
}
```

66. Avoid casting to and from `System.Object` in code that uses generics. Use constraints or the `as` operator instead
```csharp
class SomeClass
{...}

// Correct
class MyClass<T> where T : SomeClass
{
    void SomeMethod(T t)
    {
        SomeClass obj = t;
    }
}

// Avoid
class MyClass<T>
{
    void SomeMethod(T t)
    {
        object temp = t;
        SomeClass obj = (SomeClass)temp;
    }
}
```

67. Do not define constraints in generic interfaces. Interface-level constraints can often be replaced by strong-typing.
```csharp
public class Customer
{...}

// Correct
public interface ICustomerList : IList<Customer>
{...}

// Avoid
public interface IList<T>where T : Customer
{...}
```

68. Do not define method-specific constraints in interfaces.

69. Do not define constraints in delegates.

70. If a class or a method offers both generic and non generic flavors, always prefer using the generics flavor.

71. When implementing a generic interface that derives from an equivalent non-generic interface (such as `IEnumerable<T>`), use explicit interface implementation on all methods, and implement the non-generic methods by delegating to the generic ones.
```csharp
class MyCollection<T> : IEnumerable<T>
{
    IEnumerator<T> IEnumerable<T>.GetEnumerator()
    {...}

    IEnumerator IEnumerable.GetEnumerator()
    {
        IEnumerable<T> enumerable = this;
        return enumerable.GetEnumerator();
    }
}
```

72. Only use `var` when the right side of the assignment clearly indicates the type of the variable.
```csharp
// Correct
var name = EmployeeName;

// Avoid
var myVariable = DoSomethig();
```

73. Do not assign method return types or complex expressions into a `var` variable, withthe exception of LINQ projections that result in anonymous types.

## Out of iDesign scope

74. Always check for positive logic in `if` statement.
```csharp
MyObject myObject;
string myStr;

// Correct
if (myStr.IsNullOrEmpty())
{...}
else
{...}

if (myObject == null)
{...}
else
{...}

// Avoid
if (!myStr.IsNullOrEmpty())
{...}
else
{...}

if (myObject != null)
{...}
else
{...}
```

75. There should be a **space** after C# keywords `for`, `if`, `else`, `switch`,...

76. Should always include the `private` modifier.

77. PLEASE, NEVER use the new `using declaration` in [C# 8.0](https://blogs.msdn.microsoft.com/dotnet/2019/01/29/announcing-net-core-3-preview-2), or kill yourself then.
