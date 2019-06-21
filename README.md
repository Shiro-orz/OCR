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
