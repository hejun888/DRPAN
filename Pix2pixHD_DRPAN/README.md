# Pix2pixHD+DRPAN in PyTorch

This is the PyTorch implementation of our Pix2pixHD+DRPAN on image-to-image translation.

## Prerequisites
- Linux or macOS.
- Python 2 or Python 3.
- CPU or NVIDIA GPU + CUDA CuDNN.

## Getting Started
### Installation
- Install PyTorch and dependencies from http://pytorch.org/.
- Install python library [dominate](https://github.com/Knio/dominate):
```bash
pip install dominate
```

- Clone this repo:
```bash
git clone https://github.com/godisboy/DRPAN.git
cd DRPAN/Pix2pixHD_DRPAN
```

- Modify the config file:
change the `dataPath` to your data set path.

### Pix2pixHD+DRPAN train/test
- Prepare your paired image2image translation dataset. 

We use the Cityscapes dataset. To train a model on the full dataset, please download it from the [official website](https://www.cityscapes-dataset.com/) (registration required).
- Train the model:
```
python main.py --config configs/cityscapes.yaml --cuda --gpu_ids 0
```
The train results and trained model will be saved to `checkpoints`, you can set the `outf` in config file to change it.
- Test the model:
```
python test.py --config configs/cityscapes.yaml --modeldir checkpoints/generator_epoch_199.pkl --cuda --gpu_ids 0
```
If you want to test with the trained model of other epochs, please modify `--modeldir checkpoints/generator_epoch_other.pkl`. 
