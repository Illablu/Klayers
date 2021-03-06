# Keith's Layers (Klayers)

[![Python 3.7](https://img.shields.io/badge/python-3.7-green.svg)](https://www.python.org/downloads/release/python-375/)  [![Python 3.8](https://img.shields.io/badge/python-3.8-green.svg)](https://www.python.org/downloads/release/python-380/)

[![Language grade: Python](https://img.shields.io/lgtm/grade/python/g/keithrozario/Klayers.svg?logo=lgtm&logoWidth=18)](https://lgtm.com/projects/g/keithrozario/Klayers/context:python)


A collection of AWS Lambda Layers for Python3.7 & Python3.8

# Python Packages

The following PyPi packages are available for both Python3.7 & Python3.8 unless otherwise stated:

* aiobotocore
* aiodns (Python3.7 only)
* aiohttp
* ansible
* aws-lambda-powertools (Python3.8 only)
* arrow
* aws-xray-sdk
* bcrypt
* beautifulsoup4
* boltons
* boto3
* construct
* dynamodb-encryption-sdk (Python3.8 only)
* elasticsearch
* envelopes
* ffmpeg-python
* flashtext
* google-auth
* google-auth-oauthlib
* graphene (Python3.7 only)
* grequests (Python3.7 only)
* grpcio
* gspread
* idna
* itsdangerous
* kafka-python
* nltk
* numpy
* opencv-python-headless
* openpyxl
* pandas
* parliament (Python3.8 only)
* Pillow
* pulp
* pycryptodome (Python3.8 only)
* PyJWT
* pymongo
* PyMUPDF
* PyMySQL
* PyNaCl
* pyOpenSSL
* pyparsing
* pyqldb
* pytesseract
* python-docx
* python-Levenshtein
* pytz
* PyYAML
* reportlab (Python3.8 only)
* requests
* scipy (Python3.7 only)
* simplejson
* spacy
* SQLAlchemy
* textdistance
* tinydb
* tldextract

# Layer List

List of all layer version arns are available by region here:
 * [Python3.7](deployments/python3.7/arns)
 * [Python3.8](deployments/python3.8/arns)

# Status of layers

[![Updates](https://pyup.io/repos/github/keithrozario/Klayers/shield.svg)](https://pyup.io/repos/github/keithrozario/Klayers/)

Click on badge above to see the specific package version of the latest builds.

Layers are built with the latest package version (available on PyPI) every Monday 2am UTC.

# Using the Layers

You can either set one of the ARNs below as a layer in your function. Or download the layer and deploy a copy into your account.

## Set ARN as layer

Currently only the following regions have the layers deployed, use the arn to include layer into your lambda function.

* us-east-1, US East (N. Virginia)
* us-east-2, US East (Ohio)
* us-west-1, US West (N. California)
* us-west-2, US West (Oregon)
* ca-central-1, Canada (Central)
* eu-central-1, EU (Frankfurt)
* eu-west-1, EU (Ireland)
* eu-west-2, EU (London)
* eu-west-3, EU (Paris)
* eu-north-1, EU (Stockholm)
* ap-northeast-1, Asia Pacific (Tokyo)
* ap-northeast-2, Asia Pacific (Seoul)
* ap-southeast-1, Asia Pacific (Singapore)
* ap-southeast-2, Asia Pacific (Sydney)
* ap-south-1, Asia Pacific (Mumbai)
* sa-east-1, South America (São Paulo)
* ap-east-1, Asia Pacific (Hong Kong)
* me-south-1, Middle East (Bahrain)

## Download copy of layer

* Use the `Get Layer Version by ARN` in [python](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/lambda.html#Lambda.Client.get_layer_version_by_arn) or [bash](https://docs.aws.amazon.com/cli/latest/reference/lambda/get-layer-version-by-arn.html) command which will provide an S3 location to download the layer as a zip. *Note: You can only get layers from the specific region your awscli is configured for, otherwise you'll get a `AccessDeniedException` error. In python, setup the boto3 client for the same region as the arn you're getting.*

## Layer expiry

Some layer versions will have a `time_to_live` field. This is the date for when the layers will be deleted.

All functions deployed with a layer will still work indefinitely, but you won't be able to deploy new functions referencing a deleted layer version.

## Binaries

Special hand-crafted binaries for layers. These layers are not automatically built, and hence slower update cycles, and will only work with python3.7 functions as the underlying OS is Amazon Linux 1.

| Package        | ARN                                                                             | Version    |         
| :------------- |:------------------------------------------------------------------------------- | ---------- | 
| tesseract      | arn:aws:lambda:\<*region*>:113088814899:layer:Klayers-python37-tesseract:1      | 4.1.0-rc1<sup>1</sup>|
| pip            | arn:aws:lambda:\<*region*>:113088814899:layer:Klayers-python37-pip:2            | 19.2.1     |
| netcat         | arn:aws:lambda:\<*region*>:113088814899:layer:Klayers-python37-netcat:2         | 0.7.1<sup>2</sup>|

<sup>1</sup> Includes leptonica-1.76.0, libjpeg 6b (libjpeg-turbo 1.2.90) : libpng 1.2.49 : libtiff 4.0.3 : zlib 1.2.8 : libwebp 0.3.0

<sup>2</sup> netcat-traditional with the -e option -- compiled for 64-bit to run on AWS Lambda

# Architecture Diagram

Diagram is still pretty draft will add more details later!

![Screenshot](documentation/Klayers-Architecture.png)

# Special Thanks

[Chahna107](https://github.com/chahna107) for adding tesseract config files into the tesseract layer.