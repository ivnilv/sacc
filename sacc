#!/usr/bin/env bash
# Source external bash resources
. ./spinner.sh

# Variables
aws=`which aws`
AWS_CONFIG_G7R_FILE=~/.aws/aws-config-g7r.cfg
#AWS_CONFIG_FILE=~/.aws/config

# Functions

generate_tmp_config_file(){
    > $AWS_CONFIG_G7R_FILE
    echo -e "[default]" >> $AWS_CONFIG_G7R_FILE
    echo -n -e "aws_access_key_id = " >> $AWS_CONFIG_G7R_FILE;  echo -e $aws_acc_key >> $AWS_CONFIG_G7R_FILE
    echo -n -e "aws_secret_access_key = " >> $AWS_CONFIG_G7R_FILE; echo -e $aws_sec_key >> $AWS_CONFIG_G7R_FILE
}

generate_real_config_file(){
    > $AWS_CONFIG_G7R_FILE
    echo -e "[default]" >> $AWS_CONFIG_G7R_FILE
    echo -n -e "aws_access_key_id = " >> $AWS_CONFIG_G7R_FILE;  echo -e $aws_acc_key >> $AWS_CONFIG_G7R_FILE
    echo -n -e "aws_secret_access_key = " >> $AWS_CONFIG_G7R_FILE; echo -e $aws_sec_key >> $AWS_CONFIG_G7R_FILE
}

# Main

# First let's get your AWS Access Key ID and Access Secret Key. 
# Those will be used later to request new AWS Access Key ID, Access Secret Key and AWS Session Token. 
# Session Tokens have a default TTL 43,200 seconds (12 hours). 
# You can change that or use the default later in the script.
echo "Enter your AWS Access Key ID: "  
read aws_acc_key
#echo $aws_acc_key
echo "Enter your AWS Secret Key: "
read aws_sec_key
# Ask for MFA device ARN number:
echo "Enter your MFA device number: (Format: arn:aws:iam::123456789123:mfa/user.name)"
read mfa_arn
# Write those to ~/.aws/aws-config-g7r.cfg
AWS_CONFIG_G7R_FILE=~/.aws/aws-config-g7r.cfg
touch $AWS_CONFIG_G7R_FILE
chmod 600 $AWS_CONFIG_G7R_FILE

generate_tmp_config_file
# Ask for mfa and send a warning to prepare device 
echo "Next we'll need your MFA code. Please prepare your device and wait for the input prompt!"
echo ""
sleep 5
echo -n "Enter MFA Code here: "
read mfa_code
#echo -n "MFA code is: "; echo $mfa_code

# Request real credentials to store in real config
#AWS_CONFIG_FILE=${AWS_CONFIG_G7R_FILE}
AWS_SHARED_CREDENTIALS_FILE=${AWS_CONFIG_G7R_FILE} `which aws` sts get-session-token --duration-seconds 3600 --serial-number $mfa_arn --token-code $mfa_code
#AWS_SHARED_CREDENTIALS_FILE=${AWS_CONFIG_G7R_FILE} export mfa_arn=${mfa_arn} ; export mfa_code=${mfa_code} ; bash -c '/usr/local/bin/aws sts get-session-token --duration-seconds 3600 --serial-number $mfa_arn --token-code $mfa_code'



