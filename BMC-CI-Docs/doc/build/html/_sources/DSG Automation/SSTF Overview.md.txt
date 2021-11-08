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

