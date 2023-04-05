FROM mcr.microsoft.com/dotnet/aspnet:6.0@sha256:d3167d2996f3d0ec044538452332112e991fb9aca4e27b9e0d93371b0fc86219 AS base
WORKDIR /app
EXPOSE 3000

FROM mcr.microsoft.com/dotnet/sdk:6.0@sha256:ef18259e9c0570d28b874b6680b13d83cf0c6c2e7e2a2509a339aab5e88c16b4 AS build
WORKDIR /src
COPY ["CarActor.csproj", "./"]
RUN dotnet restore "CarActor.csproj"
COPY . .
WORKDIR "/src/."
RUN dotnet build "CarActor.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "CarActor.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "CarActor.dll"]
