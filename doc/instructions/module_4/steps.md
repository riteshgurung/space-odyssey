- Use manifest to provision the function for ```trigger-logging-CloudTrail-bucket```

```bash
$ cd workshop/
workshop $ cp manifest.yml.step-3.example manifest.yml
workshop $ rake process_manifest
workshop $ rake describe_manifest_status
workshop $ rake get_stack_build_status["trigger-logging-CloudTrail-bucket"]
logging, CloudTrail-bucket: CREATE_COMPLETE

workshop $ rake get_cf_stack_status["CloudTrail-bucket","logging"]
logging, CloudTrail-bucket: CREATE_COMPLETE

```

- Use manifest to provision the function for ```create-CloudTrail-bucket-policy```

```bash
workshop $ cp manifest.yml.step-4.example manifest.yml
workshop $ rake process_manifest
workshop $ rake describe_manifest_status

```
           
- Use manifest to provision the function for ```trigger-all-CloudTrail```

```bash
workshop $ cp manifest.yml.step-5.example manifest.yml
workshop $ rake process_manifest
workshop $ rake describe_manifest_status

```   

- Navigate to the logging account and verify that the bucket is created and a bucket policy is applied that allows other accounts to write CloudTrail logs to the bucket

```bash
workshop $ rake navigate["logging"]

# Copy the URL and use the AWS Management console to verify

```

- Navigate to some functional account and verify that CloudTrail is provisioned and is logging to the common bucket

```bash
workshop $ rake navigate["dione"]

# Copy the URL and use the AWS Management console to verify

```

Move on to [module 5](../module_5/steps.md), or back up to [overview](../overview.md)