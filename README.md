# JetsonNotes

## jtop install
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install python3-pip
sudo -H pip3 install -U jetson-stats

sudo reboot
jtop
```
![image](https://github.com/jeonggunlee/JetsonNotes/assets/7118106/ff1b788d-d866-44d7-b91b-a60abe48bca3)

## onnx install

```
sudo python3 -m pip install onnx
```

## torch and torchvision install
Follow the [guide](https://forums.developer.nvidia.com/t/pytorch-for-jetson/72048)

```
$ sudo apt-get install libjpeg-dev zlib1g-dev libpython3-dev libopenblas-dev libavcodec-dev libavformat-dev libswscale-dev
$ git clone --branch <version> https://github.com/pytorch/vision torchvision   # see below for version of torchvision to download
      # git clone --branch 0.15.1 https://github.com/pytorch/vision torchvision
$ cd torchvision
$ export BUILD_VERSION=0.x.0  # where 0.x.0 is the torchvision version
      # export BUILD_VERSION=0.15.1
$ python3 setup.py install --user
$ cd ../  # attempting to load torchvision from build dir will result in import error
$ pip install 'pillow<7' # always needed for Python 2.7, not needed torchvision v0.5.0+ with Python 3.6
```

## tensorRT
TensorRT: 8.5.2.2
  - binary directory: /usr/src/tensorrt/bin/


## DeepStream
Refer to [the site](https://wiki.seeedstudio.com/YOLOv8-DeepStream-TRT-Jetson/)
