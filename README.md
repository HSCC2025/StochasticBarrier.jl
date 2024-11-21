# StochasticBarrier.jl

We present *StochasticBarrier.jl*, an open-source Julia-based toolbox for generating Stochastic Barrier Functions (SBFs) for safety verification of discrete-time stochastic systems with additive Gaussian noise. The tool supports linear, polynomial, and piecewise affine (PWA) uncertain dynamics. The toolbox implements a Sum-of-Squares (SOS) optimization approach, as well as  methods based on piecewise constant (PWC) functions. For the class of of PWC-SBFs, three engines are offered based on: (1) DUAL Linear Programming, (2) Counter Example Guided (CEGS) Linear Programming, and (3) Projected Gradient Descent (GD).

## Repeat Experiments
| **`Linux`** | **`Mac OS X`** | **`Windows`** |
|-----------------|---------------------|-------------------------|

Read the description below for repeatability of all the experiments.

### Docker Image
The Dockerfile is provided in the main folder. Build this docker file to obtain all the required Julia packages, as specified in the Project.toml. To build the docker image, navigate into the main folder and run the following command 
```sh
sudo docker build -t stochasticbarrier .
```

To start a container 

```sh
sudo docker run -it --name StochasticBarrier stochasticbarrier
```

## Run through bash

Use the following commands to run the optimization case studies through bash.

```sh
stochasticbarrier contraction_sos      # To run the stochastic contraction map with a SOS barrier
stochasticbarrier contraction_pwc      # To run the stochastic contraction map with a PWC barrier
```

The same commands can be run for other benchmarks: population, oscillator, roomtemperature, or pendulum.

## Run through Julia
Use the following commands to run the optimization case studies through Julia

Navigate to *```/StochasticBarrierFunctions```* \
In terminal call julia and run the following commands:
1. ```julia
      using Pkg
   ```
2. ```julia 
      Pkg.activate(".") 
   ```
3. ```julia 
      Pkg.precompile(".") 
   ```   

To run the Contraction Map for example, use the following command: 
```julia 
   yaml_file = "benchmarks/linear/systems/contraction/sos.yaml"; include("benchmarks/barrier_synthesis.jl")
```
The same commands can be run for other benchmarks: oscillator, roomtemperature, or pendulum.
