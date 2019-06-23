# OCR
## Operate Online
项目已部署到服务器，可通过公网IP (http://139.224.132.209/) 进行访问。
## Local Operation
### 环境配置
Ubuntu18.04 + Python3.6 + Tensorflow

Win10 + Python3.7 + Tensorflow
```
git clone
virtualenv --no-site-packages --python=python3 venv
source venv/bin/activate
pip install -r requirements
```
### 配置CTPN
在Linux环境下执行以下代码
```
cd ctpn/utils/bbox
chmod +x make.sh
./make.sh
#会在当前目录下生成nms.so和bbox.so文件
```
在Win环境下执行以下代码
```
cd ctpn/utils/bbox
python setup.py install
#在文件夹中找到*.pyd后缀的文件，移至当前目录下
```
### Prepare Data
#### CTPN
- 下载 checkpoint file
- 把 checkpoints_mlt/ 移至 ctpn/
#### CRNN
- 下载预训练的模型
- 将模型移至 crnn/
- 在 crnn/densenet/model.py 中，修改 modelPath 可以选择要使用的模型文件
### Run
```
python run.py
```
浏览器打开本地链接：http://127.0.0.1:5000/

![图片]()
## Training
### CRNN
#### 1.Prepare data
- 通过数据增强将原始数据集扩充
```shell
python aug.py
```
- 将扩充过后的数据集分为训练集和验证集，生成 train.txt 和 test.txt
```shell
python cd.py
```


#### 2.Training
```shell
cd python
python train.py
```
## 效果展示
