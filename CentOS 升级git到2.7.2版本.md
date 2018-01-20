#CentOS 升级git到2.7.2版本

[陈养彬 http://www.ybchen.com](http://www.ybchen.com "陈养彬") 2018-1-20 21:24:05 

CentOS系统可以使用`yum install git`, CentOS 6.5默认的版本为1.7.1，对于很多的Git服务器来说，这个版本有些老了。
因为最新Linux内核的git版本都到2.9.5了，所以我决定升级到2.7.2版本。

##1.系统安装需求

	# yum install -y tk zlib-devel openssl-devel perl cpio expat-devel gettext-devel asciidoc xmlto    
	# yum install -y curl-devel expat-devel gcc perl-ExtUtils-MakeMaker

##2.卸载Centos6.5自带的git1.7.1

通过`git –-version`查看系统带的版本，Cento6.5应该自带的是git版本是1.7.1。
运行

    # yum remove git

卸载Cento6.5应该自带的是git。

##3.下载git最新版本

    # cd ~/
    # wget https://www.kernel.org/pub/software/scm/git/git-2.7.2.tar.gz
    # tar xzf git-2.7.2.tar.gz

##4.安装git并添加到环境变量中

    # cd git-2.7.2
    # make configure
    # ./configure --prefix=/usr/local/git --with-iconv=/usr/local/libiconv
    # make all doc
    # make install install-doc install-html
    # echo "export PATH=$PATH:/usr/local/git/bin" >> /etc/bashrc
    # source /etc/profile

##5.检测验证版本号

    # git --version
    git version 2.7.2
