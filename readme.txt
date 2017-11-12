
An attempt to get 'dotnet watch' running against a custom MSBuild project.

Open a command prompt in the root folder (or open CommandPrompt.bat);

Type: dotnet msbuild Build\Build.proj

The folder TextFilesCopy is created, with a copy of the files from the folder TextFiles.

Type: dotnet watch msbuild Build\Build.proj

I get the error: No executable found matching command "dotnet-watch"

I added the following to the Build.proj:

  <ItemGroup>
    <DotNetCliToolReference Include="Microsoft.DotNet.Watcher.Tools" Version="2.0.0" />
  </ItemGroup>

Type: dotnet restore Build\Build.proj

I get the error: Build\Build.proj : error MSB4057: The target "Restore" does not exist in the project

I added the following to the Build.proj:

  <Import Project="$(MSBuildToolsPath)\Microsoft.Common.targets"/>

Type: dotnet restore Build\Build.project

I get the error:

C:\Program Files\dotnet\sdk\2.0.2\NuGet.targets(102,5): error : Value cannot be null.\r [C:\work\scratch\dotnet\WatchCustomProject\Build\Build.proj]
C:\Program Files\dotnet\sdk\2.0.2\NuGet.targets(102,5): error : Parameter name: key [C:\work\scratch\dotnet\WatchCustomProject\Build\Build.proj]

