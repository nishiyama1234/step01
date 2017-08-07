# snort インストール手順

### 環境
- CentOS (2.6.32-696.6.3.el6.x86_64)
- CPU:2core,MEM:2048MB,HDD:50GB onVMwarevSphere6
- epelリポジトリを追加してある


### 前提
- 作業はrootアカウント
- ライブラリのパス等のパラメータはカスタマイズしない(RPMに任せる)


### 事前作業
###### 1. 本インストール手順で要求されるパッケージを予めインストールしておく
yum install autoconf automake bison flex gcc libpcap-devel pcre-devel rpm-rebuild zlib-devel

###### 2. NFQを有効にする(DAQインストール時)ために必要なパッケージを予めインストールしておく
yum install libnetfilter_queue libnetfilter_queue-devel

###### 3. snortインストールで要求されるパッケージを予めインストールしておく
yum install libdnet linbdnet-devel


### インストール手順
###### 4. DAQ(Data Acquisition Liblary)のインストール
cd /root

wget https://www.snort.org/downloads/snort/daq-2.0.6-1.src.rpm

rpmbuild --rebuild daq-2.0.6-1.src.rpm

cd /root/rpmbuild/RPMS/x86_64/

rpm -Uvh daq-2.0.6-1.x86_64.rpm

###### 5. snortのインストール
cd /root

wget https://www.snort.org/downloads/snort/snort-2.9.9.0.tar.gz

rpmbuild -tb --clean snort-2.9.9.0.tar.gz

cd /root/rpmbuild/RPMS/x86_64/

rpm -Uvh snort-2.9.9.0-1.x86_64.rpm
