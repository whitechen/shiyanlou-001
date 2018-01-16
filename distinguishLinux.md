# 怎样用linux命令知道系统是ubuntu还是redhat或者其它的系统？

2018-1-14 20:56:50 

## 1、第一种方法：

    # lsb_release -a
    LSB Version::core-4.0-ia32:core-4.0-noarch:graphics-4.0-ia32:graphics-4.0-noarch:printing-4.0-ia32:printing-4.0-noarch
    Distributor ID:CentOS
    Description:CentOS release 5.7 (Final)
    Release:5.7
    Codename:Final

这个命令适用于所有遵守LSB规范的的linux，包括Redhat、SuSE、Debian、Ubuntu、Centos等发行版。
接下来的命令虽不能查看当前系统名和版本，但可以显示系统核心信息。

    root@MyMail ~ # uname
    Linux
    root@MyMail ~ # uname -r
    2.6.18-164.el5
    [root@localhost ~]# uname -a
    Linux localhost.localdomain 2.6.18-194.el5 #1 SMP Fri Apr 2 14:58:35 EDT 2010 i686 i686 i386 GNU/Linux

## 2、以下二种方法适用于RedHat、CentOS

    root@MyMail ~ # cat /etc/redhat-release
    CentOS release 5.7 (Final)

登录到linux执行:

    #rpm -q redhat-release

或CentOS执行:

    root@MyMail ~ # rpm -q centos-release
    centos-release-5-7.el5.centos.1

## 3、第四种方法：
当前centos 版本与redhat对应的版本的命令
这个命令在centos下并不准确，显示的系统和版本也是Red Hat 3.4.6-10。

    # cat /proc/version
    Linux version 2.6.9-78.ELsmp (mockbuild@builder16.centos.org) (gcc version 3.4.6 20060404 (Red Hat 3.4.6-10)) #1 SMP Fri Jul 25 00:04:28 EDT 2008

而此命令在Ubuntu上使用，显示中智能看出是Ubuntu，但看不出版本。

## 4、最后一种方法：

    #cat /etc/issue

在CentOS下执行显示为：

    CentOS release 5.7 (Final)
    Kernel \r on an \m 

或在Ubuntu下显示为：

    Ubuntu 11.04 \n \l 

可以用来查看当前正在运行的 Ubuntu 的版本号。