FROM microsoft/dotnet:2.2-sdk AS build
WORKDIR /src
COPY . .
RUN dotnet restore Kafka.Consumer.Handler.csproj
RUN dotnet publish "Kafka.Consumer.Handler.csproj" -c Release -o /publish

FROM microsoft/dotnet:2.2-runtime
WORKDIR /publish
COPY --from=build /publish .
ENTRYPOINT ["dotnet", "Kafka.Consumer.Handler.dll"]