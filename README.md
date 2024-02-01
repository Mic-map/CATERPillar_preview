# CATERPillar: Computational Axonal Threading Engine for Realistic Proliferation

![CATERPillar Logo](https://github.com/jazz031195/CATERPillar/blob/updated/caterpillar.jpg)

## Introduction
CATERPillar is a tool that generates white matter numerical phantoms by mimicking natural fiber growth. The axons proliferate in parallel towards their target while avoiding collisions with the environment (already existing axons). The phantoms can be used to create synthetic diffusion MRI data with varying parameters.

## Table of Contents
- [Introduction](#introduction)
- [Getting Started](#getting-started)
  - [Installation](#installation)
    - [MacOS](#macos)
    - [Linux](#linux)
  - [Running the Program](#running-the-program)
    - [MacOS](#macos-1)
    - [Linux](#linux-1)
- [Parameters](#parameters)
- [Outputs of Program](#outputs-of-program)
- [Contributors](#contributors)
- [License](#license)

## Getting Started
### Running the Program

#### Linux
To install the dependencies on Linux, follow these steps:
1. Download the executable file and the args.conf file on your local machine.
2. Open a terminal.
3. Go to the path that leads to the executable file on your local machine using "cd":
4. Adapt the `args.conf` file to your preference. The parameters are explained below.
6. Run the following command to compile and run the program:
   ```shell
   chmod u+x src/Growth-Animation.exe
   ./src/Growth-Animation.exe "path/to/folder/args.conf"
   ```
   
## Parameters
The parameters that can be modified are listed in the `args.conf` file. Some parameters may have multiple values (written as `<parameter>`) over which the program will iterate. The modified parameter values will appear in the name of the output files.

Here are the parameters that can be modified:
- `data_directory` (string): Path to the folder on your local computer.
- Parameters for Gamma Distribution for axon radii:
  - `alpha` (double): Alpha parameter for a Gamma Distribution. The radii of the axons are taken from this distribution.
  - `beta` (double): Beta parameter for a Gamma Distribution. The radii of the axons are taken from this distribution.
  - `min_radius` (double): Minimum radius of the axons.
- Parameters for axon morphology:
  - `tortuous` (0 or 1): If set to 1, the axons will be tortuous; otherwise, they will grow straight.
  - `beading_variation` (double between 0 and 1): The radius of each axon will vary periodically between the original radius and radius/beading_variation. If set to 1, there will be no beading.
  - `beading_frequency` (double): Frequency of axonal beading (= 1/nbr of spheres)
- Other Parameters :
  - `vox_sizes` (list of int): The maximum distance (in micrometers) in space to define the corner of the 3D box to work in.
  - `draw` (0 or 1): If set to 1, the voxel will be drawn with all the growing axons. If so, no output with the axons' information will be created. Because the code isn't yet public, draw is set to 1 regardless of your input.
  - `regrow_thr` (int): If the amount of regrowing attempts during which no new axons are made is above the chosen threshold, the growth process stops.
  - `spheres_overlap_factors` (list of int, must be above 2): The distance between spheres in each axon is the radius/spheres_overlap_factor.
  - `icvf` (double between 0 and 1): Intra Compartment Volume Fraction.
  - `capacities` (list of int, must be below the number of processors available on the computer): Number of parallel threads to grow axons simultaneously.
  - `repetitions` (int, must be 1 or above): Number of repetitions to run growth.
  - `std_dev` (double): Standard deviation of the Gaussian distribution for growth.

## Contributors
- Jasmine Nguyen-Duc
- Melina Cherchali
- Ines deRiedmatten

