# Instalación y ejecución de AntarVis 2.0 en Debian usando Wine

## 📌 Descripción
Este documento describe el procedimiento para instalar y ejecutar el software **AntarVis 2.0 (ZKTeco)** en sistemas Debian utilizando Wine.

## ⚙️ Requisitos
- Debian 12 / 13 (amd64)
- Usuario con privilegios sudo
- Archivo: AntarVis 2.0-20210317.exe

## 📦 Configuración de repositorios
Editar:
sudo nano /etc/apt/sources.list

Agregar:
deb http://deb.debian.org/debian/ trixie main contrib non-free non-free-firmware

Actualizar:
sudo apt update

## 🧱 Instalación de Wine
sudo dpkg --add-architecture i386
sudo apt update
sudo apt install wine wine32:i386 wine64 winbind

## 🛠️ Winetricks
sudo apt install winetricks

## 🧪 Prefijo Wine
export WINEPREFIX=$HOME/.wine-antarvis
export WINEARCH=win32
winecfg

## 📚 Dependencias
WINEPREFIX=$HOME/.wine-antarvis winetricks corefonts vcrun2008 vcrun2010 vcrun2015 dotnet40 quartz wmp9

## ▶️ Ejecutar
WINEPREFIX=$HOME/.wine-antarvis wine AntarVis\ 2.0-20210317.exe

## 📁 Ruta recomendada
Z:\home\usuario\Videos\antarvis

## ⚠️ Notas
- Descargas pueden tardar sin feedback
- Compatibilidad parcial

## 🚀 Recomendación
Usar VM para producción
