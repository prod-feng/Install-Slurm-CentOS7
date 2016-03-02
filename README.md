# Install-Slurm-CentOS7
Install Slurm on CentOS7

The steps I did to install Slurm 15-08.08 on Centos 7

1. Install some required packages for isnatlling Slurm, for example:

>yum install munge-devel munge

>yum install readline-devel readline

>2. Dowdload the Slurm package from its' official website.

>3. You can untar the package file and run ./configure script, and then run make command to install.

The alternative way is to use rpmbuild to do so. You may need to install rpmnuild package first:

>yum install rpm-build

Then,

>rpmbuild -ta  slurm-15.08.8.tar.bz2 

It will compile the source code and generate a few rpm files. You can then choose which Slurm packages you want to install. The basic rpm packages you need to install are:

slurm-15.08.8-1.el7.centos.x86_64.rpm

and

slurm-plugins-15.08.8-1.el7.centos.x86_64.rpm

Then you can continue to configure Slurm.

The configure script that Slurm uses by default to run rpmbuild is:

>./configure --build=x86_64-redhat-linux-gnu --host=x86_64-redhat-linux-gnu --program-prefix= --disable-dependency-tracking --prefix=/usr --exec-prefix=/usr --bindir=/usr/bin --sbindir=/usr/sbin --sysconfdir=/etc/slurm --datadir=/usr/share --includedir=/usr/include --libdir=/usr/lib64 --libexecdir=/usr/libexec --localstatedir=/var --sharedstatedir=/var/lib --mandir=/usr/share/man --infodir=/usr/share/info

3. Before run Slurm, if you choose run Munge with Slurm, you need to make sure Munge is sunning.
 
>systemctl status munge.service


