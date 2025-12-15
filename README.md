# DiffKD_experiment_2025
论文《Adapting Diffusion-Based Knowledge Distillation for Robust Remote Sensing Scene Classification》代码复现
## Part 1 环境安装
### 1.1 克隆本仓库
```bash
git clone https://github.com/maomaoxy/DiffKD_experiment_2025.git
cd DiffKD_experiment_2025
### 1.2 创建并激活Python环境
## Part 2 重现我们的研究结果
以下步骤展示了如何在AID数据集上使用ResNet-34教师模型和ResNet-18学生模型运行DiffKD
### 2.1 数据准备
请从官方来源下载遥感场景分类数据集（NWPU-RESISC45, AID, EuroSAT, PatternNet）
在 configs/datasets/ 下的配置文件中更新数据集路径。
代码包括复现四种噪声等级下/八种变体下四种数据集的精度
### 2.2 训练教师模型 
### 2.3 使用DiffKD训练学生模型
# 许可
本项目本项目基于[Apache License 2.0]开源
# 引用
如果您的工作受益于本项目的代码或思想，请引用我们的论文。同时，本项目基于 Huang 等人 (2023) 的 DiffKD 框架，也请引用其原始论文。

**引用本项目：**
```bibtex
@article{li2025diffkd,
  title={DiffKD: Diffusion-Based Knowledge Distillation for Robust Remote Sensing Scene Classification},
  author={Li, Nan and Chu, Xinyu and Li, Xiang and Li, Longwei},
  journal={arXiv preprint arXiv:xxxx.xxxxx},
  year={2025}
}
