# DotNet CLI Cheatsheet

New Solution: `dotnet new sln -n sln_name`

List available new commands: `dotnet new -h`

List avilable project types `dotnet new -l`

New Project: `dotnet new <Project-Type> -o project_name`

```
Project-Type:
- classlib
- console

```

For more [Dotnet Project-Types](https://learn.microsoft.com/en-us/dotnet/core/tools/dotnet-new)

Add Project to Solution: `dotnet sln sln_name add project_name/project_name.csproj`

Run Project: `dotnet run -p project_name`

# Docker Commands

Dockerfile
```
FROM microsoft/dotnet:sdk AS build-env
WORKDIR /app

# Copy csproj and restore as distinct layers

COPY *.csproj ./
RUN dotnet restore

# Copy everything else and build

COPY . ./
RUN dotnet publish -c Release -o out

# Build runtime image

FROM microsoft/dotnet:aspnetcore-runtime
WORKDIR /app
COPY --from=build-env /app/out .
ENTRYPOINT ["dotnet", "aspnetapp.dll"]

```

```
$ docker build -t aspnetapp .
$ docker run -d -p 8080:80 --name myapp aspnetapp

```

```
docker run -i -p 8080:80 --link <CONTAINER-TO-ATTACH> --name <NAME> <IMAGE>

```

```
docker exec -it <CONTAINER> ../bin/bash

```