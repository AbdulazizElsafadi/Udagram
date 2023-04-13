# Pipeline Description:

## Orbs

Orbs contain basic recipes and reproducible actions. It includes the following:

1. node
2. eb (Elastic Beanstalk)
3. aws-cli

## Jobs

In this stage we have to main phases:

1. Continuous Integration
2. Hold
3. Continuous Delivery

### Continuous Integration:

In the CI, we have the following:

1. Install Dependencies of the front-end and the api. ` npm run frontend:install` ` npm run api:install`
2. Ensure the code follow the standard format by executing ` npm run lint` command
3. Build the Front-end and the api to insure the new change didn't break the application. `npm run frontend:build` ``npm run api:build`

### Hold:

Hold is just a manual approval to deploy the application (which is why it's considered continuous delivery NOT deployment)

### Continuous Delivery:

In the CD, we have the following:

1. Install dependencies of both applications (front-end and back-end)
2. Build both applications
3. deploy both applications.

Note, In the deployment:
We deploy the front-end in the s3 bucket by running:
` aws s3 cp --recursive --acl public-read ./www s3://bucketName/`
`aws s3 cp --acl public-read --cache-control="max-age=0, no-cache, no-store, must-revalidate" ./www/index.html s3://bucketName/`

## Workflows:

workflows was provided by Udacity in the starter code. It orders the jobs of the pipeline. and the create the manual approval for production
