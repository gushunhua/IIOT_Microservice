
## 一套面向工业生产应用的标准化服务


### 服务介绍

本课题构建出一套面向工业生产应用的标准化服务，主要体现在两个方面，**其一，全部微服务均面向工业生产**，由不同场景的工业互联网服务组建而成。对于生产层面，订单面临着工序的拆解和重新分配，由此产生工序调度的服务。对于辅助运行的层面，衍生出安全帽检测、生产要素预测等一系列计算服务。对于设备控制层面，我们使用资源池、设备孪生相关服务提升对资源的管理能力。因此，该微服务集合中主要从工业生产中的传输、计算和控制三个维度进行服务功能的设计，并使用Docker进行封装，具体分为数据处理类、算法策略类、虚拟资源池类和基础数据管理类四个大类，每类服务又分为若干小类，如下图所示：

![图片描述](./assets/images/index/markdown.png)

其二，服务镜像均上传至阿里云的镜像仓库并开源，开源仓库的地址为“registry.cn-hangzhou.aliyuncs.com/flowertree/”，开源服务镜像示例如下图所示：

![图片描述](./assets/images/index/markdown.png)

全部微服务和对应的镜像名称如下表所示：

| 微服务名称 | 镜像名称 |
| ------------- | ------------- |
| tabnet-cpu订单预测	| tabnet-cpu| 
| deflate文本压缩	| deflate-compression
| 压力传感器数据检测	| pressuredetection
| MQTT协议的信令传输管理	| mosquitto
| 先进后出调度算法	| lzh-lifo:v1
| Random随机调度算法	| lzh-random:v1
| 设备添加	| resource-add
| 计算卸载节点选择策略	| haproxy
| 日志流数据管理	| log_stream
| 网络流量调度策略	| traffic_ops_builder
| zlib文本解压缩编码	| zlib-decompression
| deflate文本解压缩编码	| deflate-decompression
| 人体检测	| detect-i-cam
| 湿度传感器数据检测	| humiditydetection
| 路由和连通性管理	| network-toolbox
| LSTM订单量预测	| naive-lstm-cpu
| 设备上线	| resource-install
| 基于redis的模拟计数管理	| val_counter
| DSANet钢种需求量预测	| dsa-net-auto
| mDDN订单量预测	| mddn-cpu
| huffman文本压缩	| huffman-compression
| 先进先出调度算法	| lzh-fifo:v1
| mmLSTM产能预测	| mmlstm-cpu
| 温度传感器数据检测	| tempdetection
| SLP_BDLSTM设备寿命预测	| slp-brlstm-cpu
| gzip文本压缩	| gzip-compression
| gzip文本解压缩编码	| gzip-decompression
| 基于rsyslog的GUI日志数据管理	| rsyslog-gui
| 资源池状态监控	| resource-read
| zlib文本压缩	| zlib-compression
| multi-LSTM订单量预测	| multi-lstm-cpu
| mmLSTM-GPU产能预测	| mmlstm-gpu
| SLP_BDLSTM-GPU设备寿命预测	| slp-brlstm-gpu
|LightGBM订单预测	| lgb
|mWDN-LSTM-CPU产能预测	| mwdn-lstm-cpu
|mWDN-LSTM-GPU产能预测	| mwdn-lstm-gpu
|BD-LSTM设备寿命预测	| slp-brlstm-cpu
|MSCNN设备寿命预测	| mscnn-cpu
|apriori-lstm钢种需求量预测	| ap-lstm-cpu
| DSANetBase钢种需求量预测	| dsa-net-base
| Transformer订单数据预测	| transformer
| 文件压缩解压缩	| compressions
| 基于web流的gzip和deflate压缩	| gzip-nginx
| 压缩信息检测	| compress-data-detection
| 设备删除	| resource-del
| Dhcp host管理	| dhcpd
| LPT最长作业优先调度算法	| lzh-lpt:v1
| SPT最短作业优先调度算法	| lzh-spt:v1
| 人工蜂群调度算法	| lzh-abc:v1
| 蚁群优化调度算法	| lzh-aco:v1
| 蚁群优化-禁忌搜索算法	| lzh-acots:v1
| 遗传算法	| lzh-genetic:v1
| 工序调度算法集合	| lzh-batch-set:v1
| 强化学习工序调度	| reinforcement-scheduling
| mDDN订单量预测gpu	| mddn-gpu
| 毫米波处理	| millimeter_wave_client
| 人脸识别	| face_recognition
| 安全帽检测cpu	| helmet_detection
| 安全帽检测gpu	| helmet_detection_gpu
| RTSP视频推流	| nginx-rtmp
| 口罩检测	| mask_detector
| 设备数据清洗	| data-clean
| 数据解析	| data-resolve
| 数据同步	| data-synchro
| 数据持久化	| data-save


### 使用方法
服务的拉取测试方法如下：
在一台装有docker的linux机器上，对镜像进行拉取测试。
输入命令: docker pull registry.cn-hangzhou.aliyuncs.com/flowertree/{镜像名字}
例如：docker pull registry.cn-hangzhou.aliyuncs.com/flowertree/data-save，有些镜像达到几个G，下载需要一段时间。如果下载失败，再次运行上述命令，重新下载即可。
![图片描述](./assets/images/index/markdown.png)
拉取成功后，输入docker images，会看到下载的镜像名，说明下载镜像成功。
![图片描述](./assets/images/index/markdown.png)
