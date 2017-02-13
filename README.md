# pytorch-resnet

This repository contains codes for converting resnet50,101,152 trained in caffe to pytorch model.

First, you need to have pycaffe and pytorch. Secondly, you should download the caffe models from [https://github.com/KaimingHe/deep-residual-networks](https://github.com/KaimingHe/deep-residual-networks).  Put them in data folder.

Then,

```
python convert.py
```
or
```
python convert2.py
```

The models generated by `convert.py` expect different preprocessing than the other models in the PyTorch model zoo. Images should be in BGR format in the range [0, 255], and the following BGR values should then be subtracted from each pixel: [103.939, 116.779, 123.68].

The models generated by `convert2.py` expect RGB image ranging [0, 1]. You can use standard `trn.Normalize([0.485, 0.456, 0.406],[0.229, 0.224, 0.225])`.

## Note
This model is different from what's in pytorch model zoo. Although you can actually load the parameters into the pytorch resnet, the strucuture of caffe resnet and torch resnet are slightly different. The structure is defined in the resnet.py. (The file is almost identical to what's in torchvision, with only some slight changes.)

## Acknowledgement
A large part of the code is borrowed from [https://github.com/ry/tensorflow-resnet](https://github.com/ry/tensorflow-resnet)