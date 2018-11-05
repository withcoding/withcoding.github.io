.. title: Ubuntu自动下载Bing每日一图，并自动换壁纸
.. slug: ubuntuzi-dong-xia-zai-bingmei-ri-yi-tu-bing-zi-dong-huan-bi-zhi
.. date: 2018-11-05 20:55:33 UTC+08:00
.. tags: Ubuntu, Python
.. category: Python
.. link: 
.. description: 
.. type: text


基本的逻辑部分。

::

   >> emacs /usr/local/bin/switchwallpaper.py


.. code-block :: python
    :linenos:

    import requests
    import time
    import os
    import random

    img_url = "https://area.sinaapp.com/bingImg/"
    date = time.localtime()
    year = date.tm_year
    month = date.tm_mon
    day = date.tm_mday
    filename = "bing_%s_%s_%s.jpg" % (year, month, day)
    wallpaperdir = "/home/long/wallpapers/"

    if os.path.exists(wallpaperdir + filename):
        pass
    else:
        r = requests.get(img_url)
        with open(wallpaperdir + "%s" % filename, "wb") as f:
            f.write(r.content)

    filelist = os.listdir(wallpaperdir)
    aimfile = random.choice(filelist)

    os.system("/usr/bin/gsettings set org.gnome.desktop.background picture-uri 'file://" +
              wallpaperdir+"%s'" % aimfile)


**ps** 需要格外注意的是最后一行代码，也就是gsettings的使用。


系统命令部分

::

   >> emacs /usr/bin/switcher


.. code-block :: shell
    :linenos:

    #!/bin/sh

    PID=$(pgrep gnome-session | tail -n1)
    export DBUS_SESSION_BUS_ADDRESS=$(grep -z DBUS_SESSION_BUS_ADDRESS /proc/$PID/environ|cut -d= -f2-)

    python3 /usr/local/bin/switchwallpaper.py

**ps** 中间的两句是关键，如果没有中间的两句，无法实现命令行切换壁纸。


::

   >> sudo crontab -u long -e


.. code-block :: shell
    :linenos:

    */10 * * * * /usr/bin/switcher

**ps** 用于设置每10分钟执行一次。


最后展示一下效果 ^O^


    .. image:: /1-pics/bg1.png

 




