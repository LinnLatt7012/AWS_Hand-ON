cd ./resume-code/ && zip ../resume.zip * && cd ..

aws s3 cp resume.zip s3://sourecode-bucket/resume.zip

/workspaces/AWS_Hand-ON/E2Eweb/makeAmplifyApp Resume App
/workspaces/AWS_Hand-ON/E2Eweb/deployAmplifyApp d1lwffeqki4q2l master eu-north-1 resume.zip


```sh
 aws s3 rm s3://linnlatt.info --recursive
 aws s3 rb s3://linnlatt.info
 aws s3 mb s3://resume.linnlatt.info --region us-west-2
 aws s3 cp resume-code/ s3://resume.linnlatt.info --recursive
```