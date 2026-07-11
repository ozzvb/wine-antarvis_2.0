# Instalación y ejecución de AntarVis 2.0 en Fedora 44 usando Wine

## 📌 Descripción
Este documento describe el procedimiento para instalar y ejecutar el software **AntarVis 2.0 (ZKTeco)** en Fedora 44 utilizando Wine.

## ⚙️ Requisitos
- Fedora 44 (x86_64)
- Usuario con privilegios sudo
- Archivo: AntarVis 2.0-20210317.exe

## 🧱 Instalación de Wine
Fedora incluye Wine en sus repositorios oficiales (con soporte de 32 bits incluido), no requiere RPM Fusion:

```bash
sudo dnf install wine winetricks -y
```

Si se necesita una versión más reciente de Wine, se puede usar el repositorio oficial de WineHQ:

```bash
sudo dnf install dnf5-plugins -y
sudo dnf config-manager addrepo --from-repofile=https://dl.winehq.org/wine-builds/fedora/44/winehq.repo
sudo dnf install winehq-stable -y
```

> ℹ️ Fedora 41+ usa `dnf5`, cuyo plugin `config-manager` cambió de sintaxis respecto a `dnf4` (`--add-repo` ya no existe; ahora es `addrepo --from-repofile=`).

> ⚠️ Si el repositorio de WineHQ aún no publica una versión para Fedora 44, usar el paquete `wine` de los repositorios oficiales de Fedora como alternativa.

## 🛠️ Winetricks
El paquete `winetricks` ya se instaló en el paso anterior. Verificar la versión:

```bash
winetricks --version
```

## 🧪 Prefijo Wine
```bash
export WINEPREFIX=$HOME/.wine-antarvis
export WINEARCH=win32
winecfg
```

## 📚 Dependencias
```bash
WINEPREFIX=$HOME/.wine-antarvis winetricks corefonts vcrun2008 vcrun2010 vcrun2015 dotnet40 quartz wmp9
```

## ▶️ Ejecutar
```bash
WINEPREFIX=$HOME/.wine-antarvis wine AntarVis\ 2.0-20210317.exe
```

## 📁 Ruta recomendada
```
Z:\home\usuario\Videos\antarvis
```

## ⚠️ Notas
- SELinux puede bloquear la ejecución de binarios de Wine; si ocurre, revisar `audit2allow` o ejecutar temporalmente con `setenforce 0` solo para diagnóstico
- Compatibilidad parcial
- Software CCTV puede fallar en exportación

## 🚀 Alternativas
- Máquina virtual
- RTSP con ffmpeg
