# Benchmarking the Attribution Quality of Vision Models

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![Framework](https://img.shields.io/badge/PyTorch-%23EE4C2C.svg?&logo=PyTorch&logoColor=white)](https://pytorch.org/)

[R. Hesse](https://robinhesse.github.io/), [S. Schaub-Meyer](https://schaubsi.github.io/), [J. Hesse](https://lir-mainz.de/mitarbeiter/janina-hesse), [B. Schiele](https://www.mpi-inf.mpg.de/departments/computer-vision-and-machine-learning/people/bernt-schiele), and [S. Roth](https://www.visinf.tu-darmstadt.de/visual_inference/people_vi/stefan_roth.en.jsp). **What is Missing? Explaining Neurons Activated by Absent Concepts**. _ICML_, 2026.

[ArXiv](https://arxiv.org/abs/2407.11910) | [Poster](https://github.com/visinf/what-is-missing/blob/main/poster.pdf)


## Environment

`conda env create -f environment.yml`
`conda activate what-is-missing`

## Reichardt detector experiment

```cd reichardt_detector```
and run
```python reichardt_detector.py```

The results will be stored in `/visualization`.

## Toy experiment

```cd toy_example```
and run
```python toy_example.py```

The results will be stored in `/visualization`.

## ImageNet experiment

```cd imagenet```

run, e.g.,
````
python image_quantitative.py --data_dir /fastdata/rhesse/datasets/imagenet --model resnet50 --model_layer model.layer4[2].conv3 --batch_size 256 --patch_size 48 --patch_stride 16 --nr_patches 8 --seed 0
```

## ISIC experiment

### Download the dataset 

```cd isic```

Set the DOWNLOAD_DIR and API_TOKEN in isic_download.py

run `python isic_download.py`

Disclaimer: the ISIC API changed over the course of the project, and I did not manage to recover exactly the same images. While the overall conclusions should remain the same, it is possible that the downloaded images do not exactly match the images used in the paper.

### Running the experiment

run `python train.py`

You can set:
The debiasing mode - `MODE = ['default', 'presence_debias', 'presence_absence_debias']`
The model - `MODEL = ['xresnet50', 'vit_b_16']`
and other parameters (remember to adjust the `STORE_DIR` for the different models)

