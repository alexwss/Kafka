FROM microsoft/dotnet:2.2-sdk AS build
WORKDIR /src
COPY . .
RUN dotnet restore Kafka.Producer.API.csproj
RUN dotnet build "Kafka.Producer.API.csproj" -c Release -o /publish

FROM microsoft/dotnet:2.2-runtime
WORKDIR /publish
COPY --from=build /publish .
ENTRYPOINT ["dotnet", "Kafka.Producer.API.dll"]