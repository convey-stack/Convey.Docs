## Overview
Adds capability of generating application metrics and exposing them via HTTP endpoint.

## Installation
`dotnet add package Convey.Metrics.AppMetrics`

## Dependencies

* [Convey](https://www.nuget.org/packages/Convey)


## Options
* `enabled` - detemines whether metrics endpoint is goint to be available.
* `influxEnabled` - if `true` metrics will be reported to [InfluxDB](https://www.influxdata.com/).
* `prometheusEnabled` - if `true` metrics will be formated using [Prometheus](https://prometheus.io/) data model.
* `prometheusFormatter` - if set to `protobuf` then protobuf output formatter is going to be used. Otherwise text output formater is picked.
* `InfluxUrl` - connection string to InfluxDB instance e.g. `http://localhost:8086`. Required only if `influxEnabled` is `true`.
* `database` - InfluxDB database name. Required only if `influxEnabled` is `true`.
* `interval` - InfluxDB flush interval expressed in seconds. Required only if `influxEnabled` is `true`.

### appsettings.json

```js
"metrics": {
    "enabled": true,
    "influxEnabled": false,
    "prometheusEnabled": true,
    "influxUrl": "http://localhost:8086",
    "database": "pacco",
    "env": "local",
    "interval": 5
  },
```

## Usage
Inside ``Startup.cs`` extend ``IConveyBuilder`` with ``AddMetrics()`` and ``IApplicationBuilder`` with ``UseMetrics()``:

```csharp
public IServiceProvider ConfigureServices(this IServiceCollection services)
{
    var builder = ConveyBuilder
        .Create(services)
        .AddMetrics();

    //other registrations    
    return builder.Build();
}

public void Configure(this IApplicationBuilder app)
{
    app.UseMetrics();
}
```
The above code registers all required services and exposes some default application metrics at two HTTP endpoints:
* `http://host/metrics` - depending on `prometheusEnabled` option, this endpoint exposes metrics that are either formatted using Prometheus data model or using standard, text formater
* * `http://host/metrics-text` - this endpoint exposes metrics that are always formated using standard, text formater