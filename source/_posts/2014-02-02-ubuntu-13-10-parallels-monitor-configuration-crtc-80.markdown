---
layout: post
title: "Ubuntu 13.10 in Parallels - CRTC 80 Error"
date: 2014-02-02 16:01:16 +0500
comments: true
categories: 
---

Last night I spent hours configuring Ubuntu and Installing Dependencies, programs and God-knows-what for a new Hobby Project of mine, [Pupil](http://pupil-labs.com/pupil/).

It was a clean installation of Ubuntu 13.10 in Parallels 9 on my new Macbook. I had invested too much time installing pupil, only to find that the display drivers or GTK or something had been corrupted. This was the second time I was booting ubuntu and had been slapped in the face by this:

<!--more-->

{% codeblock %}
Could not switch the Monitor Configuration
could not set the configuration for CRTC 80
{% endcodeblock %}

**image**

I restarted it, but received the same error. The login screen was perfect, mind you; The error presented it self only after logging in. There was nothing else; No Icons, no Menu bar, no Unity. I googled for hours and tried everything I could; [Using xrandr](http://ubuntuforums.org/showthread.php?t=1835391), [Editing xorg.conf](http://kb.parallels.com/en/114097), [Running Parallels Troubleshooter](http://www.parallels.com/support/desktop/troubleshooter-en_US) and so much more. In the end, I was somewhat able to restore my installation by reinstalling my Parallels Desktop Tools.

These are the exact steps I followed after logging in:

1. Press `Control + Alt + F1`
2. In the full-screen terminal, login with your credentials
3. In the Parallels Desktop Menu, select *Devices > CD/DVD 1 > Connect Image*
4. In the new Finder dialog, browse to *Applications > Parallels Desktop > Contents > Resources > Tools > pri-tools-lin.iso*
5. Now back in your terminal screen, type the following commands:

{% codeblock lang:bash%}
sudo mkdir /media/cdrom
sudo mount /dev/sr0 /media/cdrom
cd /media/cdrom
sudo ./install
{% endcodeblock %}

Parallels Tools' installation will begin. Go through the steps and complete the installation. After that, reboot using: `$ sudo reboot`

If everything went fine, you would at least be able to see your desktop. In my case, there was no Unity Sidebar or the top Menu Bar; But it's still something. Maybe installing Gnome would help.

**Lesson:** Make regular *Snapshots* of your OSes in Parallels
