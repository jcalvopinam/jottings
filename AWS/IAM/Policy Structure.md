# Format
| Description                                      | Mandatory | Field                          |
| ------------------------------------------------ | --------- | ------------------------------ |
| Language version, it's always 2012-10-17         | true      | "Version": "2012-10-17"        |
| Policy identifier                                | false     | "Id": "S3-Account-Permissions" |
| One or more individual declaration               | true      | "Statement": []                |
| Identifier declaration                           | false     | "Sid": "1"                     |
| If it is allow or denied access                  | true      | "Effect": "Allow"              |
| Account/User/Role which the policy applies       | true      | "Principal": {}                |
| List of actions that the policy allows or denied | true      | "Action": []                   |
| List of resources to which the actions apply     | true      | "Resource": []                 |
| Condition when this policy apply                 | false     | "Condition": ""                |

- Sample
```json
{
	"Version": "2012-10-17",
	"Id": "S3-Account-Permissions",
	"Statement": [
		{
			"Sid": "1",
			"Effect": "Allow",
			"Principal": {
				"AWS": ["arn:aws:iam::641241459225:root"]
			},
			"Action": [
				"s3:GetObject",
				"s3:PutObject"
			],
			"Resource": ["arn:aws:s3:::mybucket/*"]
		}
	]
}
```