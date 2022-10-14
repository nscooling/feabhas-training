# Example Feahas Docker Training Project

**Note**: this Docker based rtraining solution is under development
and designed as a potentail alternative to Virtual Machines
normally used for Feabhas embedded C/C++ training courses.

# Getting Started

Ensure Docker is running and then start VS Code and select:

   * **Open Folder in container...** to open this repo folder

This will cause Docker to download a container from 
`martinbond7/feabhas-target:latest` which is configured with a toolchain
for building Feabhas embedded training projects:
   * Arm Embedded Toolchain (10.3)
   * Customised xPack QEMU Washing Machine Simulator (WMS) emulator

Once downloaded VS Code will connect to the remote container as 
user `feabhas/ubuntu`. The container working folder is set to `~/workspace` and 
this is mapped onto this repo folder. 

This folder will now contain the files for a standard embedded target 
for the Feabhas QEMU WMS emulator (copied from a template in the Docker image). 

Unlike the standard VirtualBox container this Docker container does not 
use the embedded QEMU graphics but opens a diagnostic interface on port 8888. 
To run the built application the python script `qemu_wms.py` should be started
in the host (not via VS Code).

There are additional README files in the `workspace` folder which 
describe how to build and run an embedded project using QEMU WMS and
the remote Python script.

There is a supplied `src/main.cpp` which is simple for loop
that is ready to build.

Build the project using Ctrl-Shft-B and select **build**.

Run the script without debugging:

   * from the **host** launch the `qemu-wms.py` Python script
   * in VS code press Ctrl-Shft-P and type `test` 
   * in the popup list select **Tasks: Run Test task**
   * in the list of tasks select **Run QEMU**
   * in the Python GUI click on the **Connect** button 

To run with debugging:

   * set a breakpoint in the code
   * from the **host** launch the `qemu-wms.py` Python script
   * press F5 (or run debug task **QEMU Debug**)
   * within 30 secs click **Connect** on the Python GUI

# Exercises requiring USART3

There are extra tasks and launch scripts to run with USART3 connected to
the serial port 7777. When using the Python GUI click on the
`Connect+Serial` button to connect to both ports - the bottom of the GUI 
has an interactive text area you can use to send and receive using USART3.
A `telnet` command is provided in the Linux image configured for single
character I/O.

## VS Code tasks and launch actions

VS Code tasks:

   * build
   * clean
   * reset

VS Code test tasks:

   * Run QEMU -- uses `diag-qemu.sh` script to start dianostic server on port 8888
   * Run QEMU serial -- run with USART3 on serial port 7777
   * Run QEMU container -- uses `run-qemu.sh` to run no graphics in the container
   * Run QEMU container serial -- no graphics with USART3 on port 7777

DVS Code debug tasks (use F5 or Debug view):

   * QEMU Debug -- use host Python GUI
   * QEMU Debug serial -- host Python GUI and USART3
   * QEMU Debug container -- no grpahics QEMU in container
   * QEMU Debug container serial -- no grpahics QEMU in container
