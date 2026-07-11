# Instalación y ejecución de AntarVis 2.0 en Fedora 44 usando Wine

## 📌 Descripción
Este documento describe el procedimiento para instalar y ejecutar el software **AntarVis 2.0 (ZKTeco)** en Fedora 44 utilizando Wine.

## ⚙️ Requisitos
- Fedora 44 (x86_64)
- Usuario con privilegios sudo
- Archivo: AntarVis 2.0-20210317.exe

## 🧱 Instalación de Wine
Fedora incluye Wine en sus repositorios oficiales, ya en su variante **wow64** (un único binario de 64 bits capaz de ejecutar programas de 32 y 64 bits sin necesidad de paquetes `wine32`/`wine64` separados). No requiere RPM Fusion:

```bash
sudo dnf install wine winetricks -y
```

Con esto ya se obtiene una versión estable y reciente de Wine (11.0 en Fedora 44).

> ⚠️ **No mezclar con el repositorio de WineHQ salvo que sea necesario.** El paquete `winehq-stable` provee `wine-desktop`, el mismo nombre que ya provee el paquete `wine` de Fedora. Si agregas el repo de WineHQ e instalas `winehq-stable` mientras el `wine` de Fedora sigue instalado, dnf5 fallará con un conflicto de tipo "en conflicto con wine-desktop". Si en el futuro necesitas una versión más nueva que la de los repos de Fedora, instala con:
> ```bash
> sudo dnf install dnf5-plugins -y
> sudo dnf config-manager addrepo --from-repofile=https://dl.winehq.org/wine-builds/fedora/44/winehq.repo
> sudo dnf install winehq-stable --allowerasing -y
> ```
> `--allowerasing` permite que dnf5 quite el `wine` de Fedora para instalar el de WineHQ en su lugar. Fedora 41+ usa `dnf5`, cuyo plugin `config-manager` cambió de sintaxis respecto a `dnf4` (`--add-repo` ya no existe; ahora es `addrepo --from-repofile=`, y el paquete del plugin es `dnf5-plugins`, no `dnf-plugins-core`).

## 🛠️ Winetricks
El paquete `winetricks` ya se instaló en el paso anterior. Verificar la versión:

```bash
winetricks --version
```

## 🧪 Prefijo Wine
```bash
export WINEPREFIX=$HOME/.wine-antarvis
winecfg
```

> ℹ️ **No definir `WINEARCH=win32`.** El Wine de Fedora es un build wow64: solo crea prefijos de 64 bits (que igualmente ejecutan binarios de 32 bits como el de AntarVis de forma transparente). Forzar `WINEARCH=win32` produce el error `WINEARCH is set to 'win32' but this is not supported in wow64 mode`.

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
