# SSTF Host ENV Setup

### 1. Install dependence on the host

        1. Install Python3 and add the launchers directory to the PATH.
        
![](.\Images\Python3InstalledSuccessfully.png)
        
        2. Install Git and add proxy to configuration file.
        
        # git config --global http.proxy=http://child-prc.intel.com:913
        # git config --global https.proxy=https://child-prc.intel.com:913
        
![](.\Images\GitInstalledSuccessfully.png)
        
        3. Install Chrome and Chrome web driver.
      
![](.\Images\InstallChromeDriver.png)
        
        4. Install Firefox and Firefox web driver.
        
![](.\Images\InstallFirefoxDriver.png)
     
        5. Download and install allure from http://allure.qatools.ru/, add the "C:\allure-2.13.7\bin" to the PATH

![](.\Images\InstallAllure.png)

        6. Install OpenJDK

![](.\Images\InstallJDK.png)
      
        7. Install EasyOCR data model 
        
        8. Download and install FFmpeg from https://github.com/BtbN/FFmpeg-Builds/releases, add "C:\ffmpeg-master-latest-win64-gpl-shared\bin" to the PATH
        
![](.\Images\InstallFfmpeg.png)
        
        9. Download and install rsc2service from http://sstf.sh.intel.com/software/
        
![](.\Images\InstallRSC2.png)

        10. Install VirtualBox
        
        11. Download and install sstf-vm from http://sstf.sh.intel.com/software/
        
        12. Install others SSTF requirement python library refer to https://github.com/intel-collab/frameworks.validation.server.sstf/requirements.txt
        
 ### 2. Configure Jenkins Job
        
        1. Create a new Jenkins node, then lauch and check it
        
  ![](.\Images\CreateNewNode.png)
  
  ![](.\Images\LauchNode.png)
  
        2. Set the Jenkins node home path, git path, allure path, SUT_Config virable, Execute Windows batch command etc.
        
        3. Build and run the job
        
  ![](.\Images\BuildJob.png)
  
        4. Check the report in Allure
        
  ![](.\Images\CheckReport.png)
  
### 3. Update BIOS, BMC and CPLD for SUT

###### Use SF600 to program BIOS and BMC offline.
        
            1. Open DediProg Production Software.and select IC brand and part number.

            2. Download the programing file and save the file to PC.

            3. Click “File” icon to load programming flow.
            
![](.\Images\LoadFile.png)

            4. Click "Batch" icon to perform remaining operations and verify OK.
            
![](.\Images\BatchFile.png)

###### Use Quartus Programmer to update CPLD
        
            1. Download the programmer file and save it to PC, Start Quartus and configure like this:
            
![](.\Images\ProgramConfigure.png)

            2. Wait the performed operations ended successfully
            
![](.\Images\EndedProgram.png)
             