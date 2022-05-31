# GANimator: Neural Motion Synthesis from a Single Sequence

![Python](https://img.shields.io/badge/Python->=3.8-Blue?logo=python)  ![Pytorch](https://img.shields.io/badge/PyTorch->=1.10.0-Red?logo=pytorch)

This repository provides a library for novel motion synthesis from a single example, as well as applications including style transfer, motion mixing, key-frame editing and conditional generation. It is based on our work [GANimator: Neural Motion Synthesis from a Single Sequence](https://peizhuoli.github.io/ganimator/index.html) that is published in SIGGRAPH 2022.

<img src="https://peizhuoli.github.io/ganimator/images/video_teaser_small.gif" slign="center">

The library is still under development.


## Prerequisites Update by Grace, 2022.05.31

1. Please visit Anaconda web site and install conda first: https://www.anaconda.com/
<img width="624" alt="image" src="https://user-images.githubusercontent.com/89304181/171111097-e34a1497-25d3-42d8-b686-ea1469b252b1.png">


2. cd ~/ganimator
3. Run the following code directly. This code has been tested under Ubuntu 20.04. Before starting, please configure your Anaconda environment by
~~~bash
conda env create -f environment.yaml
conda activate ganimator
~~~
<img width="523" alt="image" src="https://user-images.githubusercontent.com/89304181/171111421-2652dfee-e8c3-482b-a5ce-991a4e543233.png">



Or you may install the following packages (and their dependencies) manually:

- pytorch 1.10
- tensorboard
- tqdm
- scipy

## Quick Start

We provide several pretrained models for various characters. Download and extract the pretrained model from [Google Drive](https://drive.google.com/file/d/1jFevozHEuSL2R0MP_ZVBqIAa4jFM0VRh/view?usp=sharing).

### Novel motion synthesis

Run `demo.sh`. The result for Salsa and Crab Dace will be saved in `./results/pre-trained/{name}/bvh`. The result after foot contact fix will be saved as `result_fixed.bvh`

### Applications and Evaluation

Under development.

## Train from scratch

We provide instructions for retraining our model.

We include several animations under `./data` directory.

Here is an example for training the crab dance animation:

~~~bash
python train.py --bvh_prefix=./data/Crabnew --bvh_name=Crab-dance-long --save_path={save_path}
~~~

You may specify training device by `--device=cuda:0` using pytorch's device convention.


For customized bvh file, specify the joint names that should be involved during the generation and the contact name in `./bvh/skeleton_databse.py`, and set corresponding `bvh_prefix` and `bvh_name` parameter for `train.py`.


## Acknowledgements

The code in `models/skeleton.py` is adapted from [deep-motion-editing](https://github.com/DeepMotionEditing/deep-motion-editing) by [@kfiraberman](https://github.com/kfiraberman), [@PeizhuoLi](https://github.com/PeizhuoLi) and [@HalfSummer11](https://github.com/HalfSummer11).

Part of the code in `bvh` is adapted from the [work](https://theorangeduck.com/media/uploads/other_stuff/motionsynth_code.zip) of [Daniel Holden](https://theorangeduck.com/page/publications).

Part of the training examples is taken from [Mixamo](http://mixamo.com) and [Truebones](https://truebones.gumroad.com).


## Citation

If you use this code for your research, please cite our paper:

~~~bibtex
@article{li2022ganimator,
  author = {Li, Peizhuo and Aberman, Kfir and Zhang, Zihan and Hanocka, Rana and Sorkine-Hornung, Olga },
  title = {GANimator: Neural Motion Synthesis from a Single Sequence},
  journal = {ACM Transactions on Graphics (TOG)},
  volume = {41},
  number = {4},
  pages = {138},
  year = {2022},
  publisher = {ACM}
}
~~~
