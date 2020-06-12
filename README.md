# trt-help
This repo shows a way to generate trt engine from an onnx model exported by pytorch when using align_corners bilinear interpolation.

Start a new trt7 docker container.
```
docker run -it --privileged=true --name convert-trt -v /home:/home --runtime=nvidia -e NVIDIA_VISIBLE_DEVICE=0,1,2,3 --shm-size 32G nvcr.io/nvidia/tensorrt:20.02-py3
```
Build tensorrt oss.
```
wget https://raw.githubusercontent.com/nigyiii/trt-help/master/build_OSS.sh
source build_OSS.sh
```
Parse model.
```
trtexec --explicitBatch --onnx=PATH_TO_ONNX_MODEL
```
