---
layout: post
featured: false
title: "¿Querés que tu Arch se vea hermoso? Acá te dejo mis DOTFILES"
description: Te gustaría tener un Arch hermoso, sin gastar mucho esfuerzo y tiempo
  aprendiendo. Bueno, acá te dejo mis DOTFILES para que puedas utilizarlo cuando quieras,
  y cuantas veces quieras.
date: 2021-12-27T03:00:00.000+00:00
image: https://i.imgur.com/ePgG6Wl.png
tags:
- Linux
- Documentacion
- Dotfiles

---
![https://camo.githubusercontent.com/57dc81b1e0993770e553e1f70ca9ba0b0e0d1c2d4982d71eb232b05133b0e6ba/68747470733a2f2f692e696d6775722e636f6d2f775136696838382e706e67](https://camo.githubusercontent.com/57dc81b1e0993770e553e1f70ca9ba0b0e0d1c2d4982d71eb232b05133b0e6ba/68747470733a2f2f692e696d6775722e636f6d2f775136696838382e706e67)

***

🙋‍♂️Hola, si estás acá dejame decirte **¡muchas gracias por visitar este post! Me ayudarías muchisimo si lo compartes con alguien.**

Esta es mi **configuración personal**. Utilizando un WM no muy conocido, y ademas, algunas configuraciones que utilizo frecuentemente. Junto con, tal vez, algunos consejos.

Espero que se entienda todo. Y **si hay algo que explico mal, o que ustedes creen que podría mejorar.** Me lo pueden hacer saber en [este link](https://github.com/linuxmobile/linuxmobile.github.io/issues). 😉

Algunos detalles sobre mi **Desktop**.

* **Window Manager** • [Hypr ](https://github.com/vaxerski/Hypr)🎨 Animaciones Everywhere!
* **Shell** • [Zsh](https://www.zsh.org) 🐚 con [oh-my-zsh](https://github.com/ohmyzsh/ohmyzsh) framework!
* **Terminal** • [Kitty](https://github.com/kovidgoyal/kitty) 💻 Una terminal que soporta imagenes!
* **Panel** • [Polybar ](https://github.com/polybar/polybar)🍧 Sencilla, sin lujos!
* **Compositor** • [Picom](https://github.com/yshui/picom) 🍩 rounded corners y mucho BLUR!
* **Notify Daemon** • [Dunst](https://github.com/dunst-project/dunst) 🍃 minimalista!
* **Launcher** • [Rofi](https://github.com/davatorium/rofi) 🚀 Realmente rápido y customizable!
* **File Manager** • [Thunar](https://github.com/xfce-mirror/thunar) y [Ranger ](https://github.com/ranger/ranger)🔖 customizado!
* **GUI Basic-IDE** • [Geany](https://www.geany.org) 🗒️Un IDE muy livianito!

## Este es mi actual desktop

<div class="video">
<iframe src="https://www.youtube.com/embed/8RDsBZiNLTA" frameborder="0" allowfullscreen></iframe>
</div>

## 🌸 Setup

Esto va a ser un intento de un "paso a paso". Pero siempre recomiendo no copiar y pegar al pie de la letra. Sino "inspirarse".  
Como suelen decir en la comunidad de linux. Solamente [R.T.F.M](https://en.wikipedia.org/wiki/RTFM).

### Instalación (dependencias)

    Primero que nada un breve "disclaimer". Esta configuración es la que estoy utilizando actualmente. Está pensado para funcionar en Archlinux, y para dejar el escritorio tal cual lo tengo yo. Por lo tanto, si estás utilizando otra distribución vas a tener que instalar las dependencias en base a ello. Así que si no utilizas Archlinux, no deberías copiar y pegar.

#### Instalando Paru como AUR Helper 🆘

{% highlight bash %}  
\# For Aur Helper install Paru
echo "### Installing paru as AUR Helper"
mkdir $HOME/Downloads/_cloned-repos
cd $HOME/Downloads/_cloned-repos
git clone https://aur.archlinux.org/paru.git
cd paru
makepkg -si  
{% endhighlight %}

#### Instalamos Oh-My-Zsh 🐚

{% highlight bash %}  
\# First install Oh-My-Zsh  
echo "### Installing oh-my-zsh"  
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"  
{% endhighlight %}

#### Instalando los paquetes requeridos 📦

{% highlight bash %}  
echo "### Installing Required Packages"
paru -S python ffmpeg pulseaudio pulseaudio-alsa alsa-utils dunst xclip scrot  \\
thunar thunar-archive-plugin thunar-volman ffmpegthumbnailer tumbler w3m       \\
viewnior mpv neofetch htop xsettingsd picom-jonaburg-git rofi rsync firefox    \\
ranger python-pip noto-fonts-emoji noto-fonts-cjk python-pillow-git xwallpaper \\
exa bat file-roller geany geany-plugins gvfs gvfs-mtp htop kitty wal-git       \\
lxappearance pavucontrol nerd-fonts-complete polybar  
{% endhighlight %}

#### Instalamos Oh-My-Zsh Plugins 🔌

{% highlight bash %}  
echo "### Installing Oh-My-Zsh Plugins"
git clone --depth 1 https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-\~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
git clone --depth 1 https://github.com/zsh-users/zsh-autosuggestions.git ${ZSH_CUSTOM:-\~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
git clone --depth 1 https://github.com/zsh-users/zsh-completions.git ${ZSH_CUSTOM:-\~/.oh-my-zsh/custom}/plugins/zsh-completions  
{% endhighlight %}

#### Instalamos Hypr WM 🪟

##### Primero vamos a instalar las dependencias.

{% highlight bash %}  
sudo pacman -S --needed cairo gdb ninja gcc cmake libxcb xcb-proto xcb-util xcb-util-cursor xcb-util-image xcb-util-keysyms xcb-util-renderutil xcb-util-wm xcb-util-xrm gtkmm gtk4 gtkmm3  
{% endhighlight %}

##### Compilamos Hypr WM

{% highlight bash %}  
cd $HOME/Downloads/_cloned-repos
git clone https://github.com/vaxerski/Hypr
cd Hypr
make clear && make release  
{% endhighlight %}

##### Y copiamos los archivos necesarios.

{% highlight bash %}  
cd $HOME/Downloads/_cloned-repos/Hypr  
sudo cp build/Hypr /usr/bin/  
sudo cp example/hypr.desktop /usr/share/xsessions/  
{% endhighlight %}

#### Ahora procedemos a Clonar y copiar los Dotfiles

##### Clonamos y Copiamos

{% highlight bash %}  
git clone https://github.com/linuxmobile/dotfiles $HOME/dotfiles/  
cd $HOME/dotfiles/
rsync -avxHAXP --exclude '.git*' .* \~/  
{% endhighlight %}

##### Agregamos los iconos

{% highlight bash %}  
pushd \~/.icons/ && \\
tar -xJf Papirus-Custom.tar.xz && tar -xJf Papirus-Dark-Custom.tar.xz && \\
sudo ln -vs \~/.icons/Papirus-Custom /usr/share/icons/
sudo ln -vs \~/.icons/Papirus-Dark-Custom /usr/share/icons/
rm -rf *.tar.xz
popd  
{% endhighlight %}

##### Por último actualizamos las fuentes

{% highlight bash %}  
fc-cache -rv  
{% endhighlight %}

    Eso es todo lo necesario. Tal vez necesite ir actualizando este post, ya que siempre es necesario mantener actualizado todo. Quizá faltan cosas, porque me olvidé o por alguna razón. Así que agregaré todo lo necesario con el tiempo.

### Les dejo un video de mi anterior Desktop

<div class="video"> <iframe src="https://www.youtube.com/embed/tiGCbY3EXks" frameborder="0" allowfullscreen></iframe> </div>

### Creditos

_A la hermosa comunidad de_ [_r/unixporn_](https://www.reddit.com/r/unixporn)_._

**_©_** _A todos los artistas que crearon los iconis, ilustraciones, y wallpapers._

**_©_** _A cada uno que ha creado y mantiene los proyectos que he mencionado y utilizado anteriormente._