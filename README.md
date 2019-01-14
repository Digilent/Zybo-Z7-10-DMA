Zybo-Z7-10-DMA Demo
====================

Description
-----------

This project demonstrates how to use the Zybo Z7-10's Audio Codec and RAM to record samples of audio and play them back. The Zynq processor is used to control the data pipeline. Vivado is used to build the demo's hardware platform, and Xilinx SDK is used to program the bitstream onto the board and to build and deploy a C application.

To use this demo, the Zybo Z7-10 must be connected to a computer over MicroUSB, which must be running a serial terminal. For more information on how to set up and use a serial terminal, such as Tera Term or PuTTY, refer to [this tutorial](https://reference.digilentinc.com/learn/programmable-logic/tutorials/tera-term).

The audio demo records a 5 second sample from microphone(J6) or line in (J7) and plays it back on headphone out(J5). Recording and playback are controlled by push buttons from a usb uart serial menu as shown below.

|  Button  | Function             |
| -------- | -------------------- |
|  BTN0    |  no effect           |
|  BTN1    |  record from mic in  |
|  BTN2    |  play on hph out     |
|  BTN3    |  record from line in |



Requirements
------------
* **Zybo Z7-10**: To purchase a Zybo Z7-10, see the [Digilent Store](https://store.digilentinc.com/zybo-z7-zynq-7000-arm-fpga-soc-development-board/).
* **Vivado 2018.2 Installation with Xilinx SDK**: To set up Vivado, see the [Installing Vivado and Digilent Board Files Tutorial](https://reference.digilentinc.com/vivado/installing-vivado/start).
* **Serial Terminal Emulator**: 
* **MicroUSB Cable**
* **Audio cables**

Demo Setup
----------

1. Download the most recent release ZIP archive ("Zybo-Z7-10-DMA-2018.2-*.zip") from the repo's [releases page](https://github.com/Digilent/Zybo-Z7-10-DMA/releases).
2. Extract the downloaded ZIP.
3. Open the XPR project file, found at \<archive extracted location\>/vivado_proj/Zybo-Z7-10-DMA.xpr, included in the extracted release archive in Vivado 2018.2.
4. In the toolbar at the top of the Vivado window, select **File -> Export -> Export Hardware**. Select **\<Local to Project\>** as the Exported Location and make sure that the **Include bitstream** box is checked, then click **OK**.
5. In the toolbar at the top of the Vivado window, select **File -> Launch SDK**. Select **\<Local to Project\>** as both the workspace location and exported location, then click **OK**.
6. With Vivado SDK opened, wait for the hardware platform exported by Vivado to be imported.
7. In the toolbar at the top of the SDK window, select **File -> New -> Application Project**.
8. Fill out the fields in the first page of the New Application Project Wizard as in the table below. Most of the listed values will be the wizard's defaults, but are included in the table for completeness.

| Setting                                 | Value                             |
| --------------------------------------- | --------------------------------- |
| Project Name                            | Zybo-Z7-10-DMA                    |
| Use default location                    | Checked box                       |
| OS Platform                             | standalone                        |
| Target Hardware: Hardware Platform      | design_1_wrapper_hw_platform_0    |
| Target Hardware: Processor              | ps7_cortexa9_0                    |
| Target Software: Language               | C                                 |
| Target Software: Board Support Package  | Create New (Zybo-Z7-10-DMA_bsp)   |

9. Click **Next**.
10. From the list of template applications, select "Empty Application", then click **Finish**.
11. In the Project Explorer pane to the left of the SDK window, expand the new application project (named "Zybo-Z7-10-DMA").
12. Right click on the "src" subdirectory of the application project and select **Import**.
13. In the "Select an import wizard" pane of the window that pops up, expand **General** and select **File System**. Then click **Next**.
14. Fill out the fields of the "File system" screen as in the table below. Most of the listed values will be the defaults, but are included in the table for completeness.

| Setting                                                | Value                                      |
| -                                                      | -                                          |
| From directory                                         | \<archive extracted location\>/sdk_appsrc  |
| Files to import pane: sdk_appsrc                       | Checked box                                |
| Into folder                                            | Zybo-Z7-10-DMA/src                         |
| Options: Overwrite existing resources without warning  | Checked box                                |
| Options: Create top-level folder                       | Unchecked box                              |

15. Click **Finish**.

<Note for maintainers: This project does not require any additional configuration of application or bsp projects. Projects that require any of this configuration should have the steps required to do so described here.>

16. Plug in a test circuit to the Zybo Z7-10's analog input pins.
17. Open a serial terminal application (such as TeraTerm FIXME LINK) and connect it to the Zybo Z7-10's serial port, using a baud rate of 115200.
18. In the toolbar at the top of the SDK window, select **Xilinx -> Program FPGA**. Leave all fields as their defaults and click "Program".
19. In the Project Explorer pane, right click on the "Zybo-Z7-10-DMA" application project and select "Run As -> Launch on Hardware (System Debugger)".
20. The application will now be running on the Zybo Z7-10. It can be interacted with as described in the first section of this README.

Next Steps
----------
This demo can be used as a basis for other projects by modifying the hardware platform in the Vivado project's block design or by modifying the SDK application project.

Check out the Zybo Z7-10's [Resource Center](https://reference.digilentinc.com/reference/programmable-logic/zybo-z7/start) to find more documentation, demos, and tutorials.

For technical support or questions, please post on the [Digilent Forum](forum.digilentinc.com).

Known Issues
------------
Ignorable critical warnings regarding ddr skew parameters - see Zybo Z7 hardware errata for more information.

Additional Notes
----------------
For more information on how this project is version controlled, refer to the [digilent-vivado-scripts repo](https://github.com/digilent/digilent-vivado-scripts).