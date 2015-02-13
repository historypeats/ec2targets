#EC2 Targets
This tool is useful when doing an audit/pentest and need to gather public/private IP information for EC2 instances. EC2 Instance information is searched for based on Tags. So let's say you want to pentest/audit the QA environment, you could run the tool like so: ./ec2targets Environment QA, where "Environment" is the tag name and "QA" is the tag value

##Installation
1. First download or clone the repo.
```bash
git clone https://github.com/historypeats/ec2targets.git
```
2. Next install the requirements with pip.
```bash
pip install -r requirements.txt
```
Note: You may need to use sudo if you are not using virtualenv.
3. Finally, invoke the ec2targets script.
```bash
./ec2targets -h
```

## Credentials
This tool uses the boto framework, so you must either have your AWS secret key in your ~/.aws folder or you can add them directly in the script's source code:

```python
# AWS creds. If these values are not changed, boto will check your .aws/.boto configs for creds
AWS_ACCESS_KEY_ID = None
AWS_SECRET_ACCESS_KEY = None


```
##Usage
```bash
usage: ec2targets [-h] [-t TAG] [-n NAME] [-r REGION] outfile

Gather EC2 Targets

positional arguments:
  outfile     The output file in CSV format

optional arguments:
  -h, --help  show this help message and exit
  -t TAG      Search by tag. Tag argument should be in the form TagName:Value.
              Example: -t Environment:QA
  -n NAME     Search by name
  -r REGION   Search by region
```
Note: If no filter flags (-t, -n, -r) are used, ec2targets will list the attack surface for all EC2 instances.
