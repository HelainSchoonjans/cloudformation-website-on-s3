## Hosting a static website on S3

Install the Amazon Cli and run the following command:

    aws configure
	
to log in and save your credentials.

## Infrastructure

To build the infrastructure use the following command:

    aws cloudformation create-stack --region $MY_REGION --template-body file://$PWD/infrastructure.yml --stack-name my-app-name

To update the bucket:

    aws cloudformation update-stack --region $MY_REGION --template-body file://$PWD/infrastructure.yml --stack-name my-app-name

To destroy the infrastructure:

    aws cloudformation delete-stack --stack-name my-app-name

## Deployment

Upload the contents of the code/ folder into the bucket:
    
    aws s3 cp --acl public-read --recursive code/ s3://my-app-name/

## Troubleshooting

An HTTP Client raised and unhandled exception: unknown encoding: idna

    https://stackoverflow.com/questions/53144254/aws-cli-upload-failed-unknown-encoding-idna
