# 新节点加入流程
## 环境 
- ubuntu18.04
## 下载安装
### 下载

```shell
cd ~/ && git clone https://github.com/FISCO-BCOS/generator.git
```
### 获取节点二进制
```shell
cd ~/generator && bash ./scripts/install.sh
./generator --download_fisco ./meta --cdn
```
### 检查二进制版本
若成功，输出 FISCO-BCOS Version : x.x.x-x
```shell
./meta/fisco-bcos -v
```
## 初始化机构
### 向颁发机构申请链证书
联系创世节点（血液链创建方，下同）将链证书ca.crt、机构证书agency.crt、机构私钥agency.key至目录~/generator/dir_agency_ca/agency下
```shell
ls ~/generator/dir_agency_ca/agency
# 从左至右分别为机构证书、机构私钥、链证书
agency.crt  agency.key  ca.crt
```
### 将文件拷贝到meta目录下
```shell
cp -r ./dir_agency_ca/agency/* ./meta/
# 从左至右分别为机构证书、机构私钥、链证书、fisco-bcos、readme
agency.crt  agency.key  ca.crt fisco-bcos README.md
```
## 修改配置文件
```shell
vim ./conf/node_deployment.ini
# 将p2p_ip的值127.0.0.1换成服务器公网ip
```
```shell

[group]group_id=1

[node0]
; host ip for the communication among peers.
; Please use your ssh login ip.
p2p_ip=本服务器公网ip
; listen ip for the communication between sdk clients.
; This ip is the same as p2p_ip for physical host.
; But for virtual host e.g. vps servers, it is usually different from p2p_ip.
; You can check accessible addresses of your network card.
; Please see https://tecadmin.net/check-ip-address-ubuntu-18-04-desktop/
; for more instructions.
rpc_ip=127.0.0.1
p2p_listen_port=30302
channel_listen_port=20202
jsonrpc_listen_port=8547

[node1]
p2p_ip=本服务器公网ip
rpc_ip=127.0.0.1
p2p_listen_port=30303
channel_listen_port=20203
jsonrpc_listen_port=8548
```
## 生成并发送节点信息
生成节点证书及P2P连接信息文件，此步需要用到上述配置的node_deployment.ini，及meta文件夹下的机构证书与私钥，机构生成节点证书及P2P连接信息文件
```shell
./generator --generate_all_certificates ./agency_node_info
```
查看生成文件:
```shell
ls ./agency_node_info
# 从左至右分别为需要交互给机构A的节点证书，节点P2P连接地址文件(根据node_deployment.ini生成的本机构节点信息)
cert_公网ip_30300.crt cert_公网ip_30301.crt peers.txt
```
```shell
cp ./agency_node_info/cert*.crt ~/generator/meta/
```
咨询创世节点获取p2p连接文件，将其它节点的p2p连接地址保存到meta目录下的otherPeers.txt中

```shell
vim ./meta/otherPeers.txt
#加入其它节点的p2p连接地址
例如：
203.195.138.240:30300
203.195.138.240:30301
```

## 获取群组创世块信息

咨询创世节点，获取创世区块信息group.1.genesis，保存至./meta中

## 生成本机构所属节点
```shell
./generator --build_install_package ./meta/otherPeers.txt ./node
```
启动节点:
```shell
bash ./node/start_all.sh
```
查看节点进程：
```shell
ps -ef | grep fisco
```
```shell
# 命令解释# 可以看到类似如下进程
fisco  15347     1  0 17:22 pts/2    00:00:00 ~/generator-A/nodeA/node_127.0.0.1_30300/fisco-bcos -c config.ini
fisco  15402     1  0 17:22 pts/2    00:00:00 ~/generator-A/nodeA/node_127.0.0.1_30301/fisco-bcos -c config.ini
```
## 查看节点nodeid
```shell
 cat ./node/node_本服务器公网ip_30300/conf/node.nodeid
 # 可以看到类似于如下nodeid
ea2ca519148cafc3e92c8d9a8572b41ea2f62d0d19e99273ee18cccd34ab50079b4ec82fe5f4ae51bd95dd788811c97153ece8c05eac7a5ae34c96454c4d3123
```
## 上报节点nodeid
联系创世节点，将本节点的nodeid信息上报给创世节点，请求加入到节点网络中
##  查看群组节点运行状态
创世节点将本节点添加进节点网络之后，查看节点log
```shell
tail -f ./node*/node*/log/log*  | grep +++
```
```shell
# log中打印的+++即为节点正常共识
info|2019-02-25 17:25:56.028692| [g:1][p:264][CONSENSUS][SEALER]++++++++++++++++ Generating seal on,blkNum=1,tx=0,myIdx=0,hash=833bd983...
info|2019-02-25 17:25:59.058625| [g:1][p:264][CONSENSUS][SEALER]++++++++++++++++ Generating seal on,blkNum=1,tx=0,myIdx=0,hash=343b1141...
info|2019-02-25 17:25:57.038284| [g:1][p:264][CONSENSUS][SEALER]++++++++++++++++ Generating seal on,blkNum=1,tx=0,myIdx=1,hash=ea85c27b...
```
## 上报本节点的p2p连接地址
联系创世节点，将本机构的p2p连接地址上报
```shell
# 类似以下格式
111.229.7.134:30300
111.229.7.134:30301
```