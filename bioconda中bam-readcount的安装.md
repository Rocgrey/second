### bam-readcount的安装及使用： 
## 1.首先下载Miniconda，Miniconda的官网上找到对应miniconda对应系统的下载地址：
### wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
## 2.下载完成之后，会看到下载的文件夹下有一个sh结尾的文件，# 注意：这里一定要用bash命令来运行sh脚本！
###  如果直接使用sh Miniconda2-latest-Linux-x86_64.sh则会报错，所以，：
### bash Miniconda3-latest-Linux-x86_64.sh
## 3.运行过程中会问起，是否安装在$HOME目录下，是否将路径写到.bashrc中。一路回车即可
## 在~/.bashrc中添加： export PATH="/home/roc/miniconda3/bin:$PATH"，然后
### source ~/.bashrc
## 4.添加channel
## 目前清华大学提供了一个conda的镜像，添加后可以非常快速的下载软件，具体添加方法如下：
### conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free
### conda config --set show_channel_urls yes
## 完成后打开$HOME/.condarc可以查看到结果
### 在对bam文件进行bam-readcount时，每一个bam文件相对应有一个索引文件，*.bai,要和*.bam放在同一个文件夹下才行。
