# Amazon Web Service Command Line Interface (AWSCLI) Installation
Step by step installation guideline for AWSCLI in Windows 10 with Python 3.5+.

#### Step 1: Installing Python 3.5+

First install Python 3.5+ and add Python to Environment Path Variable. 

* `Python 3.5+` in Windows: Download and install `Python 3.5+`. URL:
 [https://www.python.org/downloads/](https://www.python.org/downloads/)
* While installing **DO NOT FORGET TO CHECK `Add Python 3.5+ to Path` CHECKBOX**. 
* To check Python version, open command prompt (CMD) and write `python --version`.
Check if Python 3.5+ version is installed.

#### Step 2: Install AWSCLI Python package

* Open Command Prompt(CMD) and do the following.
* `pip install --upgrade --user awscli`

#### Step 3: Add AWSCLI to path

* Add AWSCLI path to Environment Variables.
* `%USERPROFILE%\AppData\Roaming\Python\Python35\Scripts`
* To check AWSCLI version, open command prompt (CMD) and write `aws --version`.
You will get something like `aws-cli/1.11.63 Python/3.5.2 Windows/10 botocore/1.5.26`

#### Step 4: Configure AWSCLI

* Open Command Prompt(CMD) and do the following.
* `aws configure`
* AWS Access Key ID [None]: YOUR-AWS-USER-KEY-ID
* AWS Secret Access Key [None]: YOUR-AWS-USER-SECRET-ACCESS-KEY 
* Default region name [None]: us-east-1
* Default output format [None]: json

#### Step 5: Configure AWSCLI

* Open Command Prompt(CMD) and do the following.
* `aws configure`
* AWS Access Key ID [None]: YOUR-AWS-USER-KEY-ID
* AWS Secret Access Key [None]: YOUR-AWS-USER-SECRET-ACCESS-KEY 
* Default region name [None]: us-east-1
* Default output format [None]: json

#### Step 6: Confirm installation of AWSCLI

* Open Command Prompt(CMD) and list all the buckets of your AWS.
* `aws s3 ls`

### Reference

* [Installing the AWS Command Line Interface](http://docs.aws.amazon.com/cli/latest/userguide/installing.html)
* [Adding the AWS CLI Executable to your Command Line Path](http://docs.aws.amazon.com/cli/latest/userguide/awscli-install-windows.html#awscli-install-windows-path)
* [Python Download](https://www.python.org/downloads/)