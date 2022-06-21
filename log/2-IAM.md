# IAM: Users & Groups

### 1. IAM:

- IAM = Identity and Access Manangement, global service
- root account created by default, shouldn't be used or shared
- Users are people within your organizationm, and can be grouped
- Groups only contain users, not other groups
- Users don't have to belong to a group, and user can belong to multiple group

## IAM: Permissions

- Users or Groups can be assigned JSON documents called policies

```JSON
 {
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": "ec2: Describe*",
            "Resource": "*"
        },
        {
            "Effect": "Allow",
            "Action": "elasticloadbalancing:Describe*",
            "Resource": "*"
        },
        {
            "Effect": "Allow",
            "Action": [
                "cloudwatch:ListMetrics",
                "cloudwatch:GetMetricStatistics",
                "cloudwatch:Describe*"
            ],
            "Resource": "*"
        }
    ]
 }
```

- These policies define the permissions of the users
- In AWS you apply the least privilege principle: don't give more permissions then a user needs

---

## IAM: Personal Note for IAM

- Access User Type:

  1. Access key: Enalbes an access key ID and secret access key for the AWS API, CLI, SDK, and other development tools

  2. password: Enables a password that allows users to sign-in to the AWS management console
     d

- Policies inheritance

  1. Inline policy can be created for who is not included the group user

- Policies Structure

  ```JSON
  {
    "Version":"2012-10-17", // 1.
    "Id": "S3-Account-Permissions", // 2.
    "Statement":[{ // 3.
        "Sid":"1",
        "Effect":"Allow",
        "Principal":{
            "AWS":["arn:aws:iam::123456789012:root"]
        },
        "Action":[
            "s3:GetObject",
            "s3:PutObject",
        ],
        "Resource":["arn:aws:s3:::mybucket*"]
    }]
  }
  ```

- 1. Version: policy language version, always include"2012-10-17"
- 2. Id: an identifer for the policy(optional)
- 3. Statement: one or more individual statements(required)
     - Sid: an identifer for the statement(optional)
     - Effect: whether the statement allows or denies access(Allow or Deny)
     - Principal: account/user/role to which this policy applied to
     - Action: list of actions this policy allows or denies
     - Resource: list of resources to which the actions applied to
     - Condition: conditions for when this policy is in effect(optional)

- Multi Factor Authentication( MFA )
  1. Users have access to your account and can possibly change configurations or delete resources in your aws account
  2. You want to protect your Root Accounts and Iam users,
     use MFA(password + security device you own)
