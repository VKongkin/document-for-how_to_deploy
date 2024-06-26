app.yaml

```
runtime: custom
env: flex

# This sample incurs costs to run on the App Engine flexible environment. 
# The settings below are to reduce costs during testing and are not appropriate
# for production use. For more information, see:
# https://cloud.google.com/appengine/docs/flexible/dotnet/configuring-your-app-with-app-yaml
manual_scaling:
  instances: 1
resources:
  cpu: 2
  memory_gb: 6
  disk_size_gb: 30

env_variables:
  # The __ in My__Greeting will be translated to a : by ASP.NET.
  My__Greeting: Hello AppEngine!
```

Dockerfile

```
FROM mcr.microsoft.com/dotnet/aspnet:6.0
ADD / /app
EXPOSE 8080
ENV ASPNETCORE_URLS=http://*:8080
WORKDIR /app
ENTRYPOINT [ "dotnet", "POSapi.dll"]

```