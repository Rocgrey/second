
#*****************************  2018/11/16下午：安装transvar g过程中出现的错误，以及解决方法：*************************
### 00000 解决方法所有的命令如下：
#### 备份完源文件之后，更换源文件 cd /etc/apt/sources.list
#####  参考https://blog.csdn.net/xiangxianghehe/article/details/80112149
## 2021  cd /etc/
## 2022  ls
## 2023  cd /apt
## 2024  cd apt/
## 2025  ls
## 2026  sudo vim sources.list
## 2027  sudo apt-get update
## 2028  sudo apt-get upgrade
## 2029  cd
### 然后开始安装 transvar，这个过程会出现各种问题。。。 

## 2030  ls

## 2031  pip install transvar

## 2032  ls

## 2033  apt-get install build-essential

## 2034  sudo apt-get install build-essential

## 2035  pip install transvar

## 2036  sudo apt-get install python-dev

## 2037  sudo apt-get install libevent-dev

## 2038  sudo apt-get groupinstall 'development tools'

## 2039  sudo apt-get transvar install 'development tools'

## 2040  sudo apt-get transvarinstall 'development tools'

## 2041  pip install transvar

## 2042  pip install --user pytabix

## 2043  sudo apt-get install zlib1g-dev

## 2044  pip install --user pytabix

## 2045  pip install transvar
#3##
## 2046  history > error_log.md




#### 猜测,跟新完源之后可以直接从第4步的方法走起
###  1 ：按照实验记录的方法：参照https://transvar.readthedocs.io/en/latest/download_and_install.html#install-using-pip
###  依赖python2.7,没有conda镜像，创建了名字为transvar的conda环境
## conda create -n transvar python=2.7
## source activate transvar
## pip install transvar
### 然后就出现了如下错误：
##############
## gcc -pthread -fno-strict-aliasing -g -O2 -DNDEBUG -g -fwrapv -O3 -Wall -Wstrict-prototypes -fPIC -D_FILE_OFFSET_BITS=64 -D_USE_KNETFILE=1 -Iexternal/pytabix -I/home/roc/miniconda3/envs/transvar/include/python2.7 -c external/pytabix/bgzf.c -o build/temp.linux-x86_64-2.7/external/pytabix/bgzf.o -w
 ## external/pytabix/bgzf.c:25:19: fatal error: stdio.h: No such file or directory
 ## compilation terminated.
 ## error: command 'gcc' failed with exit status 1

 ## ----------------------------------------
##  Failed building wheel for transvar
##  Running setup.py clean for transvar
#############
### 2.网上搜教程：说更新源文件，但是还是出现这样的错误，所以就在更新了源之后重复了第一步的操作，仍然报同样的错，
## :~$ sudo apt-get install build-essential
## :~$ pip install transvar
###  依旧报如下错误：
###############
## gcc -pthread -fno-strict-aliasing -g -O2 -DNDEBUG -g -fwrapv -O3 -Wall -Wstrict-prototypes -fPIC -D_FILE_OFFSET_BITS=64 -D_USE_KNETFILE=1 -Iexternal/pytabix -I/home/roc/miniconda3/envs/transvar/include/python2.7 -c external/pytabix/bgzf.c -o build/temp.linux-x86_64-2.7/external/pytabix/bgzf.o -w
##  In file included from external/pytabix/bgzf.c:31:0:
##  external/pytabix/bgzf.h:33:10: fatal error: zlib.h: No such file or directory
##   #include <zlib.h>
##            ^~~~~~~~
##  compilation terminated.
##  error: command 'gcc' failed with exit status 1
###############
### 3.尝试：
## ：~$ sudo apt-get install python-dev
## :~$ sudo apt-get install libevent-dev
## :~$ pip install transvar
#### 依旧报错：
################
 ## In file included from external/pytabix/bgzf.c:31:0:
##  external/pytabix/bgzf.h:33:10: fatal error: zlib.h: No such file or directory
##   #include <zlib.h>
##            ^~~~~~~~
 ## compilation terminated.
##  error: command 'gcc' failed with exit status 1

##  ----------------------------------------
##  Failed building wheel for transvar
#################
### 4，按照报错的提示：
## :~$ pip install --user pytabix
### 此过程仍有错误：
###############
##  In file included from src/bgzf.c:31:0:
##  src/bgzf.h:33:10: fatal error: zlib.h: No such file or directory
##   #include <zlib.h>
##            ^~~~~~~~
##  compilation terminated.
##  error: command 'gcc' failed with exit status 1

##  ----------------------------------------
##  Failed building wheel for pytabix
################
### 5.换个错误的试试：
## :~$ sudo apt-get install zlib1g-dev
## ：~$ pip install --user pytabix
## :~$ pip install transvar
### 终于成功了！！！！！
## Successfully built transvar
## Installing collected packages: transvar
## Successfully installed transvar-2.4.1.20180815

#####
