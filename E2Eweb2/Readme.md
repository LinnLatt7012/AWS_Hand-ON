aws s3 cp s3://ttt-wildrydes/wildrydes-site ./ --recursive

aws codecommit create-repository --repository-name MyNewRepository --repository-description "My new repository description"

aws amplify create-app --name "myAmplifyApp" --platform WEB --source-code-url "s3://your-s3-bucket-name/app.zip" --region us-west-2
