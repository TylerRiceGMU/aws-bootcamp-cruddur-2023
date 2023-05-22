# Week 0 — Billing and Architecture

## Required Homework/Tasks

### 1. Install and Verify AWS CLI
Below is the code used to install AWS CLI in Gitpod.
![Code used to install aws cli in gitpod](assets/aws%20cli%20install%20code.PNG)

Below is proof that the AWS CLI works and is connected to my AWS account.
![Get Caller Screenshot](assets/aws%20cli%20get%20caller%20identity.jpg)


### 2. Create a Billing Alarm
Below is a screenshot of the billing alarm I made in the AWS Management Console.
![Billing alarm screenshot](assets/billing%20alarm%20screenshot.PNG)
This alarm will trigger if the daily charges exceed $1.

### 3. Create a Budget
Below is a screenshot of two budgets I've made in the AWS Management Console.
![Budget screenshot](assets/Budgets%20screenshot.PNG)

### 4. Logical Architectural Design of Cruddur
![Logical Diagram of Cruddur](assets/Homework%20Diagram.png)

[Lucid Charts Share Link](https://lucid.app/lucidchart/a56b97e7-6b7f-43e6-b496-01e90f1e70dc/edit?viewport_loc=-530%2C-356%2C3328%2C1598%2C0_0&invitationId=inv_1a750180-4e62-40b5-bcd1-ee41af686a7b)
## Homework Challenges
Markdown syntax examples:
1. First item
2. Second item
3. Third item

- First item
- Second item
- Third item

How do I **bold** texts?

<https://www.markdownguide.org/basic-syntax/>


Code used in the AWS CLI to create a billing alarm once I've exceeded 80% of my budget.
```
[
    {
        "Notification": {
            "ComparisonOperator": "GREATER_THAN",
            "NotificationType": "ACTUAL",
            "Threshold": 80,
            "ThresholdType": "PERCENTAGE"
        },
        "Subscribers": [
            {
                "Address": "tylerrice9@gmail.com",
                "SubscriptionType": "EMAIL"
            }
        ]
    }
  ]
```
