# README

A CloudFormation template for a stack that has a Lambda watch an S3 location
and send any uploads to Rekognition's video face detection, then writes the
Rekognition output back to S3 with a second Lambda.

This template is not currently able to use an existing S3 bucket, the bucket
must be created by this template.


## Usage
### Parameters
#### BucketName
    Description: S3 bucket for video and output files
    Type: String
    Default: emotionrecognition
#### InputPrefix
    Description: Path to watch for input video files
    Type: String
    Default: videos
#### OutputPrefix
    Description: Path to write Rekognition output into
    Type: String
    Default: face_detection_output

### CLI command
``` shell
aws cloudformation create-stack \
    --template-body file://s3-rekognition-template.yaml \
    --capabilities=CAPABILITY_IAM \
    --stack-name <stackname> \
    --parameters ParameterKey=BucketName,ParameterValue=<bucketname> \
                 ParameterKey=InputPrefix,ParameterValue=<inputprefix> \
                 ParameterKey=OutputPrefix,ParameterValue=<outputprefix>
```
