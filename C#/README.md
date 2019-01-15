# HMS Coding Standards - C# language
The C# coding standard for HMS project, based on [iDesign standard](http://www.idesign.net/) with our own customization.

## Sections
1. [Code practices](https://github.com/CloudHMS/HMS.CodingStandard/tree/f321db651dee1a3c54bd213160e4b67a43ff69dd/C%23/Coding%20practices)
2. [Development tools](https://github.com/CloudHMS/HMS.CodingStandard/tree/f321db651dee1a3c54bd213160e4b67a43ff69dd/C%23/Development%20tools)
3. [Logging conventions](https://github.com/CloudHMS/HMS.CodingStandard/tree/f321db651dee1a3c54bd213160e4b67a43ff69dd/C%23/Logging%20conventions)
4. [Naming conventions](https://github.com/CloudHMS/HMS.CodingStandard/tree/f321db651dee1a3c54bd213160e4b67a43ff69dd/C%23/Naming%20conventions)
5. [Project settings and structure](https://github.com/CloudHMS/HMS.CodingStandard/tree/f321db651dee1a3c54bd213160e4b67a43ff69dd/C%23/Project%20settings%20and%20structure)

# Development guidelines
## Initial project phase
1. Create project as the directory same level as solution.
2. Copy the **default.gitignore** file to **repository root**.
3. Rename it to **.gitignore**.
4. Add reference to `StyleCop.Analyzers` NuGet package at least at version `1.1.1-beta.61`.
5. Make sure the `csproj` file contains these lines.
```xml
    <PropertyGroup>
        <Version>1.0.0</Version> <!-- Should change depends on which version you're working with -->
        <Authors>HMS</Authors>
        <Company>HMS</Company>
        <Product>HMS</Product>
        <GeneratePackageOnBuild>true</GeneratePackageOnBuild>
    </PropertyGroup>

    <PropertyGroup>
        <CodeAnalysisRuleSet>..\HMS.StyleCop.ruleset</CodeAnalysisRuleSet>
    </PropertyGroup>

    <ItemGroup>
        <AdditionalFiles Include="..\stylecop.json" />
    </ItemGroup>
```
## Development phase
