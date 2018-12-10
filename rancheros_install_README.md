# rancheros install 
需要docker 17.03.1-ce 版本 太高了不支持k8s
https://releases.rancher.com/os/v1.0.4/rancheros.iso
rancheros 安装到硬盘
rancheros.iso启动
修改rancher 密码
sudo passwd rancher
sudo passed
在本地编辑cloud-config
在本地创建密钥
ssh-keygen -t rsa
将公钥导入到cloud-config中
在本地创建 cloud-config.yml
Scp cloud-config.yml  rancher@192.168.3.20:/tmp
将cloud-config cp到/var/lib/rancher/conf/中

用root执行
sudo ros install -c cloud-config.yml -d /dev/sda

#cloud-config

rancher:
    network:
        interfaces:
            eth0:
                address: 192.168.88.105/24
                gateway: 192.168.88.254
                mtu: 1500
                dhcp: false

ssh_authorized_keys:
    - ssh-rsa 公钥内容粘贴写在这里
