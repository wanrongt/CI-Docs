Engineer Build Process
===================================

Engineering builds are used to do some special functional tests.

Engineer builds like the developer builds requires five repos, the difference is that these repos use different
 branches, in which Intel repo and FDBin repo have established their own separate branch.
 
**1. create new branch for Intel and FDBin repo**

Colleagues in the engineer team will create the new branch and push the code to github.
Since these branch need to be distinguished from the developer build, so the branch belong to the dev type. 
For example:
Intel: dev/eaglestreampc_dsg_smi/zhikaisu
FDBin: dev/eaglestreampc_dsg_fdbin/mal

**2. Update the manifest**

Following the combo naming rules before the FST Team, these combo names will be followed by **_dev**.
Add the combo and build targets:
```
<Combination name="eaglestreampc_dsg_smi_dev" description="the branch for eaglestreampc dsg smi">
  <Source localRoot="Intel" remote="firmware.boot.uefi.iafw.intel" branch="dev/eaglestreampc_dsg_smi/zhikaisu" sparseCheckout="true" />
  <Source localRoot="Edk2" remote="firmware.boot.uefi.iafw.externalmirror.edk2" branch="platform/eaglestreampc_dsg_main" sparseCheckout="true" enableSubmodule="true"/>
  <Source localRoot="FDBin" remote="firmware.boot.uefi.iafw.fdbinary" branch="dev/eaglestreampc_dsg_fdbin/mal" sparseCheckout="true" />
  <Source localRoot="Edk2Platforms" remote="firmware.boot.uefi.iafw.externalmirror.edk2-platforms" branch="platform/eaglestreampc_dsg_main" sparseCheckout="true" />
  <Source localRoot="Edk2-Staging-PlatformRuntimeMechanism" remote="firmware.boot.uefi.iafw.externalmirror.edk2-staging" branch="platform/eaglestreampc_dsg_main" sparseCheckout="true" />
  <Build group="Build-eaglestreampc_dsg_smi_dev" />
</Combination>

<BuildGroup name="Build-eaglestreampc_dsg_smi_dev" buildServer="Server1" projectPath="IAFW_1S/DSG/EagleStreamPc/eaglestreampc_dsg_smi_dev">
   <Build target="EagleStreamPc_SMI_Debug" />
   <Build target="EagleStreamPc_SMI_Release" />
</BuildGroup>
```
Engineer build needs to synchronize eaglestreampc_dsg_main branch code at the time of weekly build.

Add the build step to the manifest:
```
<BuildTarget name="EagleStreamPc_SMI_Debug" description="EagleStreamPc SMI debug build" timeout="60" >
  <StepList>
    <Step>git pull origin platform/eaglestreampc_dsg_main</Step>
    <Step>git push origin dev/eaglestreampc_dsg_smi/zhikaisu</Step>
    <Step>cd ../FDBin &amp;&amp; pwd</Step>
    <Step>git pull origin platform/eaglestreampc_dsg_main</Step>
    <Step>git push origin dev/eaglestreampc_dsg_fdbin/mal &amp;&amp; git status</Step>
    <Step>cd ../Intel &amp;&amp; git status</Step>
    <Step>c:\python36\python.exe EagleStreamPcPkg\PlatformBIOSBuild.py -b DEBUG -t VS15</Step>
  </StepList>
</BuildTarget>
```
**Build Process:**

(1) git clone dev branch code\
    (Now in Intel Repo k:/Intel)\
(2) git pull git pull origin platform/eaglestreampc_dsg_main\
    (synchronize platform/eaglestreampc_dsg_main branch code of Intel repo into the build environment)\
(3) git push origin dev/eaglestreampc_dsg_smi/zhikaisu\
    (Push code from the build environment to the remote repository to synchronize the remote Intel repository's code)\
(4) cd ../FDBin\
    (Switch to the FDBin directory)\
(5) git pull origin platform/eaglestreampc_dsg_main\
    (synchronize platform/eaglestreampc_dsg_main branch code of FDBin repo into the build environment)\
(6) git push origin dev/eaglestreampc_dsg_fdbin/mal\
    (Push code from the build environment to the remote repository to synchronize the remote FDBin repository's code)\
(7) cd ../Intel\
    (Switch to the Intel directory for compile the code)\
(8) c:\python36\python.exe EagleStreamPcPkg\PlatformBIOSBuild.py -b DEBUG -t VS15\
    (compile the code)