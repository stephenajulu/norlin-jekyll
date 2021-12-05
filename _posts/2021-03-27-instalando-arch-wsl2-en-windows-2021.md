---
layout: post
title: Instalando Arch-WSL2 en Windows 2021
description: Hoy vamos a aprender, juntos, a instalar Archlinux dentro de Windows,
  aprovechando la herramienta del subsistema de linux.
date: 2021-03-27 03:00:00 +0000
image: https://i2.wp.com/mundowin.com/wp-content/uploads/2020/02/WIndows-Linux.png?w=832&ssl=1
tags:
- Windows
- Documentacion
- Linux

---
## Intro

¡Primero lo primero! **WSL2 (Windows Subsystem for Linux Version 2)** es la nueva arquitectura que permite ejecutar `Linux` dentro de Windows 10 de manera nativa. Y está destinada a reemplazar WSL1.

Esta nueva versión ejecuta el kernel de `Linux` en tiempo real. Lo cual mejora el rendimiento y compatibilidad de las aplicaciones y paquetes respecto a la versión anterior.

## Preparando Windows

Para poder instalar cualquier wsl, ya sea el wsl1 tanto como el wsl2 debemos habilitar dos opciones que se encuentran dentro de las caracteristicas de windows.

**Para poder instalar estas opciones debemos ir a**

1. **Inicio** de Windows
2. **Activar o Desactivar caracteristicas de Windows** (usa el cuadro de busquedas)
3. Habilitamos **Plataforma de máquina virtual** y **Subsistema de Windows para Linux**

![](/uploads/enable-wsl1-windows-10.jpg)

4. Aceptar
5. Reinician!

## Habilitar la Máquina Virtual

    La motherboard y el procesador deben admitir la virtualización, y la opción debe estar habilitada en el sistema básico de entrada/salida (BIOS) o en la interfaz de firmware extensible unificada (UEFI).

1. **Click derecho en inicio**
2. **Windows Powershell (administrador)**
3. Escribimos en la powershell.

{% highlight bash%}

Enable-WindowsOptionalFeature -Online -FeatureName VirtualMachinePlatform

{% endhighlight %}

4. Reiniciamos

## Activando WSL2

Para poder convertir `wsl1` en `wsl2` tienen que seguir estos pasos:

1. Descargan e instalan el kernel [`WSL2`](https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi) **(obligatorio)**
2. Una vez instalado abren otra vez la powershell (administrador)
3. 

{% highlight bash%}

wsl --set-default-version 2

{% endhighlight %}

## Instalando Arch en WSL2

![](https://raw.githubusercontent.com/wiki/yuk7/wsldl/img/Arch_Alpine_Ubuntu.png)

Para no alargar demasiado el tutorial. Quisiera aclarar que ya no es necesario continuar con esto, si solamente quisieras una versión de linux que corra de forma nativa te voy a dejar unos enlaces que simplemente instalas ejecutando.

[`Ubuntu 20.04`](https://aka.ms/wslubuntu2004)

[`Ubuntu 18.04`](https://aka.ms/wsl-ubuntu-1804)

[`Ubuntu 16.04`](https://aka.ms/wsl-ubuntu-1604)

[`Debian GNU/Linux`](https://aka.ms/wsl-debian-gnulinux)

[`Kali Linux`](https://aka.ms/wsl-kali-linux-new)

[`OpenSuse Leap 42`](https://aka.ms/wsl-opensuse-42)

[`Fedora Remix`](https://github.com/WhitewaterFoundry/WSLFedoraRemix/releases/)

# Si te interesa continuar con el tutorial e instalar Archlinux dentro de WSL2, continúa con la segunda parte.

{% highlight bash%}

{% endhighlight %}