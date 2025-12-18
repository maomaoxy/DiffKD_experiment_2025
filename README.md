# Adapting Diffusion-Based Knowledge Distillation for Robust Remote Sensing Scene Classification
论文《Adapting Diffusion-Based Knowledge Distillation for Robust Remote Sensing Scene Classification》代码复现
## Part 1 环境配置
单GPU, PyTorch版本2.7.1，Python版本3.13.5
## Part 2 重现我们的研究结果
在ResNet-34教师模型和ResNet-18学生模型基线设置下重现DiffKD的示例脚本：
### 2.1 数据准备
数据集训练与验证比例7：3。  
请从官方来源下载遥感场景分类数据集（NWPU-RESISC45, AID, EuroSAT, PatternNet）  
NWPU-RESISC45数据集下载链接(http://www.escience.cn/people/JunweiHan/NWPU-RESISC45.html)  
AID数据集下载链接（http://www.escience.cn/people/gongcheng/AID.html）  
EuroSAT数据集下载链接（https://github.com/phelber/eurosat）  
PatternNet数据集下载链接（http://www.escience.cn/people/gongcheng/PatternNet.html）
在data下更新数据集路径。  
建议文件目录结构如下所示
```
image_classification_sota
├── lib
├── tools
├── experiment
├── data
│   ├── train
|   ├── val
```
### 2.2 例如复现NWPU-RESSISC45
```
#NWPU45
python -m tools.train --dataset NWPU45 --model tv_resnet18 --teacher-model tv_resnet34 --data-path data/NWPU45 --num-classes 45 --batch-size 32 --epochs 150 --lr 0.01 --opt adamw --weight-decay 0.05 --sched cosine --warmup-epochs 5 --warmup-lr 0.001 --min-lr 0.00001 --smoothing 0.1 --kd diffkd --ori-loss-weight 0.5 --kd-loss-weight 0.5 --teacher-finetune --teacher-finetune-threshold 50.0 --teacher-finetune-epochs 20 --teacher-finetune-lr 0.001 --teacher-finetune-clip-grad 1.0 --teacher-freeze-layers 3 --teacher-finetune-classifier-only --experiment diffkd_res34_res18_nwpu45_finetuned_v2
```
### 2.3 例如添加噪声
```
##添加LEVEL0.7噪声
##AID_dataset30
python -m tools.train --dataset AID_dataset30 --model tv_resnet18 --teacher-model tv_resnet34 --data-path data/AID_dataset30 --num-classes 30 --batch-size 16 --epochs 150 --lr 0.01 --opt adamw --weight-decay 0.05 --sched cosine --warmup-epochs 5 --warmup-lr 0.001 --min-lr 0.00001 --smoothing 0.1 --kd diffkd --ori-loss-weight 0.5 --kd-loss-weight 0.5 --teacher-finetune --teacher-finetune-threshold 50.0 --teacher-finetune-epochs 20 --teacher-finetune-lr 0.001 --teacher-finetune-clip-grad 1.0 --teacher-freeze-layers 3 --teacher-finetune-classifier-only --rs-noise-types mixed --rs-noise-level 0.7 --val-rs-noise-types mixed --val-rs-noise-level 0.7 --experiment diffkd_aid_rs_mixed_noise_0.7
```
# 许可
本项目基于 [Apache License 2.0](https://www.apache.org/licenses/LICENSE-2.0) 开源。完整条款请参阅项目根目录下的 [LICENSE](./LICENSE) 文件
# 引用
如果您的工作受益于本项目的代码或思想，请引用我们的论文。同时，本项目基于Huang等人(2023)的DiffKD框架，也请引用其原始论文。
原始论文（https://arxiv.org/pdf/2305.15712)
原始论文代码（https://github.com/hunto/DiffKD）
### 
