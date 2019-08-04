# Convey.Logging
Adds the logging capability, by default uses [Serilog](https://serilog.net) for logging with 3 optional extensions (sinks):

* Console
* File
* [Seq](https://datalust.co/seq)

## Installation
`dotnet add package Convey.Logging`

## Dependencies

* [Convey](https://www.nuget.org/packages/Convey)

## Overview

Extend `Program.cs` -> `CreateDefaultBuilder()` with `UseLogging()` that will add the required services and configure `ILogger` available in ASP.NET Core framework.

### Options:
* `applicationName` - sets the application name property used for log [enrichment](https://github.com/serilog/serilog/wiki/Enrichment) (optional).

```csharp
public static IWebHostBuilder GetWebHostBuilder(string[] args)
  => WebHost.CreateDefaultBuilder(args)
      .ConfigureServices(services => services.AddConvey().Build())
      .UseLogging();
```

### appsettings.json

```js
"logger": {
  "console": {
    "enabled": true
  },
  "file": {
    "enabled": true,
    "path": "logs/logs.txt",
    "interval": "day"
  },
  "seq": {
    "enabled": true,
    "url": "http://localhost:5341",
    "token": "secret"
  },
  "excludePaths": ["/ping", "/metrics"]
}
```