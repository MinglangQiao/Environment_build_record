# Code for the paper 
Code for the paper in CVPR2019, 'Multi-source weak supervision for saliency detection' ([download the pdf file](https://arxiv.org/pdf/1904.00566.pdf))

## Results

   score/datasets  |ECSSD | HKU-IS|PASCALS|SOD    |OMRON|DUTS-test| SED1|SED2|
  ---| ---  | ---   | ---   | ---   | --- | --- | ---|---|
  max$F_\beta$|.878|.856|.790|.799|.718|.767|.902|.849|
  MAE|.096|.084|.134|.167|.114|.096|.081|.097|
  
Download result maps: [OneDrive](https://1drv.ms/u/s!AqVkBGUQ01XGhx_eNt8MfQ_HpCO0) / [GoogleDrive](https://drive.google.com/file/d/1PqsH6HI_juyE6ZeDFhJ7ByscSEakwRS0/view?usp=sharing)

## Usage
### Test

0. Environment: python2.7, pytorch'0.5.0a0+54db14e'

1. [Download models](https://1drv.ms/f/s!AqVkBGUQ01XGhyeDYsaaxvAZXW7k) and put in the current folder



1. Run

```bash
python main.py \
--img_dir 'path/to/images(.jpg)' \
--gt_dir 'path/to/ground-truth(.png)'

```

### Train
[code](https://github.com/zengxianyu/trainmws)

## Citation
```
@inproceedings{zeng2019multi,
  title={Multi-source weak supervision for saliency detection},
  author={Zeng, Yu and Zhuge, Yunzhi and Lu, Huchuan and Zhang, Lihe and Qian, Mingyang and Yu, Yizhou},
  booktitle={IEEE Conference on Computer Vision and Pattern Recognition},
  year={2019}
}
```

### ml add

* enter working dir and env, mws == "没完事"
```

cd ~/1_caption_saliency_ref_code/mws
source activate mws

```

* test model
```

python main.py --img_dir "/home/ml/1_caption_saliency_ref_code/mws//datasets/ECSSD/images" \
--gt_dir "/home/ml/1_caption_saliency_ref_code/mws//datasets/ECSSD/ground_truth_mask"

```

* build env
```
conda install pytorch=0.4.1
conda install torchvision

```
If report this error, ref this [报错ImportError: No module named pycocotools.coco](https://blog.csdn.net/u013591306/article/details/79458220), but do not using make, using 'python2 setup.py build_ext --inplace' under the PythonAPI folder
```
ImportError: No module named pycocotools.coco
```
then add the following to ./datasets/build_vocab.py
```
import sys
sys.path.append('/home/ml/1_caption_saliency_ref_code/mws/datasets/env_related/coco/PythonAPI')

from pycocotools.coco import COCO
```
if encounter this
```
ImportError: No module named _mask
```
then
```
python2 setup.py build_ext --inplace
```

Then if encounter this error
```
from .resnet import *
ImportError: No module named resnet
```
Then add the following to ./models/deeplab.py
```
## ml add
from torchvision.models.resnet import *
from torchvision.models.vgg import *

from .densenet import *
# from .resnet import * # comment it 
# from .vgg import * # comment it
# from .crop_resize import CropResize ## this class seem dose not be used, comment it

```
next
```
ImportError: No module named tqdm
```
then
```
pip install tqdm
```

Bingo !





