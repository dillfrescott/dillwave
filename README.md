# DillWave

DillWave is a fast, high-quality neural vocoder and waveform synthesizer. It starts with Gaussian noise and converts it into speech via iterative refinement. The speech can be controlled by providing a conditioning signal (e.g. log-scaled Mel spectrogram). The model and architecture details are described in [DiffWave: A Versatile Diffusion Model for Audio Synthesis](https://arxiv.org/pdf/2009.09761.pdf).

Credit to the original repo [here](https://github.com/lmnt-com/diffwave).

## Recommended Requirements

An Nvidia GPU that is somewhere in the RTX 30XX-40XX range.

For training it's recommended to have 16+ GB of VRAM. For inference its recommended to have at least 4 GB of VRAM.

## Install

First install [Pytorch](https://pytorch.org), GPU version recommended! Also you need [Python](https://www.python.org) of course! Version 3.10.X is recommended for dillwave.

As a package:
```bash
pip install dillwave
```

From GitHub:
```bash
git clone https://github.com/dillfrescott/dillwave
pip install -e dillwave
```
or
```bash
pip install git+https://github.com/dillfrescott/dillwave
```
You need [Git](https://git-scm.com) installed for either of these "From GitHub" install methods to work.

### Training

```bash
python -m dillwave.preprocess /path/to/dir/containing/wavs # 48000hz, 1 channel, (8 seconds length recommended for each clip)
python -m dillwave /path/to/model/dir /path/to/dir/containing/wavs

# in another shell to monitor training progress:
tensorboard --logdir /path/to/model/dir --bind_all
```

### Inference CLI
```bash
python -m dillwave.inference /path/to/model --spectrogram_path /path/to/spectrogram -o output.wav [--fast]
```

Pretrained models are going to be released [here](https://github.com/dillfrescott/dillwave-model).
