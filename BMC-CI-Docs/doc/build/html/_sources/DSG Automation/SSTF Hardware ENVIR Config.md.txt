# SSTF Hardware ENVIR Config

## Material shows

![](./Images/A.png)

![](./Images/a003.png)



## Material list & check

|              name              | quantity |
| :----------------------------: | -------- |
|     BMC serial port cable      | x 1      |
|     BIOS serial port cable     | x 1      |
|       USB to LAN device        | x 1      |
| RSC2 To SUT Power supply cable | x 2      |
|    RSC2 Power supply cable     | x 2      |
|              Host              | x 1      |
|            RSC2 Box            | x 1      |
|           KVM Remote           | x 1      |
|   Host-SUT & SUT-RSC2 cable    | x 2      |
|             Switch             | x 1      |
|              SUT               | x 1      |



## BIOS cable link & check

### connection display

BIOS cable is used to access the BIOS of the SUT on Host. One end of bios cable link the USB port of the HOST and the other end is link SUT net port, as shown below.

![](./Images/a11.png)

![](./Images/a29.png)



1. Open the MobaXterm app  ![](./Images/a13.png)

2. After the application starts, enter the session page

   ![](./Images/a15.png)

3. Select Serial option

   ![](./Images/a17.png)

   

4. Select the serial port number for connecting the bios cable ,and select 115200 Speed(bps).

   ![](./Images/a19.png)

5. click ok

   ![](./Images/a004.png)

6. Double-click the Serial option you just added ,Then press Enter,If the Bios set-up page is displayed, Indicates that the connection is successful

   ![](./Images/a27.png)

   ​		Notice: Do not select the wrong Port number and speed value. If the BMC login prompt is not 		    displayed at the end, check the link of the bios cable.





## BMC cable link & check

### connection display

BMC cable is used to access the BMC of the SUT on Host. One end of BMC cable link the USB port of the HOST and the other end is inserted into the J18 position on the board.

![](./Images/a10.png)  ![](./Images/a30.png)

​	Notice: When inserted into the board, the white line should be aligned with the small triangle on the  pictured above



### connection verification

1. Open the MobaXterm app ![](./Images/a14.png)

2. Go to the Session page

   ![](./Images/a16.png)

3. Select Serial option

   ![](./Images/a18.png)

4. Select the serial port number for connecting the BMC cable ,and select 115200 Speed(bps).

   ![](./Images/a20.png)

   ​						notice: the serial port numbers of BMC and bios are different

5. click ok

   ![](./Images/a005.png)

6. Double-click the Serial option you just added ,Then press Enter,If the BMC login page is displayed, Indicates that the connection is successful

   ![](./Images/a21.png)

    	 

   ​	Notice: Do not select the wrong Port number and speed value. If the BMC login prompt is not displayed at the end, check the link of the BMC cable and debug again.





## RSC2 link & check

### introduction

Using a Remote System Controller 2 (RSC2), a user can remotely control a system
under test (SUT) located anywhere in the world. The RSC2 gives the ability to control
2 AC power supplies, DC power, DC reset, and 8 jumpers on the SUT's baseboard. It
also performs AC/DC power cycling via a shared USB drive. The shared USB drive
can be used to copy files or test program to the SUT, and can be further used to
install an operating system remotely.

![](./Images/a006.png)

![](./Images/a31.png)

### connection display

Follow these steps to begin using your RSC2

1) Install the software package found on the RSC2 installation media.

![](./Images/a007.png)

2) go to Windows Services manager and ensure the RSC2
Server service is Started.

![](./Images/a002.png)



3)  Attach the RSC2 box to the host computer and the SUT by connecting the following mandatory connections:

a. AC IN A must be plugged into the wall.

b. AC OUT A must be plugged into the SUT’s power supply.

c. HOST USB must be connected to any of the host system’s USB ports.

d. SERVER USB must be connected to any of the SUT’s USB ports.

e. Insert a USB flash drive into the “USB DRIVE” connector on the front panel of the RSC2

Your system should look like this when done:

![](./Images/a008.png)



4)The other end of the front panel cable is inserted into the SSI_FRONT_PANEL position on the SUT

![](./Images/a12.png)	![](./Images/a32.png)

### connection verification

1. Launch the software![](./Images/a001.png)

2. Click the ‘Add Host’ button to add a new RSC2 

   ![](./Images/a22.png)

3. Select Local and click Find

   ![](./Images/a23.png)

4. double click the searched option

   ![](./Images/a24.png)

   ​										Searched option ：displays the host name and device name

5.   SUT can be controlled through RSC2 ,the page display after entering is as shown in the figure below

   ![](./Images/a25.png)

6. Press AC power a and AC power B to turn the green display into green and check the power failure of SUT. If the power failure is successful, it indicates that the rsc2 connection is successful

   ![](./Images/a26.png)

   
   
   ​			If you want to use RSC2 for anchor jumping control or have  other problems during connection, please refer to   RSC2 User Manual.pdf

















