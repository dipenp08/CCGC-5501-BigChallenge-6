CloudFoxable Challenge 1 - Do This First

Overview
The "Do This First" CloudFoxable challenge introduces fundamental cloud security enumeration techniques. The objective is to log in using AWS credentials, identify accessible cloud resources, and retrieve the first flag. 
Methodology
Step 1: Setup AWS CLI
The challenge provided AWS credentials which I initialized with:
aws configure
When I entered the Access Key and Secret Key, it was successful in its authentication.
To ensure that my CLI was working, I issued the following command:
aws sts get-caller-identity

Step 2: Listing IAM User
To verify that the IAM user whose credentials I employed was present, I issued:
aws iam list-users
This ensured that I did have an IAM user account.

Step 3: Confirming Permissions
To observe what permissions existed, I listed attached policies:
aws iam list-attached-user-policies --user-name non_root_user
The output verified read access to S3.

Step 4: Listing S3 Buckets
S3 read access confirmed, I listed the existing S3 buckets:
aws s3 ls
There was a bucket called cloudfoxable-flag-bucket. Listing its contents:
aws s3 ls s3://cloudfoxable-flag-bucket
unfolded to show a file called flag.txt.

Step 5: Obtaining the Flag
Obtaining the flag, I executed:
aws s3 cp s3://cloudfoxable-flag-bucket/flag.tx

The received flag was:
FLAG{congrats_you_are_now_a_terraform_expert_happy_hunting}

Conclusion
This challenge cemented fundamental AWS enumeration principles, such as IAM policy auditing and S3 bucket enumeration. Gaining the first flag essentially set the stage for more substantial privilege escalation in the subsequent challenges.
