# Notes
my notes


## 暂时记录一下

### linux 报错记录

ssh_exchange_identification: read: Connection reset by peer 

一个歪果仁的网站上，在一个不起眼论坛的一个不起眼的帖子中一个不起眼的跟帖中，一个哥们很低调的说了句“I know this quesiton is old ,but I wanted to share some findings I had,Check if /var/empty/sshd on the server has appropriate ownership and permissions. We had a chef script that was modifile to update some directory peimisions,but indavertently updated the diectory below the intended target,chaning ownership of /var to an applicaton user/group and changing the permissons to 755."
去/var下看了看，果然权限很大，都是777,cd 到 empty 目录，果然有ssh这个文件夹，在cd进去，啥也没有了。于是直接执行两条命令： 
cd /var 
chmod -R 755 * 
然后就再次尝试了远程连接了下，竟然ok了。

看来Linux到处是坑啊，类似粗心的错误，有rm -f log * ,把当前目录下的东西都清空了；hostname命令带了一个空格，导致RAC崩溃了。听前辈的话没错儿，能不用root就不要用root，能不用root就不要用root，能不用root就不要用root！

https://blog.csdn.net/x6_9x/article/details/49983607
