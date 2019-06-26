# OCR
## Operate Online
项目已部署到服务器，可通过公网IP进行访问。
## Local Operation
### 环境配置
Ubuntu18.04 + Python3.6 + Tensorflow + keras

Win10 + Python3.7 + Tensorflow + keras
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
<div align = "left">
    <img src="https://upload-images.jianshu.io/upload_images/16784976-e756949a8057fae6.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1080/q/50" width = "200" height = "350" alt="图片名称" align=center /> <img src="https://upload-images.jianshu.io/upload_images/16784976-b68d8ecb533a78f9.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1080/q/50" width = "200" height = "350" alt="图片名称" align=center /> <img src="https://upload-images.jianshu.io/upload_images/16784976-7642bffe2fd16c9b.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1080/q/50" width = "200" height = "350" alt="图片名称" align=center />
</div>

## Reference
CTPN : https://github.com/eragonruan/text-detection-ctpn

DenseNet + CTC : https://github.com/YCG09/chinese_ocr
