# Chapter 16: Robot Learning in Simulation (Project 4) (edited for New PyRep (4.1.0.3))
## Description:
Example of Sawyer robot learning to reach the target with paralleled Soft Actor-Critic (SAC) algorithm, using PyRep for Sawyer robot simulation and game building. The environment is wrapped into OpenAI Gym format.
<p align="center">
<img src="https://github.com/deep-reinforcement-learning-book/Chapter16-Robot-Learning-in-Simulation/blob/master/figures/reacher.gif" width="40%">
</p>

## Dependencies and Installation:
### Install CoppeliaSim 
```bash
# Install CoppeliaSim 4.1.0 for Ubuntu 20.04
# Refer to PyRep README for other versions
export COPPELIASIM_ROOT=${HOME}/.local/bin/CoppeliaSim
curl -O https://www.coppeliarobotics.com/files/CoppeliaSim_Edu_V4_1_0_Ubuntu20_04.tar.xz
mkdir -p $COPPELIASIM_ROOT && tar -xf CoppeliaSim_Edu_V4_1_0_Ubuntu20_04.tar.xz -C $COPPELIASIM_ROOT --strip-components 1
## Add environment variables into bashrc (or zshrc)
echo "export COPPELIASIM_ROOT=$COPPELIASIM_ROOT
export LD_LIBRARY_PATH=\$LD_LIBRARY_PATH:\$COPPELIASIM_ROOT
export QT_QPA_PLATFORM_PLUGIN_PATH=\$COPPELIASIM_ROOT" >> ~/.bashrc
```
### Install PyRep
```bash
# Install PyRep
git clone https://github.com/stepjam/PyRep.git .local/PyRep
cd .local/PyRep
pip install -r requirements.txt
pip install .
cd ../..
```
* PyTorch

## Contents:
* `arms/`: object models of arms;
* `hands/`: object models of grippers;
* `objects/`: models of other objects in the scene;
* `scenes/`: built scenes for Sawyer robot grasping;
* `figures/`: figures for displaying;
* `model/`: the model after training, and two pre-trained models with different reward functions;
* `data/`: reward logs of with different reward functions;
* `sawyer_grasp_env_boundingbox.py`: script of Sawyer robot grasping environment;
* `sac_learn.py`: pralleled Soft Actor-Critic algorithm for solving Sawyer robot grasping task;
* `reward_log.npy`: log of episode reward during training;
* `plot.ipynb`: displaying the learning curves.


## Usage:
0. First check the environment can run successfully:

    `$ python sawyer_grasp_env_boundingbox.py`

    If it works properly with VRep called to run a scene, with Sawyer robot arm moving randomly, then go to next step; otherwise check the dependencies for necessary packages and versions.
1. Run `$ python sac_learn.py --train` for training the policy

2. Run `$ python sac_learn.py --test` for testing the trained policy, remember to change the `trained_model_path`, which is default to be the trained model we provided.

3. The training process will provide a `reward_log.npy` file for recording the reward value during training, which can be displayed with `$ jupyter notebook` in a new terminal, choose `plot.ipynb`and Shift+Enter to run the first cell, shown as follows:
<p align="center">
<img src="https://github.com/deep-reinforcement-learning-book/Chapter16-Robot-Learning-in-Simulation/blob/master/figures/training.png" width="80%">
</p>

## Authors:
[Zihan Ding](https://github.com/quantumiracle), [Yanhua Huang](https://github.com/Officium)


## Citing:

```
@misc{DeepReinforcementLearning-Chapter16-RobotLearninginSimulation,
  author = {Zihan Ding, Yanhua Huang},
  title = {Chapter16-RobotLearninginSimulation},
  year = {2019},
  publisher = {GitHub},
  journal = {GitHub repository},
  howpublished = {\url{https://github.com/deep-reinforcement-learning-book/Chapter16-Robot-Learning-in-Simulation}},
}
```

or

```
@book{deepRL-2020,
 title={Deep Reinforcement Learning: Fundamentals, Research, and Applications},
 editor={Hao Dong, Zihan Ding, Shanghang Zhang},
 author={Hao Dong, Zihan Ding, Shanghang Zhang, Hang Yuan, Hongming Zhang, Jingqing Zhang, Yanhua Huang, Tianyang Yu, Huaqing Zhang, Ruitong Huang},
 publisher={Springer Nature},
 note={\url{http://www.deepreinforcementlearningbook.org}},
 year={2020}
}
```

