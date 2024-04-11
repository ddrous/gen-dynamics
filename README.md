# Gen Dynamics
A collection of datasets for learning generalisable dynamical systems

Learning dynamical systems that can generalize to various parameter changes in their underlying ODEs or PDEs is a significant but challenging task. In recent years, several methods have been proposed to learn such systems. This repository contains a collection of datasets that can be used to benchmark these methods.

We aim to provide a consistent interface to access each dataset. The datasets are made up of 4 splits each: 
1) `train`: For In-Domain meta-learning
2) `test`: For In-Domain meta-testing
2) `ood_train`: For Out-of-Distribution adaptation to new environments
3) `ood_test`: For Out-of-Distribution testing of the adaptation to new environments

Each split is a NumPy archive (.npz) containing the trajectory of the system (`X`) and the time points (`t`) at which they were evaluated. While `t` is a 1-dimensional array, `X` is a 4-dimensional tensor of shape `(nb_envs, nb_trajs_per_env, nb_steps_per_traj, state_size)` described as follows:
1) `nb_envs`: Number of distinct environments
2) `nb_trajs_per_env`: Number of trajectories per environment
3) `nb_steps_per_traj`: Number of time steps per trajectory (matching the size of `t`)
4) `state_size`: Size of the state space


## Methods
The following methods use at least in part the datasets provided in this repository:
- LEADS: https://arxiv.org/abs/2106.04546
- CoDA: https://arxiv.org/pdf/2202.01889.pdf
- NCF: Coming soon...
- FOCA: https://openreview.net/forum?id=AW0i0lOhzqJ
- Etc. (If you have a method that you would like to add, please open an issue, a pull request, or get in touch directly :) )


## Current Datasets
- Lotka-Volterra (see CoDA, LEADS)
- Glycolytic Oscillator (see CoDA, LEADS)
- Gray-Scott: Since this is a PDE on a 2D grid, its spatial data is flattened to a 1D state vector (see CoDA, LEADS, NCF)
- Selkov-Model (see NCF)
- Please feel free to add more datasets by opening a pull request.


## More Datasets to Add
The following datasets are currently being prepared for addition to this repository:
- https://arxiv.org/abs/2312.00477
- https://arxiv.org/abs/2303.03181
- https://arxiv.org/abs/2303.15827
