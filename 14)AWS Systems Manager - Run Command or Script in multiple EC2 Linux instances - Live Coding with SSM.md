<pre>AWS SYSTEM MANAGER
(RUN COMMANDS IN MULTIPLE EC2 INSTANCES)
 here we need tags env production and testing and for the both os also
 we need IAM role 
 steps 
 create role
 select EC2
 select role as EC2 role for simply system manager
 next permissions
 select Amazonec2roleforSSM
 give role name 
 create role</pre>
 
<pre>for this select 2 instances 
 under the creation select the IAM role which we given at the time of Amazonec2roleforSSM
 under Advanced Details
 under add tags
 Name SSm-Demo
 Env  prod
 OS   Linux</pre>
 
<pre> for running commands remotely
 steps
 run commands
 Run a COMMAND
 select run a shell script
 select targets by: Manually select the instances
 click on select instances
 select both
 Execute on (leave it empty)
 stop after (if there are any errors)
 click on run
 view result
 select command iD
 choose the first command iD
 click output
 the out put is given as link (if the output is more characters it will be stored in S3 bucket)</pre>
 
<pre>If we want to run on specific instances
 Steps
  run commands
 Run a COMMAND
 select run a shell script
 select targets by: specifying a tag give the tag name</pre>
 
 
<pre># Install AWS SSM
cd /tmp
sudo yum install -y https://s3.amazonaws.com/ec2-download-windows/SSmAgent/latest/linux_amd64/amazon-ssm-agent.rpm
yum install -y amazon-ssm-agent.rpm
sudo systemctl start amazon-ssm-agent
sudo systemctl enable amazon-ssm-agent
------------------------------------------------------------------------------------------------------------------------
#/bin/bash

echo -e "{
 'Hostname':'`curl http://169.254.169.254/latest/meta-data/local-hostname--silent`', \
\n 'AMI-ID':'`curl http://169.254.169.254/latest/meta-data/ami-id--silent`', \
\n 'Kernel-Version':'`rpm -q kernel`' \
\n 'Instance Type':'`curl http://169.254.169.254/latest/meta-data/instance-type--silent`'
 }"</pre>