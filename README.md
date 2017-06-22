# Convert caffe to pytorch
# Convert caffe to torch
# Convert torch to pytorch
+ [x] Convert caffe model to pytorch model
+ [x] Convert caffe model to torch model
+ [x] Convert torch model to pytorch model

* I have tested on vgg16, it behaves well on classification tasks. But I can't guarantee it performs well on other tasks（such as object detection and semantic segmentation). You can try it and modify the code according the bug info. If there are new components in your caffe model, you should add corresponding parts in the code。


## [Install torch](http://torch.ch/docs/getting-started.html#_)

## [install loadcaffe](https://github.com/szagoruyko/loadcaffe)

## Convert caffe to torch
* Change the path to your own path.

* Put the `.prototxt` and `.caffemodel` file in the same folder.

* You will get the `vgg16_torch.t7` file.

```
th caffemodel_to_t7.lua
```

## Convert torch to pytorch

```bash
python convert_torch.py -m vgg16_torch.t7
```
Two file will be created ```vgg16_torch.py``` ```vgg16_torch.pth```


## Load the .pth model in python
* Make sure the ```vgg16_torch.py``` and ```vgg16_torch.pth``` files in the same folder with the python workspace.
* The ```import vgg16_torch``` means importing the model structure from the ```vgg16_torch.py```.
* The ```model.load_state_dict``` means loading weights from ```vgg16_torch.pth``` into the model structure.
```python
import vgg16_torch

model = vgg16_torch.vgg16_torch
model.load_state_dict(torch.load('vgg16_torch.pth'))
model.eval()
...
```

# Acknowledgement
* The caffe to torch code is modified from [https://github.com/jcjohnson/pytorch-vgg](https://github.com/jcjohnson/pytorch-vgg)

* The torch to pytorch code is borrowed from [https://github.com/clcarwin/convert_torch_to_pytorch](https://github.com/clcarwin/convert_torch_to_pytorch)

