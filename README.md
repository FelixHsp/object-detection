### 数据集准备
将自己要训练的图像准备好，并将其分为两部分放入code/Tensorflow/workspace/images/train和code/Tensorflow/workspace/images/test中。建议train中放70%，test中放30%。
### 环境安装
使用anaconda创建一个独立环境。
#### 安装tensorflow
可以选择安装GPU版或CPU版，建议个人电脑直接安装CPU版。GPU版本安装可自行百度。如果使用云GPU服务器，一般会有安装好tensorflow-GPU的镜像可以直接初始化来用。
```
// 不是一定要安装2.3.1版本，但至少应是2.0.0以上
pip install tensorflow==2.3.1
```
#### 安装protoc
```
git clone https://github.com/protocolbuffers/protobuf.git
yum install -y autoreconf automake  libtool
./autogen.sh 

./configure

make 

sudo make install

sudo ldconfig 
# 测试是否安装成功
protoc -h 
```
#### 安装protobuf
```
cd code/Tensorflow/models/research

protoc object_detection/protos/*.proto --python_out=.
```

#### 安装COCO API
```
pip install cython
pip install git+https://github.com/philferriere/cocoapi.git#subdirectory=PythonAPI
```

#### 安装Tensorflow object detection API 
```
cd code/Tensorflow/models/research

cp object_detection/packages/tf2/setup.py .
python -m pip install .

# 检验是否安装成功
python object_detection/builders/model_builder_tf2_test.py
```

#### 模型配置及训练
打开code下的Tutorial.ipynb，跟着执行每一步即可- -。