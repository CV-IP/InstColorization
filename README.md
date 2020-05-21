# Instance-aware Image Colorization
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/ericsujw/InstColorization/blob/master/InstColorization.ipynb)

This is the pytorch demo code of our CVPR 2020 paper. (Arxiv, [Project](https://ericsujw.github.io/InstColorization/))

By this repo you can predict a color image from a single grayscale image. To see more details please refer to the paper or project page.

<img src='imgs/teaser.png' width=600>

## Prerequisites
* Python3
* Pytorch >= 1.5
* Detectron2
* OpenCV-Python
* Pillow/scikit-image
* Please refer to the [env.yml](env.yml) for detail dependencies.

## Getting Started
1. Clone this repo:
```sh
git clone https://github.com/ericsujw/InstColorization
cd InstColorization
```
2. Install [conda](https://www.anaconda.com/).
3. Install all the dependencies
```sh
conda env create --file env.yml --name instacolorization
```
4. Switch to the conda environment
```sh
conda activate instacolorization
```

## Pretrained Model
1. Download it from [google drive](https://drive.google.com/open?id=1Xb-DKAA9ibCVLqm8teKd1MWk6imjwTBh).
```sh
sh scripts/download_model.sh
```
2. Now the pretrained models would place in [checkpoints](checkpoints).

## Instance Prediction
Please follow the command below to predict all the bounding boxes fo the images in `example` folder.
```
python inference_bbox.py --test_img_dir example
```
All the prediction results would save in `example_bbox` folder.

## Colorize Images
Please follow the command below to colorize all the images in `example` foler.
```
python test_fusion.py --name test_fusion --sample_p 1.0 --model fusion --fineSize 256 --test_img_dir example --results_img_dir results
```
All the colorized results would save in `results` folder.

* Note: all the images would convert into L channel to colorize in [test_fusion.py's L51](test_fusion.py#L51)

## Citation
If you use this code for your research, please cite our paper:
```
@article{
    ...
}
```

## Acknowledgments
This code borrows heavily from the [colorization-pytorch](https://github.com/richzhang/colorization-pytorch) repository.