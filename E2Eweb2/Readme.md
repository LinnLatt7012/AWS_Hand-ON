aws s3 cp s3://ttt-wildrydes/wildrydes-site ./ --recursive
```sh 
cd web
zip -r ../web.zip *
aws s3api create-bucket \
--bucket sourecode-bucket \
--create-bucket-configuration="LocationConstraint=eu-north-1"
aws s3 cp web.zip s3://sourecode-bucket/app.zip
```

Step 1: To create app with name as appName. aws amplify create-app --name dry-web-app --region eu-north-1

Step 2: To create branch. 
```sh
aws amplify create-branch --region eu-north-1 --app-id "d7a05orkpgv8p" --branch-name "master"
```

Step 3: To deploy. 
```sh 
aws amplify start-deployment --region eu-north-1 --app-id "d7a05orkpgv8p" --branch-name "master" --source-url "s3://sourecode-bucket/app.zip" --query jobSummary.jobId --output text
```

Step 4: To verify deployment status, 
```sh 
aws amplify get-job --region eu-north-1 --app-id "d7a05orkpgv8p" --branch-name "master" --job-id "6" --query job.summary.status --output text
```

