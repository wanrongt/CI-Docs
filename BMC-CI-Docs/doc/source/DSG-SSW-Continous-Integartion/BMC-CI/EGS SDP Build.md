# EGS SDP Build

## Introduction

+ Add some options to BMC code to make the build generate SDP images

## Build Preparation 

### Code Repo

+ **[openbmc](https://github.com/intel-collab/firmware.management.bmc.dsg-openbmc.dsg-openbmc-openbmc)**: The main framework of EGS openbmc

+ **[openbmc-meta-intel](https://github.com/intel-collab/firmware.management.bmc.dsg-openbmc.dsg-openbmc-meta-intel)**: The feature code of EGS openbmc

## Build step

+ Preparing the build environment

  ```
  mv openbmc-meta-intel openbmc/
  export TEMPLATECONF=$WORKSPACE/openbmc/openbmc-meta-intel/meta-egs/conf
  cd $WORKSPACE/openbmc
  source oe-init-build-env
  ```

+ Add one line in openbmc/build/conf/local.conf to enable sdp build

  ```
  EXTRA_IMAGE_FEATURES += "sdp-feature"
  ```

+ Add three lines in openbmc/openbmc-meta-intel/meta-common/classes/image_types_intel_pfr.bbclass to generate sdp-OBMC-egs-xxx-xxx-pfr-full.ROM

  ```
  bld_suffix="_dnp"
  bld_prefix="sdp-"
  do_image_pfr_internal
  ```

+ Build command

  ```
  bitbake intel-platforms
  ```