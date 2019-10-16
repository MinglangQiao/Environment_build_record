# Mask R-CNN for Object Detection and Segmentation

This instruction indicates the installation steps of MASKRCNN used in the CapSal model. Please refer to the original [repository](https://github.com/matterport/Mask_RCNN.git) if you have any questions.

The repository includes:
* Source code of CapSal based on ResNet101
* Training code on COCO-CapSal
* Pre-trained weights for CapSal



# Getting Started
The codes required in the CapSal model are stored in the `CapSal`. To begin with, you should first install the requirements for the MaskRCNN benchmark.

## Requirements
Python 2.7 , TensorFlow 1.4.1, Keras 2.1.4 and other common packages listed in `requirements.txt`.

### MS COCO Requirements:
To train or test on COCO-CapSal, you'll also need:
* pycocotools (installation instructions below)
* [COCO-CapSal Dataset]()


If you use Docker, the code has been verified to work on
[this Docker container](https://hub.docker.com/r/waleedka/modern-deep-learning/).


## Installation
1. Install dependencies
   ```bash
   pip install -r requirements.txt
   ```
2. Clone this repository
3. Run setup from the repository root directory
    ```bash
    python setup.py install
    ``` 
3. Download pre-trained COCO weights (mask_rcnn_coco.h5) from the [releases page](https://github.com/matterport/Mask_RCNN/releases).
4. (Optional) To train or test on MS COCO install `pycocotools` from one of these repos. They are forks of the original pycocotools with fixes for Python3 and Windows (the official repo doesn't seem to be active anymore).

    * Linux: https://github.com/waleedka/coco

###
minglang build process record
首先，新建一个python2.7的虚拟环境
```
conda create -n salcap_py27 python=2.7
```
进入虚拟环境，然后解压一个mask-rcnn-master，将capsal文件夹中的requirements.txt, setupt.py, setup.cfg拷贝到Maskrcnn的文件夹中，覆盖原来的文件，然后
```
pip install -r requirements.txt

pip install tensorflow==1.4.1
pip install keras==2.1.4

## 再跑一次
pip install -r requirements.txt

python setup.py install

```
再把cap_sal中的data,capsal,test_cap.py拷贝到MaskRCNN中、
```
python test_capsal.py

```
会报这个错
```
from mrcnn.coco.pycocoevalcap.tokenizer.ptbtokenizer import PTBTokenizer
ImportError: No module named mrcnn.coco.pycocoevalcap.tokenizer.ptbtokenizer
```
去[这里](https://pan.baidu.com/s/1mRN_qV7X8ZLUeuARQY3EwQ)下载mrcnn,解压后放在capsal的目录下边，然后这个把mrcnn
目录下的coco文件下的所有文件拷出来，放在mrcnn目录下，否者程序还是找不到这个包
然后就ok了，再安装一些其他包
```
pip install pandas
pip install nltk
```
then set the model and img data path

然后我将放在mask-rnn下的这些文件夹又拷回了calsal的目录下，依然可以跑，所以应该在capsal的目录下配环境就行，如果配不了，再这样在mask-rcnn的
目录下配

搞定！


- step1:
```
conda create -n calsal python=2.7
pip install -r requirements.txt
```
has this error
```
ERROR: imgaug 0.3.0 has requirement scikit-image>=0.14.2, but you'll have scikit-image 0.13.1 which is incompatible
```
I ignore that
- step2:
```
python setup.py install
```
and has this error
```
error: package directory 'mrcnn' does not exist
```
- step3
run
```
python test_capsal.py
```
then
```
from numpy.lib.arraypad import _validate_lengths
ImportError: cannot import name _validate_lengths
```
then
```
pip install numpy==1.15.0
```
though this error
```
ERROR: tensorflow 2.0.0 has requirement numpy<2.0,>=1.16.0, but you'll have numpy 1.15.0 which is incompatible.
ERROR: imgaug 0.3.0 has requirement scikit-image>=0.14.2, but you'll have scikit-image 0.13.1 which is incompatible.
```
ignore it, re-run "python test_capsal.py"

encounter this
```
ImportError: No module named theano
```
then change the /home/.keras/keras.json to config tensorflow

if
```
import tensorflow.contrib.layers as layers
ImportError: No module named contrib.layers
```
check version
```
python 
import tensorflow as tf
print(tf.__version__)
```
then
```
pip install tensorflow==1.4.1
```
if this
```
from tensorflow.python.keras.utils import tf_utils
ImportError: cannot import name tf_utils
```
then
```
pip install keras==2.1.4
```
then
```
from mrcnn.coco.pycocoevalcap.tokenizer.ptbtokenizer import PTBTokenizer
ImportError: No module named mrcnn.coco.pycocoevalcap.tokenizer.ptbtokenizer
```

### try again
```
conda create -n maskrcnn python=3.6

```
then, using the uncompile raw Mask_RCNN-master
```
cd Mask_RCNN-master
```
then
```
python steup.py install
```




