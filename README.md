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
