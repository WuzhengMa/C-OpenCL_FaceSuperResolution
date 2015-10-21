### FaceSuperResolution
Face super-resolution with LcR algorithm in C and OpenCL


### Project overview
The codes in this repository are optimized from my predecessor's work, who is also a poineer in this project. 

Check out his link for more details on the project: 'https://github.com/reginalio'

This repository contains the C and OpenCL code for a face super-resolution algorithm called LcR proposed by Junjun Jiang, Ruimin Hu, Zhongyuan Wang, Zhen Han. Noise Robust Face Hallucination via
Locality-Constrained Representation. Multimedia, IEEE Transactions on 2014;16(5) 1268-1281.

Implementing the algorithm above requires massive cost on time, the step to solve a matrix linear equation within the algorithm occupied most of the cost. Therefore, a fast implementation on solving the linear equation must be used to reduce the time consumption. In addition, extra hardwares beside CPU are also considerred.   

In this repository, Gauss Seidel Method and a FPGA running environment are used to solve the matrix linear equation

For other implementations(e.g. analytic method and iterative method named Conjugate Gredient Method with a CPU running environment) on solving the linear equation, check out the link above.


### Makefile command for different compilation purposes

make: compile the c source file that will run on CPU

make kernel: compile the kernel code which will run on the board

make simu_iter: compile the kernel code by using the emulator on CPU

make run: bin/lcr

make without_hw: only optimize the kernel code and generate hardware language from it, but will not compile on hardware; therefore this process is much quicker. This command allows us to have a quick compilation so that we could see the optimization report without too much waiting.

make cleanall: clean the executable file for both the c source codes and the kernel code

make clean: only clean the executable file generated from c source codes


### Full compilation

The program will run on CPU; 
When it comes to solving the linear equation, it will send a query to a FPGA board;
After computing from FPGA, the results will be sent back to CPU and the grogram will then keep running.

-----------------------------------------------
Before compilation, due to the difference in directories, the directories needed to be set.
Open up Makefile, adjust directories for input training images, input testing images, output images and the executable files generated by aoc compiler.

Open up util.h to change any parameters, after that, the parameters also need to be changed within the Makefile

-----------------------------------------------
Use 'make kernel' command to fully compile the kernel code and generate executable files for the board.
Use 'make' command to compile all the c source codes, generate executable files for the program in CPU.
Use 'make run' command to run the program. 
After running, you are expected to see the time it costs to run the program.

