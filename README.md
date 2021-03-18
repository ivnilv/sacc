# SACC 
**S**mart **A**WS **C**li **C**onfig - `~/.aws/credentials` generator for lazy devs

`sacc` is a tool built out of the necessity to get new AWS session tokens every 36 (maximum) hours. 

Usage:

![usage](./sacc.svg)
<img src="./sacc.svg">

Requirements:
- bash 3.2+
- [jq](https://github.com/stedolan/jq)
- [aws-cli](https://github.com/aws/aws-cli)
