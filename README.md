# **NBA Game Day Notifications** / **Sports Alerts System**

## **Project Overview**
Stay on top of the game!This project is a **real time NBA Game Day Notifications System** that delivers live score updates straight to your inbox or phone via **SMS/Email**. Built using **AWS Services** and **NBA APIs**, it showcases how to design a secure, scalable, and automated cloud-based notification system. Perfect for sports enthusiasts and techies exploring AWS and Python-based solutions.

---

## **Key Features**
- **Live Score Updates**: Fetches live NBA scores from the **NBA Game API**.
- **Real-Time Notifications**: Sends formatted updates via **Amazon SNS** (SMS/Email).
- **Automated Scheduling**: Uses **Amazon EventBridge** for regular updates.
- **Security-Focused Design**: Implements the **principle of least privilege** for AWS IAM roles.

---

## **Tech Stack**
- **Cloud Provider**: AWS
- **Core Services**: Amazon SNS, AWS Lambda, EventBridge
- **API**: NBA Game API from [SportsData.io](https://sportsdata.io/)
- **Language**: Python 3.x
- **Security**: Custom IAM policies for secure integration

---

## **Architecture Overview**
![nba_API](https://github.com/user-attachments/assets/5e19635e-0685-4c07-9601-330f7d1231f9)

- **Amazon EventBridge**: Automates scheduling of the Lambda function to fetch live game data.
- **AWS Lambda**: Executes the notification logic in real time.
- **Amazon SNS**: Sends game day updates to users via SMS and Email.

---

## **Project Structure**
```bash
game-day-notifications/
├── src/
│   ├── gd_notifications.py          # Main Lambda function code
├── policies/
│   ├── gd_sns_policy.json           # SNS publishing permissions
│   ├── gd_eventbridge_policy.json   # EventBridge to Lambda permissions
│   └── gd_lambda_policy.json        # Lambda execution role permissions
├── .gitignore
└── README.md                        # Project documentation
```
---

## **Getting Started**

1. ### **Prerequisites**
   - **NBA API Key:** Get your free API key from [SportsData.io](https://sportsdata.io/)
   - **AWS Account:** Familiarity with AWS services and Python is a plus!
   
2. ### **Clone the Repository**
```bash
git clone git@github.com:adesegunasunmo/Game-Day-Notifications.git
cd Game-Day-Notifications
```
---
## **Step-by-Step Setup**

### **Create an SNS Topic**
1. Open the AWS Management Console.
2. Navigate to the SNS service.
3. Click Create Topic and select Standard as the topic type.
4. Name the topic (e.g., gd_topic) and note the ARN.
5. Click Create Topic.

### **Add Subscriptions to the SNS Topic**
1. After creating the topic, click on the topic name from the list.
2. Navigate to the Subscriptions tab and click Create subscription.
3. Select a Protocol: For Email:
  - Choose Email.
  - Enter a valid email address.
  - For SMS (phone number):
  - Choose SMS.
  - Enter a valid phone number in international format (e.g., +1234567890).

4. Click Create Subscription.
5. If you added an Email subscription:
- Check the inbox of the provided email address.
- Confirm the subscription by clicking the confirmation link in the email.
6. For SMS, the subscription will be immediately active after creation.

### **Create an SNS Topic Policy**
1. Open the IAM service in the AWS Management Console.
2. Navigate to Policies → Create Policy.
3. Click JSON and paste the JSON policy from gd_sns_policy.json file
4. Replace REGION and ACCOUNT_ID with your AWS region and account ID.
5. Click Next: Tags (you can skip adding tags).
6. Click Next: Review.
7. Enter a name for the policy (e.g., gd_sns_policy).
8. Review and click Create Policy.

### **Create an IAM Role for Lambda**
1. Open the IAM service in the AWS Management Console.
2. Click Roles → Create Role.
3. Select AWS Service and choose Lambda.
4. Attach the following policies:
- SNS Publish Policy (gd_sns_policy) (created in the previous step).
- Lambda Basic Execution Role (AWSLambdaBasicExecutionRole) (an AWS managed policy).
5. Click Next: Tags (you can skip adding tags).
6. Click Next: Review.
7. Enter a name for the role (e.g., gd_role).
8. Review and click Create Role.
9. Copy and save the ARN of the role for use in the Lambda function.

  ![image](https://github.com/user-attachments/assets/c31d21a3-285e-4c3f-9f19-f2387e4c153d)


### **Deploy the Lambda Function**
1. Open the AWS Management Console and navigate to the Lambda service.
2. Click Create Function.
3. Select Author from Scratch.
4. Enter a function name (e.g., gd_notifications).
5. Choose Python 3.x as the runtime.
6. Assign the IAM role created earlier (gd_role) to the function.
7. Under the Function Code section:
- Copy the content of the src/gd_notifications.py file from the repository.
- Paste it into the inline code editor.
8. Under the Environment Variables section, add the following:
- NBA_API_KEY: your NBA API key.
- SNS_TOPIC_ARN: the ARN of the SNS topic created earlier.
9. Click Create Function.


### **Automate with Eventbridge**
1. Navigate to the Eventbridge service in the AWS Management Console.
2. Go to Rules → Create Rule.
3. Select Event Source: Schedule.
4. Set the cron schedule for when you want updates (e.g., hourly).
5. Under Targets, select the Lambda function (gd_notifications) and save the rule.

![image](https://github.com/user-attachments/assets/3d28aca6-ea9c-4e2d-858b-a42d991262a3)

![image](https://github.com/user-attachments/assets/8953d740-e83b-4818-ae08-d746fbc8a3be)



### **Testing the System**
- Open the Lambda function in the AWS Management Console.
- Create a test event to simulate execution.
- Run the function and check CloudWatch Logs for errors.
- Verify that SMS notifications are sent to the subscribed users.

![image](https://github.com/user-attachments/assets/a8e8e105-89f7-43fe-b358-70958a6d2636)



### **What I Learned**
- Setting up a cloud-based notification system with AWS SNS and Lambda.
- Best practices for securing AWS resources with IAM..
- Integrating third-party APIs into serverless workflows.
- Automating tasks with EventBridge and Lambda.
---

### **Future Enhancements**
- Add NFL score alerts for extended functionality.
- Personalize notifications by storing user preferences (e.g., favorite teams) in **DynamoDB**.
- Build a web-based dashboard for subscription management and live scores.
---
### **Contribution**
Contributions are welcome! Feel free to fork the repo, make your improvements, and create a pull request. Let’s make this project even better!
