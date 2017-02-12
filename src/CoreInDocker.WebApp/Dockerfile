FROM microsoft/dotnet:1.0.1-sdk-projectjson
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