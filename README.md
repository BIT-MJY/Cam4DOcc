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
### Data Structure

Please link your [nuScenes dataset](https://www.nuscenes.org/nuscenes#download) to the data folder. [nuscenes_occ_infos_train.pkl](https://github.com/JeffWang987/OpenOccupancy/releases/tag/train_pkl) and [nuscenes_occ_infos_val.pkl](https://github.com/JeffWang987/OpenOccupancy/releases/tag/val_pkl) are also provided by the previous work.

```bash
Cam4DOcc
├── data/
│   ├── nuscenes/
│   │   ├── maps/
│   │   ├── samples/
│   │   ├── sweeps/
│   │   ├── lidarseg/
│   │   ├── v1.0-test/
│   │   ├── v1.0-trainval/
│   │   ├── nuscenes_occ_infos_train.pkl/
│   │   ├── nuscenes_occ_infos_val.pkl/
```




