# Build aşaması
FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build-env
WORKDIR /app

# Proje dosyasını kopyala ve bağımlılıkları indir
COPY *.csproj . 
RUN dotnet restore

# Tüm dosyaları kopyala ve projeyi yayımla
COPY . ./
RUN dotnet publish -c Release -o out

# Çalışma aşaması
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
WORKDIR /app

# Build aşamasından çıktıları kopyala
COPY --from=build-env /app/out .

# Çalıştırılacak uygulamayı tanımla
ENTRYPOINT ["dotnet", "Api.dll"]

