# Face-Anti-spoofing-Datasets

## Person Re-Identification based on Eigenbody
- Eigenbody dataset (produced by by laboratory partners)

## Environment
- Ubuntu or Windows
- Python 2.7 or 3.5
- Numpy, Matplotlib, Pillow
- Caffe
- Matlab

## The experiments is performed on our caffe
- Our [caffe-DDM](https://github.com/liuajian/caffe-DDM) is a modified caffe fork (version of 2018/12/10) with several layers which providing whole training, testing and evaluation codes, reference on:
- [caffe](https://github.com/BVLC/caffe)
- [caffe-reid](https://github.com/D-X-Y/caffe-reid)
- [caffe-augmentation](https://github.com/twtygqyy/caffe-augmentation)
- [caffe-face](https://github.com/ydwen/caffe-face)

## Datasets
- [cuhk03](http://www.ee.cuhk.edu.hk/~rzhao/) 
- [market1501](http://www.liangzheng.org/Project/project_reid.html)(for pre-training, Imagenet dataset is used in this paper)

## Network
- [resnet50](https://github.com/KaimingHe/deep-residual-networks)

## Installation
- Clone the ReId_Eigen repository. We'll call the directory that you cloned ReId_Eigen as $ROOT_PATH.
    ```Shell
  git clone --recursive https://github.com/liuajian/ReId_Eigen.git
    ```
- Build Caffe and matcaffe
    ```Shell
  cd $ROOT_PATH/caffe-DDM
  # Now follow the Caffe installation instructions here:
  # http://caffe.berkeleyvision.org/installation.html
  make all -j8 && make matcaffe
    ```
## Usage
Note: In this session, we assume you are in the directory $ROOT_PATH/

Part 1: Preprocessing
 ```Shell
- Download the Market-1501-v15.09.15.zip and place it in the $root_path/$datasets directory
- Unzip $root_path/datasets/Market-1501-v15.09.15.zip 
- Unzip $root_path/datasets/eigen_v2.zip 
   ```
Part 2: Training
- Generate the txt files needed for training, such as train.txt, query.txt, test.txt, training_pair.txt etc.
    ```Shell
  bash start_reid.sh Step_1=True
    ```
- Convert images to lmdb if need
    ```Shell
  bash start_reid.sh Step_2=True
    ```
- Training the models,such as softmax(s)  eigen_softmax(es)  softmax_verification(sv) center_loss(cs)
    ```Shell
  bash start_reid.sh Step_3=True
    ```
Part 3: Testing
- Extracting features by python and testing by matlab
    ```Shell
  bash start_reid.sh Step_4=True
    ```
## Results
- Finally we have the `caffe.caffemodel`, extracted features `features.mat` in folder **`snapshot/`** and **`out_features/`** respectively.
- The testing results of these methods based on multi-shot setting are as follows(%): 
   ```Shell
   --------------------------------
   |Method |  s  |  es |  sv |  cs |
   |Rank-1 |74.91|77.88|79.72|80.88|
   | mAP   |50.44|55.64|57.81|59.16|
   --------------------------------
  Note Method|s:softmax|es:eigen_softmax|sv:softmax_verification|cs:center_loss
  ```
## Citation
  ```Shell
Please cite the following papers in your publications if it helps your research:
    @article{zheng2016discriminatively,
      title={A Discriminatively Learned CNN Embedding for Person Re-identification},
      author={Zheng, Zhedong and Zheng, Liang and Yang, Yi},
      journal={TOMM},
      year={2017}
    }
    @inproceedings{wen2016discriminative,
      title={A Discriminative Feature Learning Approach for Deep Face Recognition},
      author={Wen, Yandong and Zhang, Kaipeng and Li, Zhifeng and Qiao, Yu},
      booktitle={European Conference on Computer Vision},
      pages={499--515},
      year={2016},
      organization={Springer}
    }
  ```
## Questions
 
Please contact ajianliu92@gmail.com
