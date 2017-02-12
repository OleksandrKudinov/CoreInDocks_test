# Don't use microsoft/dotnet because microsoft updated their docker to the newest sdk (at least since 17/02/08) 
# which moves back to .csproj from project.json.
# https://hub.docker.com/r/microsoft/dotnet/
# Note: The latest tag no longer uses the project.json project format, 
# but has now been updated to be csproj/MSBuild-based. If you do not 
# wish to migrate your existing projects to MSBuild simply change your 
# Dockerfile to use the 1.1.0-sdk-projectjson or 1.1.0-sdk-projectjson-nanoserver tag. 
# Going forward, new .NET Core sdk images will be MSBuild-based.
# (for ASP.NET Core 1.1.0)
FROM microsoft/dotnet:1.1-sdk-projectjson

ARG source=.
RUN mkdir /app
WORKDIR /app

# TODO Investigate this issue:
# Does not work without this line "ASPNETCORE_URLS". 
# Maybe related issues, not the same:
# [1] https://blog.sixeyed.com/published-ports-on-windows-containers-dont-do-loopback/
# [2] https://github.com/docker/for-win/issues/458
ENV ASPNETCORE_URLS http://*:80 

EXPOSE 80
COPY $source .
RUN ["dotnet","restore"]
RUN ["dotnet","build"]
ENTRYPOINT ["dotnet", "run"]