FROM mcr.microsoft.com/dotnet/sdk:7.0 AS build
WORKDIR /app

COPY ["MessageService/MessageService.csproj", "MessageService/"]
RUN dotnet restore "MessageService/MessageService.csproj"
RUN dotnet publish "MessageService/MessageService.csproj" -c Release -o out

FROM mcr.microsoft.com/dotnet/aspnet:7.0 AS runtime
WORKDIR /app
COPY --from=publish /app/out .
ENTRYPOINT ["dotnet", "MessageService.dll"]
