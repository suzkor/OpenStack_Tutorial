# OpenStack_Tutorial
OpenStack個人学習の忘備録

# OpenStackってなぁに
クラウドインフラ提供するプラットフォーム  
https://www.redhat.com/ja/topics/openstack

オンプレでクラウドマシン提供できる？  
コンポーネントごとに分離してて、なんかk8sみがある

とりま作って試してみよう

# 環境構築
何ステップかに分けてやる（予定）
1. All-in-One on VM
1. ? All-in-One on Docker
1. ? VMs
1. ? k8s

## 1 参考通りにAll-in-One on VM

せっかくコンポーネントごとに分離できんのに1台にまとめるのはあれだけど、とりまテストなので最初はこれで  
[参考ココ](https://qiita.com/A0yama_anpl/items/126dfdaffe884c0bd6cf)

### CentOS 7 DL
[ここからDL](http://ftp.jaist.ac.jp/pub/Linux/CentOS/7/isos/x86_64/)
### VirtualboxでVM作成  
[参考ここ](https://qiita.com/mfujita/items/ee2da9d1e241926fc790)、一部改変  
[改変箇所1](https://qiita.com/mfujita/items/ee2da9d1e241926fc790#4-%E3%82%AB%E3%83%BC%E3%83%8D%E3%83%AB%E3%83%91%E3%83%A9%E3%83%A1%E3%83%BC%E3%82%BF%E3%81%AE%E5%A4%89%E6%9B%B4)
```shell-session
# sysctl -p
net.ipv4.ip_forward = 1
net.ipv4.conf.all.rp_filter = 0
net.ipv4.conf.default.rp_filter = 0
sysctl: cannot stat /proc/sys/net/bridge/bridge-nf-call-arptables: No such file or directory
sysctl: cannot stat /proc/sys/net/bridge/bridge-nf-call-iptables: No such file or directory
sysctl: cannot stat /proc/sys/net/bridge/bridge-nf-call-ip6tables: No such file or directory
# modprobe br_netfilter
# sysctl -p
net.ipv4.ip_forward = 1
net.ipv4.conf.all.rp_filter = 0
net.ipv4.conf.default.rp_filter = 0
net.bridge.bridge-nf-call-arptables = 1
net.bridge.bridge-nf-call-iptables = 1
net.bridge.bridge-nf-call-ip6tables = 1
```
ここまでやったら参考変更

### Install
[参考ここから](https://qiita.com/A0yama_anpl/items/126dfdaffe884c0bd6cf#%E6%89%8B%E9%A0%86)


