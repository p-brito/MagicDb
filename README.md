[![Build](https://github.com/p-brito/MagicDb/workflows/MagicDb-build/badge.svg)](https://github.com/p-brito/MagicDb/actions?query=workflow%3A%22MagicDb+-+build%22)
[![Nuget](https://img.shields.io/nuget/v/MagicDb)](https://www.nuget.org/packages/MagicDb/)
[![Nuget Downloads](https://img.shields.io/nuget/dt/MagicDb)](https://www.nuget.org/stats/packages/MagicDb?groupby=Version)
[![Apache License 2.0](https://img.shields.io/badge/License-MIT-blue.svg)](https://github.com/p-brito/MagicDb/blob/main/license)

# MagicDb

MagicDb provides a fast and easy way to implement a NoSQL db provider in your project.

## Getting started

- Install the package.

- Register the service in your Startup.cs.

```cshsarp
  services.AddMagicDb();
```

- Add the `MagicDbOptions` to appsetting.json and register these.

```json
{
    "MagicDbOptions":{
        "Provider":"",
        "ConnectionString":"",
        "Database":""
    }
}
```
```csharp
 services.Configure<MagicDbOptions>(configuration.GetSection(nameof(MagicDbOptions)));
```

> Notice, that these options will change accordingly to the provider that you are using. Read the documentation on how to configure your provider below.

- Get the provider

```csharp
IMagicDbProvider<TEntity> DbProvider = this.serviceProvider.GetRequiredService<IMagicDbProvider<TEntity>>();
```

The MagicDbProvider has the following methods:
- GetAsync;
- InsertAsync;
- UpdateAsync;
- DeleteAsync.

> Notice, that all the entities that are used need to inherit from `BaseEntity`.

## Providers
* [MongoDB](#MongoDB)
* [Firebase](#Firebase)
* [DynamoDB](#DynamoDB)
* [CosmosDB](#CosmosDB)


## MongoDB

To configure the MagicDb to use the MongoDB provider you just need to configure it as follows:

```json
{
    "MagicDbOptions":{
        "Provider":"MongoDB",
        "ConnectionString":"mongodb+srv://admin:mypass123@myddbcluster.c900q.mongodb.net/magicboxDb?retryWrites=true&w=majority",
        "Database":"MyDatabaseName"
    }
}
```

## Firebase

> [Under Development]

## DynamoDB
> [Under Development]

## CosmosDB
> [Under Development]
