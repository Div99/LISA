
# LISA

Divyansh Garg\*, Skanda Vaidyanath\*, Kuno Kim, Jiaming Song, Stefano Ermon

\*equal contribution

A link to our paper can be found on [arXiv](https://arxiv.org/abs/2203.00054).

## Overview

Official codebase for [LISA: Learning Interpretable Skill Abstractions from language](https://div99.github.io/LISA/).
Contains scripts to reproduce experiments.

<!-- ![image info](./architecture.png) -->

## Instructions

Our code for running LISA experiments is present in `hrl` folder.

To run the code us the following command:

`python main.py model=traj_option batch_size=128 option_selector.use_vq=True seed=69 train_dataset.num_trajectories=1000 model.horizon=10 model.K=10 option_selector.num_options=10 env=babyai/GoToSeq warmup_steps=2500 max_iters=2500 trainer.eval_every=100 option_selector.commitment_weight=20 option_selector.kmeans_init=True save_interval=100 os_learning_rate=1e-5`

This is a sample command intended to show the usage of different flags available.
For example, `model=traj_option` runs LISA and `model=vanilla` runs a flat language conditioned Decision Transformer.
You can also change the environment by setting `env=babyai/BossLevel` or `env=lorel_sawyer_obs` or `env=lorel_sawyer_state`, etc.
There are several other configuration options available in the folder `hrl/conf` that allows you to remove vector quantization, change the number of skill codes and dimension of skill codes, change the horizon, change the commitment weight, etc. The configurations are specified with YAML files and we use [hydra](https://hydra.cc/).
Here is a sample command for the LORL dataset with some different falgs set:
`main.py env=lorel_sawyer_obs method=traj_option dt.n_layer=1 dt.n_head=4 option_selector.option_transformer.n_layer=1 option_selector.option_transformer.n_head=4 option_selector.option_transformer.hidden_size=128 batch_size=256 seed=1 warmup_steps=5000`
The hyperparameters needed to reproduce the experiments are in [Appendix D of the paper](https://arxiv.org/pdf/2203.00054.pdf).
<!-- See corresponding READMEs in each folder for instructions; scripts should be run from the respective directories.
It may be necessary to add the respective directories to your PYTHONPATH. -->

## License

The code is made available for academic, non-commercial usage. Please see the LICENSE for the licensing terms of LISA for commercial use and running it on your robots/creating new AI agents.

For any inquiry, contact: Div Garg (divgarg@stanford.edu), Skanda Vaidyanath (svaidyan@stanford.edu)
