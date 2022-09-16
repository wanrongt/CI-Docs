# BHS BMC CI Process

##  Code repository

+ Openbmc : [https://github.com/intel-innersource/firmware.bmc.openbmc-commercial.bhs-openbmc-openbmc](https://github.com/intel-innersource/firmware.bmc.openbmc-commercial.bhs-openbmc-openbmc)
+ Meta-intel:  [https://github.com/intel-innersource/firmware.bmc.openbmc-commercial.bhs-openbmc-meta-intel](https://github.com/intel-innersource/firmware.bmc.openbmc-commercial.bhs-openbmc-meta-intel)
+ BHS CI Configuration files: [https://github.com/intel-collab/firmware.management.bmc.dsg-openbmc.openbmc-ci.openbmc-jenkins/tree/master/JenkinsBhsIDF](https://github.com/intel-collab/firmware.management.bmc.dsg-openbmc.openbmc-ci.openbmc-jenkins/tree/master/JenkinsBhsIDF)

## Build step
* Clone code

  ```python
  cd ~
  
  git clone https://github.com/intel-innersource/firmware.bmc.openbmc-commercial.bhs-openbmc-openbmc.git
  
  git clone https://github.com/intel-innersource/firmware.bmc.openbmc-commercial.bhs-openbmc-meta-intel.git
  
  mv dsg-openbmc-openbmc openbmc
  
  mv dsg-openbmc-meta-intel openbmc/openbmc-meta-intel
  ```

* Create workspace

  ```
  cd /home/jenkins/openbmc/
  
  export TEMPLATECONF=/home/jenkins/openbmc/openbmc-meta-intel/meta-bhs/conf/
  
  source oe-init-build-env
  ```

* Modify the thread to speed up the build

  ```
  vim ~/jenkins/openbmc/build/conf/local.conf
   
  #Add the following two lines：
  
  BB_NUMBER_THREADS ?= "16"
  
  PARALLEL_MAKE ?= "-j16"
  ```

* Execute **build command** 

  ```
  cd ~/jenkins/openbmc/build

  time bitbake intel-platforms --runall=fetch (optional, download libraries and repo first)
  
  time bitbake intel-platforms
  ```


* After the build is successful, build artifacts/images are placed under the path: 

  ```
  ~/openbmc/build/tmp/deploy/images/intel-ast2600/pfr_images
  ```

## Build job

###  Trigger job:

+ Openbmc-openbmc trigger job : [https://cbjenkins-pg.devtools.intel.com/teams-dsgbmc/job/dsgbmc/job/BirchstreamPc/job/dsg-bhs-openbmc-openbmc-trigger/](https://cbjenkins-pg.devtools.intel.com/teams-dsgbmc/job/dsgbmc/job/BirchstreamPc/job/dsg-bhs-openbmc-openbmc-trigger/)
+ Meta-intel trigger job : [https://cbjenkins-pg.devtools.intel.com/teams-dsgbmc/job/dsgbmc/job/BirchstreamPc/job/dsg-bhs-meta-intel-trigger/](https://cbjenkins-pg.devtools.intel.com/teams-dsgbmc/job/dsgbmc/job/BirchstreamPc/job/dsg-bhs-openbmc-openbmc-trigger/)
![](./Images/P37.png)
  Fig1 : Trigger job in Jenkins
### Full build job:

+ Birchstreampc-ci : [https://cbjenkins-pg.devtools.intel.com/teams-dsgbmc/job/dsgbmc/job/BirchstreamPc/job/dsg-birchstreampc-ci/](https://cbjenkins-pg.devtools.intel.com/teams-dsgbmc/job/dsgbmc/job/BirchstreamPc/job/dsg-birchstreampc-ci/)

## Build agent

### Build Env

+ Build environment of BHS platform is exactly the same as EGS,so we use same backup server and docker container to build.

### Create new cache directories

+ Download Dir : Storage of open source libraries, open source repositories and openbmc recipes repositories

  ```
  /download/bhs
  ```

+ Sstate-cache Dir

  ```
  /home/jenkins/agent/scache/openbmc-bhs/sstate-cache
  ```

  