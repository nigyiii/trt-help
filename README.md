# trt-help
This repo shows a way to generate trt engine from an onnx model exported by pytorch when using align_corners bilinear interpolation.

```
# start a new trt7 docker container when you want to convert models
# note that if you exit the container, then re-enter this container and 
# convert pyotrch(version >= 1.3.0) exported onnx models with upsampling layers, errors will occur 

docker run -it --privileged=true --name convert-trt -v /home:/home --runtime=nvidia -e NVIDIA_VISIBLE_DEVICE=0,1,2,3 --shm-size 32G nvcr.io/nvidia/tensorrt:20.02-py3

# build tensorrt oss

wget https://raw.githubusercontent.com/nigyiii/trt-help/master/build_OSS.sh
source build_OSS.sh

# parse model

trtexec --explicitBatch --onnx=PATH_TO_ONNX_MODEL
