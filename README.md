# Planning Using Schrödinger Bridge Diffusion Models &nbsp;&nbsp;

This repo contains the code for the experiments performed as part of the work [Planning Using Schrödinger Bridge Diffusion Models](https://arxiv.org/abs/2406.12458), This repo was originally forked from [the Diffuser codebase](https://github.com/jannerm/diffuser).

The experiments are based on the Maze2D environment of the [D4RL benchmark](https://github.com/Farama-Foundation/D4RL).

## Installation

```
conda env create -f environment.yml
conda activate diffusion
pip install -e .
```

## Usage

Train a diffusion model with:
```
python scripts/train.py --config config.maze2d --dataset maze2d-large-v1
```

The default hyperparameters are listed in [`config/maze2d.py`](config/maze2d.py).
You can override any of them with runtime flags, eg `--batch_size 64`.

Plan using the diffusion model with:
```
python scripts/plan_maze2d.py --config config.maze2d --dataset maze2d-large-v1
```


## Docker

1. Build the container:
```
docker build -f azure/Dockerfile . -t diffuser
```

2. Test the container:
```
docker run -it --rm --gpus all \
    --mount type=bind,source=$PWD,target=/home/code \
    --mount type=bind,source=$HOME/.d4rl,target=/root/.d4rl \
    diffuser \
    bash -c \
    "export PYTHONPATH=$PYTHONPATH:/home/code && \
    python /home/code/scripts/train.py --dataset hopper-medium-expert-v2 --logbase logs/docker"
```




## Reference
```
@misc{srivastava2024planningusingschrodingerbridge,
      title={Planning Using Schr\"odinger Bridge Diffusion Models}, 
      author={Adarsh Srivastava},
      year={2024},
      eprint={2406.12458},
      archivePrefix={arXiv},
      primaryClass={cs.RO},
      url={https://arxiv.org/abs/2406.12458}, 
}
```
