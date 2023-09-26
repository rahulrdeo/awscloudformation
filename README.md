# awscloudformation
AWS Cloudformation Templates Created for Ease of Use
This AWS CloudFormation template creates an Amazon S3 bucket with a customizable name based on the input parameter `S3BucketName`. Here's a breakdown of what the template does:

1. **Parameters**: This section defines an input parameter named `S3BucketName`. The parameter type is set to `String`, and it has a description that indicates it's for specifying the name of the S3 bucket. The `AllowedPattern` constraint ensures that the bucket name follows the required pattern (starts with a letter and can contain letters, numbers, underscores, and hyphens).

2. **Resources**: This section defines the AWS resource that will be created when the CloudFormation stack is launched. In this case, it creates an S3 bucket with the logical name `SampleS3Bucket`.

   - **Type**: `AWS::S3::Bucket` specifies that an S3 bucket resource should be created.

   - **Properties**: The properties of the S3 bucket resource are configured as follows:

     - **BucketName**: This property specifies the name of the S3 bucket. It uses the `!Join` function to concatenate various strings together to form the bucket name. The bucket name is constructed as follows:
       - The value of `S3BucketName` (input parameter) is used as the base part of the bucket name.
       - The `!Select` and `!Split` functions are used to extract parts of the `AWS::StackId` (the unique identifier for the CloudFormation stack) and combine them with the `S3BucketName`.
       - The `!Ref AWS::Region` function is used to include the AWS region in the bucket name.

   The resulting bucket name is a combination of the input parameter `S3BucketName`, parts of the stack ID, and the AWS region. This can create a unique bucket name within the constraints of S3 bucket naming rules.

In summary, this CloudFormation template allows you to create an S3 bucket with a name that is partially based on the input parameter `S3BucketName`, the stack ID, and the AWS region. The bucket name is generated to ensure uniqueness and compliance with S3 naming rules.
