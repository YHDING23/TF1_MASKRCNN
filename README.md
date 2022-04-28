## A Tensorflow 1.15 Implementation of Training MaskRCNN via COCO Dataset

This script is for training a MaskRCNN Instance Segmentation model using COCO dataset. 

Reference: [Mask R-CNN for Object Detection and Segmentation](https://github.com/matterport/Mask_RCNN)

DL framework is:
- Tensorflow-GPU==1.15.0
- Python = 3.6
- CUDA >= 11.0, <=11.4 (e.g., 11.2)

Check the reference [Here](https://www.tensorflow.org/install/source#linux) and see if your CUDA version is compatible with your Tensorflow version.  

### 1 - Setup
- Clone the repo, setup the virtual env
```angular2html

git clone https://github.com/YHDING23/TF1_MASKRRCNN.git
cd TF1_MASKRCNN

mkdir venv
virtualenv -p python3.6 venv
source venv/bin/activate

pip install -r requirements.txt

python3 setup.py install
```

### 2 - Prepare the COCO dataset. 

Install a toolkit for COCO dataset pre-process: 
```angular2html
pip install "git+https://github.com/philferriere/cocoapi.git#egg=pycocotools&subdirectory=PythonAPI"
```

We have COCO dataset at multiple locations. I am using the one at `/nfs_1/data/coco`. This script use label `2014` as default. 

### 3 - Download pretrained model and Train

Reference at https://github.com/matterport/Mask_RCNN/releases

Example: I pick up the original COCO pretrained model: `mask_rcnn_coco.h5`.
```angular2html
# from Mask_RCNN/
mkdir pretrain
cd pretrain
wget https://github.com/matterport/Mask_RCNN/releases/download/v2.0/mask_rcnn_coco.h5
```

The training flags are as followings:
```angular2html
# from directory "TF1_MASKRCNN/"
python samples/coco/coco.py train --dataset=/nfs_1/data/coco --model=pretrain/mask_rcnn_coco.h5
```
