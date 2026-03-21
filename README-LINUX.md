# Instalación y ejecución de AntarVis 2.0 en Linux usando Wine

## 📌 Descripción
Guía general para ejecutar AntarVis 2.0 en Linux utilizando Wine.

## ⚙️ Requisitos
- Linux x86_64
- Wine instalado

## 📦 Instalación de Wine (Debian/Ubuntu)
sudo dpkg --add-architecture i386
sudo apt update
sudo apt install wine wine32 wine64 winbind

## 🛠️ Winetricks
sudo apt install winetricks

## 🧪 Prefijo
export WINEPREFIX=$HOME/.wine-antarvis
export WINEARCH=win32
winecfg

## 📚 Dependencias
WINEPREFIX=$HOME/.wine-antarvis winetricks corefonts vcrun2008 vcrun2010 vcrun2015 dotnet40 quartz wmp9

## ▶️ Ejecutar
WINEPREFIX=$HOME/.wine-antarvis wine AntarVis\ 2.0-20210317.exe

## 📁 Ruta
Z:\home\usuario\Videos\antarvis

## ⚠️ Notas
- Compatibilidad parcial
- Software CCTV puede fallar en exportación

## 🚀 Alternativas
- Máquina virtual
- RTSP con ffmpeg
