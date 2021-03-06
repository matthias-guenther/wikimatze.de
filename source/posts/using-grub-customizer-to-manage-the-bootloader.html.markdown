---
title: Using Grub Customizer to manage the Bootloader
nav: articles
date: 2015-07-09
description: Using Grub Customizer to manage the Bootloader. I have Xubuntu and Windows installed on my machine. When booting my machine I can switch between those two systems. (This article was written for Xubuntu 14.04 and runs grub-customizer 4.06.)
categories: linux, howto
---

I have [Xubuntu](http://xubuntu.org/ "Xubuntu") and [Windows](http://windows.microsoft.com/en-us/windows/windows-help#windows=windows-8 "Windows") installed on my machine. When booting my machine I can switch between those two systems. (This article was written for [Xubuntu 14.04](http://xubuntu.org/news/14-04-release/ "Xubuntu 14.04") and runs [grub-customizer 4.06](https://launchpad.net/~danielrichter2007/+archive/ubuntu/grub-customizer "grub-customizer 4.06").)


## Installation

```sh
sudo add-apt-repository ppa:danielrichter2007/grub-customizer
sudo apt-get update
sudo apt-get install grub-customizer
```


## Usage

Once you have installed it, you can can start it with `grub-customizer`.


<img src="https://farm8.staticflickr.com/7779/17189896339_1a0608aee2_o_d.png" class="big center" alt="grub-customizer main window"/>
<div class="caption">grub-customizer main window</div>


After that you can click on an entry and change the loading list:


<img src="https://farm8.staticflickr.com/7666/17350222016_5178693e19_o_d.png" class="big center" alt="grub-customizer move entries around"/>
<div class="caption">grub-customizer main window</div>


The item at the first line will be the operating system which starts first.


After programming, it's good to move Windows to the top to enjoy playing for example [Pillars of Eternity](http://eternity.obsidian.net/ "Pillars of Eternity").

