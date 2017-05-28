# MoonMail Tips
When using [MoonMail](https://github.com/microapps/MoonMail), the documentation had some gaps. Below are some tips to help get to the next step.

## Help
* MoonMail Wiki: https://github.com/microapps/MoonMail/wiki
* StackOverflow: http://stackoverflow.com/questions/tagged/moonmail?sort=votes&pageSize=50
* Gitter: https://gitter.im/microapps/MoonMail

## Setup

### Serverless
MoonMail is deployed using the 0.x verison of serverless. This means if you have the 1.x version installed, you'll need to uninstall it and install the 0.x version. For instance:
```
npm uninstall -g serverless
npm install -g serverless@0.5.6
```

### Python
MoonMail uses node-gyp, which only runs in Python 2.7. If you have 3.5 installed and first on the path, then it won't work.

### Node Modules
MoonMail uses a handful of modules not defined in the package. Here are a few to make sure you have installed:
```
npm install emitter
npm install nodent --save
npm install js-beautify --save
```

## Configuration

### S3 Bucket Settings
S3 buckets are global, so be sure to edit the `___.json` file to add in unique bucket names
```
{
    ...,
    ...
}
```

### Default Settings
Be sure to add these to your `_meta/variables/s-variables-<stage>-<region>.json` file
```
{
    ...,
    "defaultApiKey": "api-key", 
    "defaultApiSecret": "api-secret", 
    "defaultRegion": "default-region",
    "defaultEmailAddress": "email-address"
}
```

### DynamoDB Settings
You'll need to add some variables to define the number of read and write capacity units for the DynamoDB tables and indexes. Add these to your `_meta/variables/s-variables-<stage>-<region>.json` file
```
{
    ...,
    "clicksRCU":2, 
    "clicksReportRCU":2, 
    "clicksReportWCU":2, 
    "clicksWCU":2, 
    "defaultRCU":2, 
    "defaultWCU":2, 
    "opensRCU":2, 
    "opensReportRCU":2, 
    "opensReportWCU":2, 
    "opensWCU":2, 
    "recipientsRCU":2, 
    "recipientsWCU":2, 
    "scheduledAtIndexRCU":2, 
    "scheduledAtIndexWCU":2, 
    "scheduledCampaignsRCU":2, 
    "scheduledCampaignsWCU":2, 
    "sentEmailsRCU":2, 
    "sentEmailsWCU":2
}
```

### Ignore These
Apparently the below can be ignored. The variables are set when running `serverless resources deploy`. 
```
Serverless: WARNING: This Variable is not defined: updateCampaignTopicARN
Serverless: WARNING: This Variable is not defined: attachRecipientsCountTopicARN
Serverless: WARNING: This Variable is not defined: precompileCampaignTopicARN
Serverless: WARNING: This Variable is not defined: opensStreamName
Serverless: WARNING: This Variable is not defined: clicksStreamName
Serverless: WARNING: This Variable is not defined: unsubscribedRecipientTopicARN
Serverless: WARNING: This Variable is not defined: unsubscribedCallbackUrl
Serverless: WARNING: This Variable is not defined: attachRecipientsCountTopicARN
Serverless: WARNING: This Variable is not defined: updateCampaignTopicARN
Serverless: WARNING: This Variable is not defined: clicksStreamARN
Serverless: WARNING: This Variable is not defined: attachRecipientsTopicARN
Serverless: WARNING: This Variable is not defined: updateCampaignTopicARN
Serverless: WARNING: This Variable is not defined: precompileEmailTopicARN
Serverless: WARNING: This Variable is not defined: attachListRecipientsTopicARN
Serverless: WARNING: This Variable is not defined: sendEmailsTopicARN
Serverless: WARNING: This Variable is not defined: updateCampaignTopicARN
Serverless: WARNING: This Variable is not defined: attachSenderTopicARN
Serverless: WARNING: This Variable is not defined: recipientsImportS3BucketName
Serverless: WARNING: This Variable is not defined: updateListImportStatusTopicARN
Serverless: WARNING: This Variable is not defined: recipientsTableStreamARN
Serverless: WARNING: This Variable is not defined: sentEmailsTopicARN
Serverless: WARNING: This Variable is not defined: clicksStreamARN
Serverless: WARNING: This Variable is not defined: opensStreamARN
Serverless: WARNING: This Variable is not defined: sentEmailsTableStreamARN
Serverless: WARNING: This Variable is not defined: sendCampaignTopicARN
Serverless: WARNING: This Variable is not defined: sendEmailsTopicARN
Serverless: WARNING: This Variable is not defined: sentEmailsTopicARN
```

### Other Settings
Some other settings I'm not sure about yet so am ignoring for now. 
```
    "iotEndpoint"
    "redisEndpointAddress"
    "redisPassword"
    "unsubscribedCallbackUrl"
```

## Deployment

### Uglify-JS Errors
It appears you can ignore them if the deployment succeeds.
