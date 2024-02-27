# Cam4DOcc

The official code an data for the benchmark with baselines for our paper: [Cam4DOcc: Benchmark for Camera-Only 4D Occupancy Forecasting in Autonomous Driving Applications](https://arxiv.org/abs/2311.17663)

[Junyi Ma#](https://github.com/BIT-MJY), [Xieyuanli Chen#](https://github.com/Chen-Xieyuanli), Jiawei Huang, [Jingyi Xu](https://github.com/BIT-XJY), [Zhen Luo](https://github.com/Blurryface0814), Jintao Xu, Weihao Gu, Rui Ai, [Hesheng Wang*](https://scholar.google.com/citations?hl=en&user=q6AY9XsAAAAJ)

## Publication

If you use the code or the Haomo dataset in your academic work, please cite our paper ([PDF](https://arxiv.org/pdf/2203.03397.pdf)):

```
@article{ma2023cam4docc,
  title={Cam4DOcc: Benchmark for Camera-Only 4D Occupancy Forecasting in Autonomous Driving Applications},
  author={Ma, Junyi and Chen, Xieyuanli and Huang, Jiawei and Xu, Jingyi and Luo, Zhen and Xu, Jintao and Gu, Weihao and Ai, Rui and Wang, Hesheng},
  journal={arXiv preprint arXiv:2311.17663},
  year={2023}
}
```

## Installation

We follow the installation instructions of our codebase [OpenOccupancy](https://github.com/JeffWang987/OpenOccupancy/blob/main/docs/install.md), which are also posted here:

* Create a conda virtual environment and activate it
```
conda create -n OpenOccupancy python=3.7 -y
conda activate OpenOccupancy
```
* Install PyTorch and torchvision (tested on torch==1.10.1 & cuda=11.3)
```
conda install pytorch==1.10.1 torchvision==0.11.2 torchaudio==0.10.1 cudatoolkit=11.3 -c pytorch -c conda-forge
```
* Install gcc>=5 in conda env
```
conda install -c omgarcia gcc-6
```
* Install mmcv, mmdet, and mmseg
```
pip install mmcv-full==1.4.0
pip install mmdet==2.14.0
pip install mmsegmentation==0.14.1
```
* Install mmdet3d from the source code
```
git clone https://github.com/open-mmlab/mmdetection3d.git
cd mmdetection3d
git checkout v0.17.1 # Other versions may not be compatible.
python setup.py install
```
* Install other dependencies
```
pip install timm
pip install open3d-python
pip install PyMCubes
pip install spconv-cu113
pip install fvcore
pip install setuptools==59.5.0
```
* Install occupancy pooling
```
git clone git@github.com:haomo-ai/Cam4DOcc.git
cd Cam4DOcc
export PYTHONPATH=“.”
python setup.py develop
```








### Code Structure

```bash
├── config
│   ├── config_haomo.yml
│   └── config.yml
├── modules
│   ├── loss.py
│   ├── netvlad.py
│   ├── overlap_transformer_haomo.py
│   └── overlap_transformer.py
├── test
│   ├── test_haomo_topn_prepare.py
│   ├── test_haomo_topn.py
│   ├── test_kitti00_prepare.py
│   ├── test_kitti00_PR.py
│   ├── test_kitti00_topN.py
│   ├── test_results_haomo
│   │   └── predicted_des_L2_dis_bet_traj_forward.npz (to be generated)
│   └── test_results_kitti
│       └── predicted_des_L2_dis.npz (to be generated)
├── tools
│   ├── read_all_sets.py
│   ├── read_samples_haomo.py
│   ├── read_samples.py
│   └── utils
│       ├── gen_depth_data.py
│       ├── split_train_val.py
│       └── utils.py
├── train
│   ├── training_overlap_transformer_haomo.py
│   └── training_overlap_transformer_kitti.py
├── valid
│   └── valid_seq.py
├── visualize
│   ├── des_list.npy
│   └── viz_haomo.py
└── weights
    ├── pretrained_overlap_transformer_haomo.pth.tar
    └── pretrained_overlap_transformer.pth.tar
```
