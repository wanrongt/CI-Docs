# SSTF Overview

## What's SSTF
SSTF (System Software Test Framework) is a service and engine to execute test cases and track test result, designed for DSG Continuous Integration automation.

Main components:

- Pytest as the low-level testing framework
- Allure as the test reporting tool
- Jenkins web UI to trigger/monitor test execution
- Intel designed libraries and     test scripts

## Download links

SSTF can be downloaded from below two locations:

1. From SSTF server share folder: [http://sstf.sh.intel.com/sstf-release/](http://sstf.sh.intel.com/sstf-release/)     
2. From Gitlab: [https://gitlab.devtools.intel.com/dsg-ssa/sstf/-/tree/master](https://gitlab.devtools.intel.com/dsg-ssa/sstf/-/tree/master)     

## Installation procedure

- Option 1(recommended for general usage):

1. Download SSTF package from [http://sstf.sh.intel.com/sstf-release/](http://sstf.sh.intel.com/sstf-release/).


2. Unzip the file to local disk.

3. Install Python 3.6+ and required python packages by following below command:

   ```
   pip install -r requirements.txt     --proxy=your_local_proxy_server
   ```

4. (For Linux only) Install command line utility:

    ```
   sudo apt install ipmitool curl p7zip
    ```

- Option 2(recommended for script development):

1. Clone the project from Gitlab to local:

   ```
   git clone https://gitlab.devtools.intel.com/dsg-ssa/sstf.git
   ```

2. Install Python 3.6+ and  required python packages by following below command:

   ```
   pip install -r requirements.txt     --proxy=your_local_proxy_server 
   ```

3. (For Linux only) Install command line utility:

   ```
   sudo apt install ipmitool curl p7zip
   ```

## Test case execution 

### How to run test scripts

1. Update test environment settings in **sstf/settings.py**     
2. Run single *test* or *test suite (grouped by a folder)*     

- Pycharm click "Run" button for single test file
- Command `pytest xxx.py or test_folder` 
- Command `python xxx.py` 

All test cases are following pytest default test discovery and execution syntax

### How to check test report

Two types of html test report are supported:

- self-contained HTML file:  sstf_test.html
- allure: Type command `allure_path serve allure_report`

# SSTF Development Guide

## SSTF Developement flow introduction  
SSTF uses simplified ["GitHub Flow"](https://githubflow.github.io/). We don't folk. Github Flow is not perfect, but it's good enough for SSTF project now. 
1. Anything in the master branch is deployable.
2. To work on something new, create a descriptively named branch off of master (ie: dev_github_branch)
   ```
   git checkout -b dev_github_branch
   ```
3. Commit to that branch locally and regularly push your work to the same named branch on the server. For the 1st time push, you may need to set upstream using below command
   ```
   git push --set-upstream origin github_flow
   ```
4. When you need feedback or help, or you think the branch is ready for merging, open a pull request. Please add the test job link in your PR Comments.  
5. After someone else has reviewed and signed off on the feature, you can merge it into master 
6. Once it is merged and pushed to 'master', you can and should deploy immediately
7. Delete your own develop branch. 


## New Jenkins job slave setup notes


## Debug Job usage guide.
