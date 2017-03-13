========================
ASP.NET Core
========================

A. Fundamentals
========================

1. Overview
---------------------------

2. Setting up ASP.NET MVC in Empty project
---------------------------------------------

1. Add Scaffolding CLI tool to the project::

    <ItemGroup>
        <DotNetCliToolReference Include="Microsoft.VisualStudio.Web.CodeGeneration.Tools" Version="1.0.0" />
    </ItemGroup>

2. Add the package dependency -> Add the following code in Startup.cs file ::

    // Add this Nuget package
    Microsoft.AspNetCore.Mvc 1.0.0

    public void Configure(IApplicationBuilder app, ...)
    {
        ...
        app.UseMvcWithDefaultRoute();
        ...
    }
    
3. Add the MVC services -> Add the following code in Startup.cs file ::

    public void ConfigurationServices(IServiceCollection services)    
    {
        services.AddMvc();
    }

4. Add the MVC middleware -> Add HomeController.cs with the following code::

    public class HomeController
    {
        public string Index()
        {
            return "Hello from HomeController";
        }
    }



