# HMS Coding Standards - C# language
The C# coding standard for HMS project, based on [iDesign standard](http://www.idesign.net/) with our own customization.

# IMPORTANT:
This coding standard is optional. The main concept that we need to have a same view on developing software. 
So if you find your own standard which is different than this, it's still fine, as long as it's approved by your technical leader.

## Sections
1. [Code practices](https://github.com/CloudHMS/HMS.Sample.CodingStandard/tree/master/C%23/Coding%20practices)
2. [Development tools](https://github.com/CloudHMS/HMS.Sample.CodingStandard/tree/master/C%23/Development%20tools)
3. [Logging conventions](https://github.com/CloudHMS/HMS.Sample.CodingStandard/tree/master/C%23/Logging%20conventions)
4. [Naming conventions](https://github.com/CloudHMS/HMS.Sample.CodingStandard/tree/master/C%23/Naming%20conventions)
5. [Project settings and structure](https://github.com/CloudHMS/HMS.Sample.CodingStandard/tree/master/C%23/Project%20settings%20and%20structure)

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
1. Branch from `master` branch to your Jira Id's name. For ex: `TT-135`
2. After finishing development, create 2 PRs which the description `MUST` contain Jira Id to `master` and `development`.
3. If there is no draft release, create 1 with the description as above. If there is, append to it.
4. Copy 2 PR links, send to technical lead in chat room.
