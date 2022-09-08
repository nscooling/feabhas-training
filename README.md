# Example Feahas Docker Training Project

Download this proof of concept repo.

Ensure Docker is running and in  VS Code:

   * **Open Folder in container...** top open this folder
   * if asked select **Dockerfile** from the options

The remote container connect as user `feabhas/ubuntu` in the
working folder `~/workspace`. There are additional README files
in this folder for further information (TODO: update target README).

There is a supplied `main.cpp` which is a copy of the one in
`~/workspace/solutions/01-wms-test` ready to build.

Build a project using Ctrl-Shft-B and select **build**.

Run the script without debugging:

   * in the host launch the `qemu-wms.py` Python script
   * run the Ctrl-Shft-P test task **Run QEMU**
   * click on the **Connect** button on the Python GUI

To run with debugging:

   * set a breakpoint (or pause debugging after startup)
   * from the **host** launch the `qemu-wms.py` Python script
   * press F5 (or run debug task **QEMU Debug**)
   * within 30 secs click **Connect** on the Python GUI

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
