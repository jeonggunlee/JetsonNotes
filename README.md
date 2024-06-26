# JetsonNotes

## chrome install
```
sudo snap install chromium
```

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

## CUDA supported OpenCV install
check the [link](https://github.com/Qengineering/Install-OpenCV-Jetson-Nano)

```
$ wget https://github.com/Qengineering/Install-OpenCV-Jetson-Nano/raw/main/OpenCV-4-10-0.sh
$ sudo chmod 755 ./OpenCV-4-10-0.sh
$ ./OpenCV-4-10-0.sh
```

## onnx install

```
sudo python3 -m pip install onnx
```


## torch and torchvision install

Follow the [guide](https://forums.developer.nvidia.com/t/pytorch-for-jetson/72048)

![image](https://github.com/jeonggunlee/JetsonNotes/assets/7118106/407df06d-24d5-4679-ac96-83694adf62e8)

```
wget https://nvidia.box.com/다운로드-주소/torch-2.1.0-cp310-cp310-linux_aarch64.whl
sudo apt-get install python3-pip libopenblas-base libopenmpi-dev libomp-dev
pip3 install Cython
pip3 install numpy torch-1.8.0-cp36-cp36m-linux_aarch64.whl
```

```
$ sudo apt-get install libjpeg-dev zlib1g-dev libpython3-dev libopenblas-dev libavcodec-dev libavformat-dev libswscale-dev
$ git clone --branch <version> https://github.com/pytorch/vision torchvision   # see below for version of torchvision to download
      # git clone --branch v0.16.1 https://github.com/pytorch/vision torchvision
$ cd torchvision
$ export BUILD_VERSION=0.x.0  # where 0.x.0 is the torchvision version
      # export BUILD_VERSION=0.16.1
$ python3 setup.py install --user
$ cd ../  # attempting to load torchvision from build dir will result in import error
```

## TensorRT
TensorRT: 8.5.2.2 or 8.6.2.3
  - binary directory: /usr/src/tensorrt/bin/
  - add "```export PATH=$PATH:/usr/src/tensorrt/bin/```" in .bashrc

## Yolo
```
pip3 install ultralytics
mkdir ultralytics
cd ultralytics
yolo predict model=yolov8n.pt imgsz=640 conf=0.25
```
![image](https://github.com/jeonggunlee/JetsonNotes/assets/7118106/406def27-a756-469c-a05e-cb3199ddd968)


## DeepStream
Refer to [the site](https://wiki.seeedstudio.com/YOLOv8-DeepStream-TRT-Jetson/)

```
aiac-nx@ubuntu:~$ deepstream-app --help
deepstream-app: error while loading shared libraries: libgstrtspserver-1.0.so.0: cannot open shared object file: No such file or directory
>> Need to install the library.
aiac-nx@ubuntu:~$ sudo apt-get install libgstrtspserver-1.0-0
```

```
aiac-nx@ubuntu:~$ deepstream-app --version-all
deepstream-app version 6.4.0
DeepStreamSDK 6.4.0
CUDA Driver Version: 12.2
CUDA Runtime Version: 12.2
TensorRT Version: 8.6
cuDNN Version: 8.9
libNVWarp360 Version: 2.0.1d3
```

## v4l-utils

The **v4l2-ctl** tool is used to control video4linux devices,
```
sudo apt-get install v4l-utils

v4l2-ctl --device=/dev/video1 --all

gst-launch-1.0 v4l2src device=/dev/video0 ! image/jpeg, width=1920, height=1080, framerate=30/1, format=MJPG ! nvv4l2decoder mjpeg=1 ! nvvidconv ! videocrop name=cropper  ! xvimagesink sync=False

```

Install https://github.com/jetsonhacks/camera-caps for a GUI based camera control.


