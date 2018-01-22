# A PyTorch implementation of MobileNetV2

This is a PyTorch implementation of MobileNetV2 architecture as described in the paper [Inverted Residuals and Linear Bottlenecks: Mobile Networks for Classification, Detection and Segmentation](https://arxiv.org/pdf/1801.04381).


## Training & Accuracy
I tried to train the model with RMSprop from scratch as described in the paper, but it does not seem to work. 

I am currently training the model with SGD and keeping other hyper-parameters the same. I will also try fine-tuning with RMSprop from SGD checkpoint in the future.

The top-1 accuracy on the ImageNet from the paper is **71.7%**. My current result is:

| Optimizer     | Epoch | Top1-acc | Pretrained Model                         |
| ------------- | ----- | -------- | ---------------------------------------- |
| RMSprop       | -     | -        | -                                        |
| SGD           | 184   | 70.636%  | [[google drive](https://drive.google.com/open?id=1MXBud3DIpwH3dKugQcVsobdU_1ehuKZD)] |
| SGD + RMSprop | TODO  | TODO     | TODO                                     |

(The training is still going on since I do not have many GPUs :(, I'll update the link if I obtain better results.)

## Usage
To use the pretrained model, run

```python
from MobileNetV2 import MobileNetV2

net = models.MobileNetV2(n_class=1000)
state_dict = torch.load('mobilenetv2.pth.tar')
net.load_state_dict(state_dict)
```

