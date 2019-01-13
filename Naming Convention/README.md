# Naming convention

### Type, method, and constant
- Pascal casing
```csharp
public class SomeClass
{
	const int DefaultSize = 100;
	
	public void SomeMethod()
	{}
}
```
### Private member
- Prefix with **_** and then camel casing
> The iDesign's original rule for private member is **m_** and pascal casing. However, the community (StackOverflow) recently agreed that the **_** and camel casing still makes sense and applicable.
```csharp
public class SomeClass
{
	private int _defaultSize = 100;
}
```
### Local variable, method argument
- Camel casing
```csharp
public class SomeClass
{
	public void Add(int paramA, int paramB)
	{
		int result;3
	}
}
```
### Interface
- Prefix with ***I*** and pascal casing
```csharp
public interface IMyInterface
{...}
```
### Attribute, Exception
- Suffix with **Attribute**, **Exception**
```csharp
public class CustomFilterAttribute
{...}
public class CustomException
{...}
```
### Name Methods using verb-object pair
```csharp
public void ShowDialog()
{...}
```
### Methods with return values should have name describing the value returned
```csharp
public IEnumerable<Rates> GetRates()
{...}
```
### Variable names
- Avoid single character, such as **t**, **s**, except the declaration in *(**for** int **i**;...)*
- No abbreviate, as **num** instead of **number**
### Always use C# predefined types
```csharp
object
string
int
```
### With generics, use capital letters for types. Preserve suffing *Type*
```csharp
// Correct
public class LinkedList<K,T>
{...}
// Avoid
public class LinkedList<KeyType,DataType>
{...}
```
### Namespaces
- Use meaningful namespaces such as product name or the company name.
- Avoid fully qualified type names. Use **using**.
- Avoid putting **using** inside of namespace.
- Group namespaces together, and custom or third-party namespaces underneath.
```csharp
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using MyCompany;
using MyControls;
```
### Indentation
- Using **tab** instead of **space**
- A **tab** is **4 spaces**
> This rule is different with original iDesign
### Comment
- Are at some level as indentation as the code you are documenting.
- Must pass spell checking.
### Variables
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
### File name should reflect the class it contains
### Partial types and allocating a part per file
- Name each file after thelogical part that part plays.
```csharp
//In MyClass.cs
public partial class MyClass
{...}
//In MyClass.Designer.cs
public partial class MyClass
{...}
```
### Always place open curly brace **{** in a new line
### Anonymous methods, Lambda expressions
- Mimic the code layout of a regular method, aligned with the delegate declaration. (complies with placing an open curly brace in a new line):
```csharp
delegate void SomeDelegate(string someString);
//Correct
void InvokeMethod()
{
    SomeDelegate someDelegate = delegate (string name)
                                {
                                    MessageBox.Show(name);
                                };
    someDelegate("Juval");
}
//Avoid
void InvokeMethod()
{
    SomeDelegate someDelegate = delegate(string name){MessageBox.Show(name);};
    someDelegate("Juval");
}
```
### Avoid using empty parentheses on parameter-less anonymous methods
```csharp
delegate void SomeDelegate();
//Correct
SomeDelegate someDelegate = delegate
                            {
                                MessageBox.Show("Hello");
                            };
//Avoid
SomeDelegate someDelegate = delegate()
                            {
                                MessageBox.Show("Hello");
                            };
```
> This rule is different with original iDesign
### Use in-line Lambda expressions when they contain a single simple statement