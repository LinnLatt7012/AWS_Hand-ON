cd ./resume-code/ && zip ../resume.zip * && cd ..

aws s3 cp resume.zip s3://sourecode-bucket/resume.zip

/workspaces/AWS_Hand-ON/E2Eweb/makeAmplifyApp Resume App
/workspaces/AWS_Hand-ON/E2Eweb/deployAmplifyApp d1lwffeqki4q2l master eu-north-1 resume.zip
