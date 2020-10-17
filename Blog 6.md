# blog 6

## CloudTrail log analysis

CloudTrail logs help monitor events that occur on the AWS account. CloudTrail in itself is there to  enable governance, compliance, and operational and risk auditing of your AWS account, recording actions from AWS users, roles, or by an AWS service. In an event of Incident Response, these logs can be very useful to determine what kind of activities were performed by adversary, such as creating new users, adding users to admin group, exporting S3 databases, etc. While the CloudTrail logs are enabled by default, and furthermore can be used to view, search, download, archive, analyze, and respond to account activity across your AWS infrastructure. One way to respond to an incident is by exporting the logs into centralized log software such as Splunk. Let's start by looking into some particular types of calls that show in CloudTrail and and see how we can pivot around those to possibly find and identify details of intrusion.


### CloudTrail events


#### AddUserToGroup

```
{"Records": [{
    "eventVersion": "1.0",
    "userIdentity": {
        "type": "IAMUser",
        "principalId": "EX_PRINCIPAL_ID",
        "arn": "arn:aws:iam::123456789012:user/Alice",
        "accountId": "123456789012",
        "accessKeyId": "EXAMPLE_KEY_ID",
        "userName": "Alice",
        "sessionContext": {"attributes": {
            "mfaAuthenticated": "false",
            "creationDate": "2014-03-25T18:45:11Z"
        }}
    },
    "eventTime": "2014-03-25T21:08:14Z",
    "eventSource": "iam.amazonaws.com",
    "eventName": "AddUserToGroup",
    "awsRegion": "us-east-2",
    "sourceIPAddress": "127.0.0.1",
    "userAgent": "AWSConsole",
    "requestParameters": {
        "userName": "Bob",
        "groupName": "admin"
    },
    "responseElements": null
}]}
```
Here we can highlight **AddUserToGroup**, which is an event name associated with this log. We can see that IAM user by the name Alice is requesting to add another user by the name of Bob to the user group of **Admin**. This activity in its own is not particularly suspicious, but is certianly something to pay attention to; in most of cases, we would investigate on whether the user Bob is authorized to be an admin and whether the Alice is not the account that was compromised in order to pivot and create unsuspicious user account to be used later on. One should pay attention to the IP address of the user, whether it's a known IP associated with that user (sourceIPAddress) and time of the event (eventTime). 


#### Splunk

Splunk can be helpful to analyze patterns associated with logs. If you have over 5gb of logs, it is impossible to really understand what has happened. By quering user names, IP's, and event names you get to build a trail of events and get the understand of what happened.

