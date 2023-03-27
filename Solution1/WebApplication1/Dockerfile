#See https://aka.ms/containerfastmode to understand how Visual Studio uses this Dockerfile to build your images for faster debugging.

#FROM mcr.microsoft.com/dotnet/aspnet:6.0 AS base
#WORKDIR /app
#EXPOSE 80
#EXPOSE 443
#
#FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build
#WORKDIR /src
#COPY ["WebApplication1/WebApplication1.csproj", "WebApplication1/"]
#RUN dotnet restore "WebApplication1/WebApplication1.csproj"
#COPY . .
#WORKDIR "/src/WebApplication1"
#RUN dotnet build "WebApplication1.csproj" -c Release -o /app/build
#
#FROM build AS publish
#RUN dotnet publish "WebApplication1.csproj" -c Release -o /app/publish /p:UseAppHost=false
#
#FROM base AS final
#WORKDIR /app
#COPY --from=publish /app/publish .
#ENTRYPOINT ["dotnet", "WebApplication1.dll"]




#
#FROM mcr.microsoft.com/dotnet/sdk:6.0 as build #imageyi çek (sdk image)
#WORKDIR /app #image içerisinde /app adında klasör oluştur
#COPY *.csproj . # .csproj dosyasını app içerisine kopyala	
#RUN dotnet restore # dotnet içerisindeki kütüphaneleri güncelle
#COPY . . #dockerfile dosyasının olduğu dizindeki tüm dosyaları image içerisindeki app klasörüne yükle 
#
#RUN dotnet restore # dotnet içerisindeki kütüphaneleri güncelle
#RUN dotnet publish WebApplication1.csproj -c Release -o  out #image içerisindeki app klasörünün içerisine out klasörüne uygulamayı publish yap 
#
#
#FROM mcr.microsoft.com/dotnet/aspnet:6.0 # ikinci bir image çek (runtime image)
#WORKDIR /app # ikinci image içerisine app adında klasör oluştur
#COPY --from=build /app/out . # üstteki build olarak adlandırdığımız imagenin içerisindeki app/out klasörünün içerisindeki dosyaları ikinci image içerisinedeki app klasörüne kopyala
#ENV ASPNETCORE_URLS="http://*:4500" # image içerisindeki port numarasını 4500 e eşitle
#ENTRYPOINT ["dotnet","WebApplication1.dll"] # imageyi çalıştır




FROM mcr.microsoft.com/dotnet/sdk:6.0 as build 
WORKDIR /app 
COPY *.csproj .
RUN dotnet restore 
COPY . .  
RUN dotnet publish WebApplication1.csproj -c Release -o  out 
FROM mcr.microsoft.com/dotnet/aspnet:6.0 
WORKDIR /app 
COPY --from=build /app/out . 
ENV ASPNETCORE_URLS="http://*:4500" 
ENTRYPOINT ["dotnet","WebApplication1.dll"] 

