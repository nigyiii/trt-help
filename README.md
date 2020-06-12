# trt-help
This repo shows a way to generate trt engine from an onnx model exported by pytorch.
* support align_corners=true when using bilinear interpolation in pytorch

```
# start a trt7 docker container
docker run -it --privileged=true --name convert-trt -v /home:/home --runtime=nvidia -e NVIDIA_VISIBLE_DEVICE=0,1,2,3 --shm-size 32G nvcr.io/nvidia/tensorrt:20.02-py3

# build tensorrt oss

# parse model
trtexec --explicitBatch --onnx=PATH_TO_ONNX_MODEL
