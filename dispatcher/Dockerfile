
#FROM microsoft/aspnetcore:1
#LABEL Name=dispatcher Version=0.0.1
#ARG source=.
#WORKDIR /app
#EXPOSE 3002
#COPY $source .
#ENTRYPOINT dotnet dispatcher.dll

#FROM microsoft/aspnetcore-build:2.0 AS build
#WORKDIR /code
#COPY . .
#RUN dotnet restore
#RUN dotnet publish --output /output --configuration Release
#FROM microsoft/aspnetcore:2.0
#COPY --from=build /output /app
#WORKDIR /app
#EXPOSE 3002
#ENTRYPOINT [ "dotnet", "dispatcher.dll" ]

FROM microsoft/dotnet:2.0-sdk
WORKDIR /app
COPY *.csproj ./
COPY ./JsonTemplates ./JsonTemplates
COPY ./SoapTemplates ./SoapTemplates
RUN dotnet restore
COPY . ./
RUN dotnet publish -c Release -o out
ENTRYPOINT ["dotnet", "out/dispatcher.dll"]
