# MPC_Implementation
## Project description: 
- A project to implement MPC control calculation with constraints on Microcomputer (Teensy4.1) for simple autonoumous driving control.
- The vehicle uses Kinematic Bicycle Model. 
- The program utilizes Quadratic Programming solvers and run on PlatformIO IDE.

## Structure:
Main files of this project are stored in src folder (because of platformIO configuration), including:
1.  konfig.h
2.  matrix.cpp
3.  matrix.h
4.  mpc.cpp
5.  mpc.h
6.  mpc_constrainedschur_engl.ino
## Instruction:
- Install the PlatformIO
- Configure the system for Teensy40 (as environment) and Teensy41 (as a device, change this to your Arduino system, accordingly)
- Build and Upload

### Configuration:
For custom implementation, you need to modify `konfig.h` and `*.ino` files. More specifically:
1. Set the length of `X, U, Z` vectors and sampling time `dt` in `konfig.h`, depend on your model.
2. Set the MPC parameters like `Hp (Prediction Horizon)` or `Hu (Control Horizon)` in `konfig.h`, depend on your application.
3. Enable/disable and set the MPC constraints parameters like `DU`, `U`, or `Z` in `konfig.h`, depend on your application.
4. Define the (linear) matrix system `A, B, C` and MPC initialization value `weightQ, weightR` in the `*.ino` file.

After that, you only need to initialize the MPC class, set the non-zero initialization matrix by calling `MPC::vReInit(A, B, C, weightQ, weightR)` function at initialization, and call the function `MPC::bUpdate(SP, x, u)` at every sampling time to calculate the control value `u(k)`.
### Calculation and algorithms (to be updated):
1.  Matrix
2.  Quadratic Programming solver
3.  Optimization
4.  

This project is adapted from a public repo by pronenewbits. Thank you very much for developing such a good repo and detailed docs. 
- https://github.com/pronenewbits/Arduino_Constrained_MPC_Library
