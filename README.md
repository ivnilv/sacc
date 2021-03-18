# SACC 
**S**mart **A**WS **C**li **C**onfig - `~/.aws/credentials` generator for lazy devs

`sacc` is a tool built out of the necessity to get new AWS session tokens every 36 (maximum) hours. 

The tool will use your AWS access key and secret to request new session token from the AWS Security Token Service (AWS STS).

Usage:

![usage](./sacc.svg)

Prerequisites:

- You will need an existing AWS account
- MFA (Multi-factor authentication) device linked to your account
- AWS API Access key generated from your account

Requirements:
- bash 3.2+
- [jq](https://github.com/stedolan/jq)
- [aws-cli](https://github.com/aws/aws-cli)

Installation:

Clone the repository locally:
```
$ 	
```
Install a link to your `$PATH`:
```
$ sudo ln -s ~/sacc/sacc /usr/local/bin/
```