---
layout: post
title:  "Getting started with .NET Core on Ubuntu - HelloWorld App"
date:   2019-09-05 15:26:16 +0500
categories: net-core
---

In our previous post we looked into the basics of .NET Core and also learned about installing the .NET Core SDK on ubuntu.

 In this blog post we will explore the builtin project templates that we can use as a startup boilerplate code and continue building stuff on top of that.

 We will build a simple `HelloWorld` app which will be a `console application`.

 So let's begin.

 Open up a terminal window and type the following `dotnet` command.

 ```
> dotnet new --help
 ```

You will see an output similar to the following:

```
Usage: new [options]

Templates                                         Short Name         Language          Tags                                 
----------------------------------------------------------------------------------------------------------------------------
Console Application                               console            [C#], F#, VB      Common/Console                       
Class library                                     classlib           [C#], F#, VB      Common/Library                       
Unit Test Project                                 mstest             [C#], F#, VB      Test/MSTest                          
NUnit 3 Test Project                              nunit              [C#], F#, VB      Test/NUnit                           
NUnit 3 Test Item                                 nunit-test         [C#], F#, VB      Test/NUnit                           
xUnit Test Project                                xunit              [C#], F#, VB      Test/xUnit                           
Razor Page                                        page               [C#]              Web/ASP.NET                          
MVC ViewImports                                   viewimports        [C#]              Web/ASP.NET                          
MVC ViewStart                                     viewstart          [C#]              Web/ASP.NET                          
ASP.NET Core Empty                                web                [C#], F#          Web/Empty                            
ASP.NET Core Web App (Model-View-Controller)      mvc                [C#], F#          Web/MVC                              
ASP.NET Core Web App                              webapp             [C#]              Web/MVC/Razor Pages                  
ASP.NET Core with Angular                         angular            [C#]              Web/MVC/SPA                          
ASP.NET Core with React.js                        react              [C#]              Web/MVC/SPA                          
ASP.NET Core with React.js and Redux              reactredux         [C#]              Web/MVC/SPA                          
Razor Class Library                               razorclasslib      [C#]              Web/Razor/Library/Razor Class Library
ASP.NET Core Web API                              webapi             [C#], F#          Web/WebAPI                           
global.json file                                  globaljson                           Config                               
NuGet Config                                      nugetconfig                          Config                               
Web Config                                        webconfig                            Config                               
Solution File                                     sln                                  Solution                             

Examples:
    dotnet new mvc --auth Individual
    dotnet new angular
    dotnet new --help

```

The output shows the set of available project templates that we can use, each project template serves a different purpose than the other. 

While these projects are pretty handy to use as a starting point for your application but its utterly possible not to use any of them at all and build your project based on your own personal needs and requirements.

We will start off with a simple `console` application and will see that how can we generate a console application using the `dotnet` cli.

Open up the terminal and run the following command:

```
> dotnet new console -o HelloWorld
```

I will explain the output generated by the command later but first let us understand the command itself.

We are simply telling the `dotnet` cli to generate a project for us which should be of type `console`, the `-o` argument tells the name of the directory in which it should create the project, in our case it will be `HelloWorld`.

For the full list of possible arguments to the above command run the command `dotnet new --help`.

To run the application we first need to step into the `HelloWorld` directory, so let's do that.

```
> cd HelloWorld
```

Now run the app.

```
> dotnet run
```

You should be able to see the generated output like below

```
> Hello World!
```

