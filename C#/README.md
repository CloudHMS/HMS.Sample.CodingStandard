# HMS Coding Standards - C# language
The C# coding standard for HMS project, based on [iDesign standard](http://www.idesign.net/) with our own customization.

# IMPORTANT:
This coding standard is optional. The main concept that we need to have a same view on developing software. So if you find your own standard which is different than this, it's still fine.

## Sections
1. [Code practices](https://github.com/CloudHMS/HMS.CodingStandard/tree/fcfbaa9abf6361b3f29ad9ab359628b1a970497c/C%23/Coding%20practices)
2. [Development tools](https://github.com/CloudHMS/HMS.CodingStandard/tree/fcfbaa9abf6361b3f29ad9ab359628b1a970497c/C%23/Development%20tools)
3. [Logging conventions](https://github.com/CloudHMS/HMS.CodingStandard/tree/fcfbaa9abf6361b3f29ad9ab359628b1a970497c/C%23/Logging%20conventions)
4. [Naming conventions](https://github.com/CloudHMS/HMS.CodingStandard/tree/fcfbaa9abf6361b3f29ad9ab359628b1a970497c/C%23/Naming%20conventions)
5. [Project settings and structure](https://github.com/CloudHMS/HMS.CodingStandard/tree/fcfbaa9abf6361b3f29ad9ab359628b1a970497c/C%23/Project%20settings%20and%20structure)

# Development guidelines
## Initial project phase
1. Create project as the directory same level as solution.
2. Copy the **Directory.Build.props** file to **solution directory**.
3. Copy the **HMS.StyleCop.ruleset**, **stylecop.json** files to **solution directory**.
4. Add reference to `StyleCop.Analyzers` NuGet package at least at version `1.1.1-beta.61`.
5. Make sure the `csproj` file contains these lines.
```xml
    <PropertyGroup>
        <CodeAnalysisRuleSet>..\HMS.StyleCop.ruleset</CodeAnalysisRuleSet> <!-- Could be changed depends on the location from the project to solution -->
    </PropertyGroup>

    <ItemGroup>
        <AdditionalFiles Include="..\stylecop.json" /> <!-- Could be changed depends on the location from the project to solution -->
    </ItemGroup>
```
## Development phase
