# [Pattern Recognition] Decomposition Dynamic Graph Conolutional Recurrent Network for Traffic Forecasting  

This is a PyTorch implementation of Decomposition Dynamic Graph Conolutional Recurrent Network for Traffic Forecasting, as described in our paper: [Weng, Wenchao](https://github.com/wengwenchao123/DDGCRN/), Fan Jin ,Wu Huifeng and Hu Yujie ,Tian Hao, Zhu Fu, Wu Jia,  **[A Decomposition Dynamic Graph Convolutional Recurrent Network for Traffic Forecasting](https://www.sciencedirect.com/science/article/pii/S0031320323003710)**,Pattern Recognition 2023.

[![PWC](https://img.shields.io/endpoint.svg?url=https://paperswithcode.com/badge/a-decomposition-dynamic-graph-convolutional/traffic-prediction-on-pemsd3)](https://paperswithcode.com/sota/traffic-prediction-on-pemsd3?p=a-decomposition-dynamic-graph-convolutional)
[![PWC](https://img.shields.io/endpoint.svg?url=https://paperswithcode.com/badge/a-decomposition-dynamic-graph-convolutional/traffic-prediction-on-pemsd4)](https://paperswithcode.com/sota/traffic-prediction-on-pemsd4?p=a-decomposition-dynamic-graph-convolutional)
[![PWC](https://img.shields.io/endpoint.svg?url=https://paperswithcode.com/badge/a-decomposition-dynamic-graph-convolutional/traffic-prediction-on-pems07)](https://paperswithcode.com/sota/traffic-prediction-on-pems07?p=a-decomposition-dynamic-graph-convolutional)
[![PWC](https://img.shields.io/endpoint.svg?url=https://paperswithcode.com/badge/a-decomposition-dynamic-graph-convolutional/traffic-prediction-on-pems08)](https://paperswithcode.com/sota/traffic-prediction-on-pems08?p=a-decomposition-dynamic-graph-convolutional)
[![PWC](https://img.shields.io/endpoint.svg?url=https://paperswithcode.com/badge/a-decomposition-dynamic-graph-convolutional/traffic-prediction-on-pemsd7-m)](https://paperswithcode.com/sota/traffic-prediction-on-pemsd7-m?p=a-decomposition-dynamic-graph-convolutional)
[![PWC](https://img.shields.io/endpoint.svg?url=https://paperswithcode.com/badge/a-decomposition-dynamic-graph-convolutional/traffic-prediction-on-pemsd7-l)](https://paperswithcode.com/sota/traffic-prediction-on-pemsd7-l?p=a-decomposition-dynamic-graph-convolutional)
## Update (2024/1/29)

* Optimized the data processing part of the model by changing the normalization process from using the mean and variance of the entire dataset to using the mean and variance of the training set.

* Improved the normalization operation when reading data, no longer normalizing the prediction target to avoid the abnormal MAPE issue on the PEMS03 dataset.

* Enhanced the dataset splitting operation, changing from initially dividing the dataset and then segmenting samples to first segmenting samples and then dividing the dataset. This has increased the number of training and testing samples.


## Table of Contents

* configs: training Configs and model configs for each dataset

* lib: contains self-defined modules for our work, such as data loading, data pre-process, normalization, and evaluate metrics.

* model: implementation of our model 

* pre-trained:  pre-trained model parameters


# Data Preparation

For convenience, we package these datasets used in our model in [Google Drive](https://drive.google.com/drive/folders/1OQYVddI5icsHwSVWtRHbqJ-xG7242q1r?usp=share_link).

Unzip the downloaded dataset files to the main file directory, the same directory as run.py.

# Requirements

Python 3.6.5, Pytorch 1.9.0, Numpy 1.16.3, argparse and configparser

# Model Training

```bash
python run.py --datasets {DATASET_NAME} --mode {MODE_NAME}
```
Replace `{DATASET_NAME}` with one of `PEMSD3`, `PEMSD4`, `PEMSD7`, `PEMSD8`, `PEMSD7(L)`, `PEMSD7(M)`

such as `python run.py --datasets PEMSD4`

There are two options for `{MODE_NAME}` : `train` and `test`

Selecting `train` will retrain the model and save the trained model parameters and records in the `experiment` folder.

With `test` selected, run.py will import the trained model parameters from `{DATASET_NAME}.pth` in the 'pre-trained' folder.

## Cite

If you find the paper useful, please cite as following:

```
@article{weng2023decomposition,
  title={A Decomposition Dynamic Graph Convolutional Recurrent Network for Traffic Forecasting},
  author={Weng, Wenchao and Fan, Jin and Wu, Huifeng and Hu, Yujie and Tian, Hao and Zhu, Fu and Wu, Jia},
  journal={Pattern Recognition},
  pages={109670},
  year={2023},
  publisher={Elsevier}
}
```

## More Related Works

- [[Neural Networks] RGDAN: A random graph diffusion attention network for traffic prediction](https://doi.org/10.1016/j.neunet.2023.106093)

