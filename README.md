# CATERPillar: Computational Axonal Threading Engine for Realistic Proliferation

![CATERPillar Logo](https://github.com/jazz031195/CATERPillar/blob/updated/caterpillar.jpg)

## Introduction
CATERPillar is a tool that generates white matter numerical phantoms by mimicking natural fiber growth. The axons proliferate in parallel towards their target while avoiding collisions with the environment (already existing axons). The phantoms can be used to create synthetic diffusion MRI data with varying parameters.

This preview enables the visualisation of this growth by using an executable file, easily run (with linux only :/). We hope to publish the entire code in C++ ASAP ! 

## Table of Contents
- [Introduction](#introduction)
- [Getting Started](#getting-started)
  - [Installation](#installation)
  - [Running the Program](#running-the-program)
- [Parameters](#parameters)
- [Outputs of Program](#outputs-of-program)
- [Contributors](#contributors)
  - [Authors and Affiliations](#authors-and-affiliations)
  - [Logo](#logo)
  - [Website](#website)

## Getting Started

### Installations
To run the program, you must first install the SFML (Simple and Fast Multimedia Library) library and the OpenGL Utility Toolkit (GLUT) library. This allows for the visualisation. For this, run the following command in your terminal : 
  ```shell
  sudo apt update
  sudo apt-get install libsfml-dev
  sudo apt-get install freeglut3-dev
  sudo apt-get install mesa-common-dev
  ```

### Running the Program

Follow these steps:
1. Download the executable file and the args.conf file on your local machine.
2. Open a terminal.
3. Go to the path that leads to the executable file on your local machine using "cd":
4. Adapt the `args.conf` file to your preference. The parameters are explained below. Modify "data_directory" to the path on your local computer.
6. Run the following command to compile and run the program:
   ```shell
   chmod u+x Growth-Animation.exe
   ./Growth-Animation.exe "path/to/folder/args.conf"
   ```
A video will then open and you will see axons growing in a substrate. You can stop the viseo at anytime with Ctrl+C. An example of such a video is given.
   
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
  - `std_dev` (double): Standard deviation of the Gaussian distribution for growth. The higher this value, the more tortuous the axons ! 
  - `beading_variation` (double between 0 and 1): The radius of each axon will vary periodically between the original radius and radius/beading_variation. If set to 1, there will be no beading.
  - `beading_frequency` (double): Frequency of axonal beading (= 1/nbr of spheres)
- Other Parameters (these are lists, if you want to put in multiple values, create a new line to do so. If there are more than one value in each list, the video will repeat itself after the first one to perform again according to the next values):
  - `vox_sizes` (list of int): The maximum distance (in micrometers) in space to define the corner of the 3D box to work in.
  - `icvf` (list of double between 0 and 1): Intra Compartment Volume Fraction.
  - `capacities` (list of int, must be below the number of processors available on the computer): Number of parallel threads to grow axons simultaneously.

## Contributors

### Authors and Affiliations

- **Jasmine Nguyen-Duc:** Centre Hospitalier Universitaire Vaudois (CHUV), Lausanne, Switzerland
- **Melina Cherchali:** École Polytechnique Fédérale de Lausanne (EPFL), Lausanne, Switzerland
- **Ines deRiedmatten:** Centre Hospitalier Universitaire Vaudois (CHUV), Lausanne, Switzerland
- **Ileana Jelescu:** Centre Hospitalier Universitaire Vaudois (CHUV), Lausanne, Switzerland

### Logo

![MIcMap Logo](https://wp.unil.ch/mic-map/files/2022/01/cropped-2-MicrostructureMappingLab-01.png)

### Website 

https://wp.unil.ch/mic-map/
