# NAMING CONVENTIONS

<a id="1st"></a>
[1. Type, method](#1st)
- `Non-Microsoft` Camel casing.
```csharp
public class SomeClass
{	
	public void SomeMethod()
	{...}
}
```

<a id="2nd"></a>
[2. Constant](#2nd)
- Capital letters.
```csharp
public class SomeClass
{
	private const int DEFAULT_SIZE = 100;
}
```

3. Private member
- Prefix with `_` and then `Non-Microsoft` pascal casing.
> The iDesign's original rule for private member is `m_` and `Non-Microsoft` camel casing. However, the community (StackOverflow) recently agreed that the `_` and `Non-Microsoft` pascal casing still makes sense and applicable.
```csharp
public class SomeClass
{
	private int _defaultSize = 100;
}
```

4. Local variable, method argument
- `Non-Microsoft` Camel casing.
```csharp
public class SomeClass
{
	public void Add(int paramA, int paramB)
	{
		int result;
	}
}
```

5. Interface
- Prefix with `I` and `Non-Microsoft` camel casing.
```csharp
public interface IMyInterface
{...}
```

6. `Attribute`, `Exception`, `Func`, `Action`, or `Async`
- Suffix with `Attribute`, `Exception`, `Func`, `Action`, or `Async`.
```csharp
public class CustomFilterAttribute
{...}
public class CustomException
{...}
public class Awaitable
{
    public async Task ExecuteAsync()
    {
        await SomeTask();
    }
}
```

7. Name Methods using verb-object pair
```csharp
public void ShowDialog()
{...}
```

8. Methods with return values should have name describing the value returned
```csharp
public IEnumerable<Rates> GetRates()
{...}
```

9. Variable names
- Avoid single character, such as `t`, `s`, except the declaration in `for (int i;...)`.
- No abbreviate, as `num` instead of `number`.

10. Always use C# predefined types
```csharp
object
string
int
```

11. With generics, use capital letters for types. Preserve suffing `Type`.
```csharp
// Correct
public class LinkedList<K,T>
{...}

// Avoid
public class LinkedList<KeyType,DataType>
{...}
```

12. Namespaces
- Use meaningful namespaces such as product name or the company name.
- Avoid fully qualified type names. Use `using`.
- Avoid putting `using` inside of namespace.
- Group namespaces together, and custom or third-party namespaces underneath.
```csharp
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using MyCompany;
using MyControls;
```

13. Indentation
- Using **tab** instead of **space**.
- A **tab** is **4 spaces**.
> This rule is different with original iDesign.

14. Comment
- Are at some level as indentation as the code you are documenting.
- Must pass spell checking.

15. Variables
- Member variables should be declared at the top, 1 line separating from the properties, or methods.
- Local variables should be declared as close as possible to its first use.
```csharp
public class MyClass
{
	int _number;
	
	public void SomeMethod1()
	{}
}
```

16. File name should reflect the class it contains.

17. Partial types and allocating a part per file
- Name each file after thelogical part that part plays.
```csharp
// In MyClass.cs
public partial class MyClass
{...}

// In MyClass.Designer.cs
public partial class MyClass
{...}
```

18. Always place brace and curly brace `{`, `}`, `( ` and `)` in a new line.

19. Anonymous methods, Lambda expressions
- Mimic the code layout of a regular method, aligned with the delegate declaration. (complies with placing an open curly brace in a new line).
```csharp
delegate void SomeDelegate(string someString);
// Correct
void InvokeMethod()
{
    SomeDelegate someDelegate = delegate (string name)
                                {
                                    MessageBox.Show(name);
                                };
    someDelegate("Juval");
}

// Avoid
void InvokeMethod()
{
    SomeDelegate someDelegate = delegate(string name){MessageBox.Show(name);};
    someDelegate("Juval");
}
```

20. Avoid using empty parentheses on parameter-less anonymous methods.
```csharp
delegate void SomeDelegate();
// Correct
SomeDelegate someDelegate = delegate
                            {
                                MessageBox.Show("Hello");
                            };
			    
// Avoid
SomeDelegate someDelegate = delegate()
                            {
                                MessageBox.Show("Hello");
                            };
```
> This rule is different with original iDesign.

21. Use in-line Lambda expressions when they contain a single simple statement.

## Out of iDesign scope

22. Always have **space** before and after the **colon** (`:`).

### <a id="rule-23"></a>
23. Project name, or DynamoDB should follow structure as each name-pair **`<NameOfSystem>.<FunctionOfSystem>.<NameOfSubSystem1>.<FunctionOfSubSystem1>.<abc_system>.<function_of_abc_system>`**. Any sub-systems shouls keep extending this naming structure.
- **`<NameOfSystem>`** could be company name, library name,... If it's the sub-system, it means that it belongs to the previous system. Optional, sometimes the function of the system already explains the system itself.
- **`<FunctionOfSystem>`** could be the purpose of this project on the above name, explain its existence. Must be in singular form. 
```csharp
// This is the core code of HMS company
HMS.Core
// The OWS system belongs to HMS proxy system
HMS.Proxy.OWS
// The tool for OWS system of HMS proxy system
HMS.Proxy.OWS.Tool
```

24. Mimic the code layout of a regular method, aligned with the dot annotation.
```csharp
myInstance.AddMethod1()
          .AddMethod2()
          .AddMethod3();
```

25. The private members, properties, and methods of a class, if possible, shouldn't repeat the class type's name.
```csharp
// The class type is Response type
public class ApiResponse
{
    // Correct
    public object Data { get; set; }

    // Avoid
    public object ResponseData { get; set; } 
}
```

26. No suffix with a typical name as `Object`.
```csharp
// Correct
public class ApiResponse
{...}

// Avoid
public class ApiResponseObject
{...}
```

27. Any abbreviation which is more than 3 letters should have all capital letters
```csharp
SMTPHost
ETCDHost
SQLServer
AccountId
```

<a id="28th"></a>
[28. API endpoints should be named in **hyphen-case**](#28th)

E.g.: **{host}/api/_get-hotel-availability_**

And remaining types of data, still keeps `Non-Microsoft` pascal casing.

E.g.: **{host}/api/get-hotel-info?_queyString=hello_**
