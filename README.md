# In Progress
# CHIP: CHannel Independence-based Pruning for Compact Neural Networks

## Code for our NeurIPS 2021 paper: ([CHIP: CHannel Independence-based Pruning for Compact Neural Networks](https://arxiv.org/abs/2110.13981))![visitors](https://visitor-badge.glitch.me/badge?page_id=yangsui.chip&left_color=green&right_color=red).

<p align="center">
<img src="fig/algorithm.png" width="800">
</p>

## Usage

### Generate Feature Maps.
```shell
python calculate_feature_maps.py \
--arch resnet_56 \
--dataset cifar10 \
--data_dir ./data \
--pretrain_dir ./pretrain_model/resnet_56.pt \
--gpu 0
```

### Generate Channel Independence (CI).
```shell
python calculate_ci.py \
--arch resnet_56
```

### Prune and Fine-tune Models.

##### 1. CIFAR-10
```shell
python prune_finetune_cifar.py \
--data_dir ./data \
--result_dir ./result/resnet_56/1 \
--arch resnet_56 \
--ci_dir ./CI_resnet_56 \
--batch_size 256 \
--epochs 200 \
--lr_type cos \
--learning_rate 0.01 \
--momentum 0.99 \
--weight_decay 0.001 \
--pretrain_dir ./pretrain_model/resnet_56.pt \
--sparsity [0.]+[0.4]*2+[0.5]*9+[0.6]*9+[0.7]*9 \
--gpu 0
```
##### 2. ImageNet
```shell
python prune_finetune_imagenet.py \
--data_dir ./imagenet \
--result_dir ./result/resnet_50/1 \
--arch resnet_50 \
--ci_dir ./CI_resnet_50 \
--batch_size 256 \
--epochs 200 \
--lr_type cos \
--learning_rate 0.01 \
--momentum 0.99 \
--weight_decay 0.001 \
--pretrain_dir ./pretrain_model/resnet_50.pt \
--sparsity [xx] \
--gpu 0
```
### Results
##### CIFAR-10
TBD.

##### ImageNet
TBD.

## Others
Some codes are based on [link](https://github.com/lmbxmu/HRankPlus).

## Citation

TBD.