# 文件目录
```
|—— models      # 存放模型目录 存放网页相关前端配置
|—— modules     # 存放自己封装的encoder
|—— out         
|—— bert-base-chinese 
|—— |—— bert-base-chinese.tar.gz # bert预训练参数
|—— |—— vocab.txt # bert词典库
|—— data        # 存放数据
|—— |—— Data.py
|—— |—— small #自己合并了实体类型的数据
|—— |——|—— json_data  
|—— |——|—— npy_data  
|—— |——|——|——train
|—— |——|——|——dev
|—— |——|——|——test1
|—— |——|——|——test2
|—— |——|—— origin_data  # 存放原始数据
|—— analysis_result.ipynb  # 用来分析错误结果
|—— checkpoints # 存放训练模型参数
|—— config.py     
|—— helpData.py # 数据预处理函数
|—— mian.py     # 主函数
|—— metrics.py  # 测评函数
|—— README.md
```
# 项目环境配置
- 硬件	        配置
- 处理器	       Intel(R) Core(TM) i5-7200U
- 操作系统	  Windows10
- 内存	        4.00GB
- 编程语言	  Python3.7
- 开发工具	  Pycharm
- 深度学习框架	Pytorch1.7.1
- Python包	     jieba版本 0.42.1、sklearn版本0.23.2、xgboost版本1.2.1、gensim版本4.0.1等

# 运行方式
- 克隆项目

```
git clone https://github.com/Henkleholm/Weibo-text-Classifier.git
```
- 准备数据
    - 在这里[下载](https://pan.baidu.com/s/1ahcx4b8EnuvBjMR-2KNvRQ)数据,提取码`1111`。
    - 解压数据，放在`data/small/origin_data/`文件夹下
- 准备Bert预训练模型
    - 在这里[下载](https://pan.baidu.com/s/14MRsOjwuvHlRTC_x3_nXNQ), 提取码`2345`。将下载后的压缩文件放在`bert-base-chinese`文件夹下
- 在data/small/目录下按项目结构中所示创建所需目录
- 回到主目录，执行

```
python helpData.py
```
- 开始训练

```
python main train
```
- 预测
    - 将config.py中的`ckpt_path`更改为训练后的模型地址.
    执行：
    ```
    python main tofile --case=1
    ```
    预测结果存放在`out`文件夹下.

- 实验结果：Accuracy = 0.872	AUC = 0.929
- 实验总结：本项目提出的BERT-CNN模型在微博爬取的数据集上获得了87.2％的准确率以及0.929的AUC值，大幅度领先过去的卷积神经网络与循环神经网络分类法，且各种深度学习模型都在同一个微博数据集上总结进行性能对比分析，所有的参数均设置为各模型对应的最优参数。通过分析不同模型的准确率和AUC，证明了本项目提出的BERT-CNN模型在文本情感分类方面综合性能最优。
