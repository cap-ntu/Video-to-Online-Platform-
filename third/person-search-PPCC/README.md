# Person Search by Progressive Propagation via Competitive Consensus (PPCC)
This is the implement of our [ECCV 2018](https://eccv2018.org/) paper

***Person Search in Videos with One Portrait Through Visual and Temporal Links***.  
Qingqiu Huang, Wentao Liu, Dahua Lin.  ECCV 2018, Munich.

This project is based on our person search dataset -- ***Cast Search in Movies (CSM)*** .
More details about this dataset can be found in our [project page](http://qqhuang.cn/projects/eccv18-person-search/).

## Basic Usage

1. Download the affinity matrices and meta data of CSM from [Google Drive](https://drive.google.com/drive/folders/1u51eRnZS1rQaM7GStPTQKB0BugpnGM9W?usp=sharing) or [Baidu Wangpan](https://pan.baidu.com/s/1JG30kPTWxJmf1saA0e6CLQ)
2. Put affnity matrix in "\*\*/data/affinity" and meta data in "\*\*/data/meta".
Here "**" means the path that you clone this project to.
3. Run "matching.py" for visual matching and "propagation.py" for lable propagation. Example:  
`python propagation.py --exp in --gpu_id -1 --temporal_link`

## More Details

* The downloaded affinity matrices are calculate by the consin simmilarity of the visual features bewteen the instances.
More specific, we use face features for cast-tracklet links and body features for tracklet-tracklet links.
The face model is a Resnet-101 trained on MS-Celeb-1M.
The body model is a Resnet-50 pretrianed on ImageNet and finetune on the training set of CSM.
You can also train your own model on CSM.

* We implement both CPU and GPU version of PPCC,
you can choose any one of them by setting the paprameter "gpu_id" (-1 for CPU and others for a specific GPU).
The GPU code is based on [PyTorch](https://pytorch.org/).
You are recommand to use GPU version since it is much faster, especially for the "ACROSS" experiment settting.

## Citation
```
@inproceedings{huang2018person,
    title={Person Search in Videos with One Portrait Through Visual and Temporal Links},
    author={Huang, Qingqiu and Liu, Wentao and Lin, Dahua},
    booktitle={Proceedings of the European Conference on Computer Vision (ECCV)},
    pages={425--441},
    year={2018}
}
```
