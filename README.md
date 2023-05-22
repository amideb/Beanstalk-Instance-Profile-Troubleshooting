# Beanstalk-Instance-Profile-Troubleshooting
This repository is dedicated to providing solutions and guidance specifically related to managing instance profiles in AWS Elastic Beanstalk. It covers topics such as creating and configuring instance profiles, assigning necessary policies, and resolving common issues associated with instance profiles in Elastic Beanstalk.

<br>

![vlcsnap-2023-05-22-10h59m02s928](https://github.com/amideb/Beanstalk-Instance-Profile-Troubleshooting/assets/57451228/4ef784c9-03fe-4f48-99cb-90d01b6c0926)

<br>

## Demonstration Video

A detailed walkthrough of the setup and deployment process is available on YouTube. Click on the image below to watch the video.
<br>
**Link of the Video:** https://youtu.be/GxUi6MsXZPM

<br>


## Step 1: Open Elastic Beanstalk console

- First, open the [Elastic Beanstalk console](https://console.aws.amazon.com/elasticbeanstalk/).
- Click on "Create Application"

<br>

![Screenshot 2023-05-22 at 11 28 41 AM](https://github.com/amideb/Beanstalk-Instance-Profile-Troubleshooting/assets/57451228/0bc76619-a29e-4379-afaa-472fa72bc993)

<br>


## Step 2: Configure the new environment

On the "Create a new environment" page, do the following:

-   For "Application Name", type `my-first-elasticbeanstalk-application`.
-   Keep "Environment name" and "Domain" as default or you can modify it according to your needs.
-   For "Platform", choose "Python".

<br>

![Screenshot 2023-05-22 at 11 01 40 AM](https://github.com/amideb/Beanstalk-Instance-Profile-Troubleshooting/assets/57451228/90de27da-7331-42e6-bc54-2ec625684495)

<br>

![Screenshot 2023-05-22 at 11 02 35 AM](https://github.com/amideb/Beanstalk-Instance-Profile-Troubleshooting/assets/57451228/6f668efa-0081-420f-aaa6-b9153a449191)

<br>

![Screenshot 2023-05-22 at 11 03 43 AM](https://github.com/amideb/Beanstalk-Instance-Profile-Troubleshooting/assets/57451228/6dcec3b5-deeb-4540-b16e-3187deef0971)

<br>

![Screenshot 2023-05-22 at 11 04 04 AM](https://github.com/amideb/Beanstalk-Instance-Profile-Troubleshooting/assets/57451228/f7921742-757a-4ed6-b8d7-153563d1967a)

<br>

## Step 3: Configure Service Access

In "Configure Service Access" step,
-   Choose "Create and use new service role".
-   For "Service role name", type `aws-elasticbeanstalk-service-role`.
- Now, Check the "EC2 Instance Profile and click refresh, If you have created any EC2 Instance profile before with proper permission it will show that, you can select that and click on next. And skip the next step, jump to **Step 4**
- Otherwise Open IAM in a new tab and follow the next **Step 3A**

<br>

![Screenshot 2023-05-22 at 11 04 57 AM](https://github.com/amideb/Beanstalk-Instance-Profile-Troubleshooting/assets/57451228/ec826f92-653a-4e77-a5bd-4278fd32ebc6)

<br>

## Step 3A: Create a new IAM Role

- Open the IAM Console in your AWS Management Console.
- In the navigation pane, choose "Roles", and then "Create role".
- In Trusted entity type Select `AWS Service` .
- Choose the "EC2" use case, and then "Next: Permissions".
- In the Attach permissions policies page, type "AWSElasticBeanstalk" in the search box.
- Check the boxes for "AWSElasticBeanstalkWebTier", "AWSElasticBeanstalkWorkerTier", and "AWSElasticBeanstalkMulticontainerDocker".
- Click "Next: Tags" to optionally add tags to the role.
- Click "Next: Review".
-  For Role name, type "aws-elasticbeanstalk-ec2-role" and then click "Create role".

<br>

![Screenshot 2023-05-22 at 11 05 38 AM](https://github.com/amideb/Beanstalk-Instance-Profile-Troubleshooting/assets/57451228/ee34b838-ba4b-49d2-a524-96d61ad2cc94)

<br>

![Screenshot 2023-05-22 at 11 06 05 AM](https://github.com/amideb/Beanstalk-Instance-Profile-Troubleshooting/assets/57451228/a41d998e-18da-483f-9d4f-49023b4a4404)

<br>

![Screenshot 2023-05-22 at 11 06 52 AM](https://github.com/amideb/Beanstalk-Instance-Profile-Troubleshooting/assets/57451228/57a9d04b-0eca-45e4-920c-24f5bb562108)

<br>

![Screenshot 2023-05-22 at 11 07 20 AM](https://github.com/amideb/Beanstalk-Instance-Profile-Troubleshooting/assets/57451228/17bf9c3f-2a08-4e35-99ce-d291355c19c0)

<br>


![Screenshot 2023-05-22 at 11 07 59 AM](https://github.com/amideb/Beanstalk-Instance-Profile-Troubleshooting/assets/57451228/faf17db7-d124-4cba-abff-f9916639ff26)

<br>

![Screenshot 2023-05-22 at 11 08 22 AM](https://github.com/amideb/Beanstalk-Instance-Profile-Troubleshooting/assets/57451228/e7dc9b9b-c3d4-481f-a261-e2a2269f633d)

<br>


![Screenshot 2023-05-22 at 11 08 58 AM](https://github.com/amideb/Beanstalk-Instance-Profile-Troubleshooting/assets/57451228/e16f6bfc-5e8f-4213-a0be-b225c7763af4)

<br>

## Step 4: Configure Service Access after creating IAM Role

Go back to Configure Service Access  page

-   Refresh "EC2 Instance Profile"
-   Make sure "IAM instance profile" is set to `aws-elasticbeanstalk-ec2-role`.


<br>


![Screenshot 2023-05-22 at 11 09 44 AM](https://github.com/amideb/Beanstalk-Instance-Profile-Troubleshooting/assets/57451228/edec9838-b2e2-424c-a433-71701b0851ad)

<br>

![Screenshot 2023-05-22 at 11 10 21 AM](https://github.com/amideb/Beanstalk-Instance-Profile-Troubleshooting/assets/57451228/d06de6fc-46bf-4e95-9ff6-3923631334e7)

<br>

![Screenshot 2023-05-22 at 11 11 10 AM](https://github.com/amideb/Beanstalk-Instance-Profile-Troubleshooting/assets/57451228/24d80c4b-95b0-42c9-aa1b-0f0442a2c599)

<br>

## Step 5: Configure Capacity

Click on the "Capacity" category and do the following:

-   For "Environment type", choose "Load balanced".
-   For "Min instances", type `1`.
-   For "Max instances", type `2`.

<br>


![Screenshot 2023-05-22 at 11 12 02 AM](https://github.com/amideb/Beanstalk-Instance-Profile-Troubleshooting/assets/57451228/6608d1ed-cec3-40e6-b8b4-ccccec3ddd64)

<br>

![Screenshot 2023-05-22 at 11 12 51 AM](https://github.com/amideb/Beanstalk-Instance-Profile-Troubleshooting/assets/57451228/fbb4ba78-6116-4377-a1b5-aa5b869480ef)

<br>

![Screenshot 2023-05-22 at 11 13 27 AM](https://github.com/amideb/Beanstalk-Instance-Profile-Troubleshooting/assets/57451228/78af24f6-5a93-4bbc-9694-110b1c1b5c8f)

<br>

## Step 6: Create the environment

Click "Submit". AWS Elastic Beanstalk will then start creating the application. This may take a few minutes.

<br>

![Screenshot 2023-05-22 at 11 14 10 AM](https://github.com/amideb/Beanstalk-Instance-Profile-Troubleshooting/assets/57451228/72a1cca4-2356-4eca-bb4c-2abc45e521fd)

<br>

![Screenshot 2023-05-22 at 11 14 35 AM](https://github.com/amideb/Beanstalk-Instance-Profile-Troubleshooting/assets/57451228/4793c634-44ae-4a9c-add9-9475395b65cd)

<br>

## Step 7: Open the Application

After the environment is created, Elastic Beanstalk provides you with a URL to your website. If you used the sample application, this will be a simple web page that's served by a Python application running on your environment.

<br>


![Screenshot 2023-05-22 at 11 15 05 AM](https://github.com/amideb/Beanstalk-Instance-Profile-Troubleshooting/assets/57451228/9c35b468-e98e-4000-b936-b8d976e7edec)

<br>

## Congratulations! 🎉

You've successfully created your Python application on Amazon Elastic Beanstalk. This is a significant step forward in your cloud journey. Your my-first-elasticbeanstalk-application is now up and running, encapsulating best practices of scalability, load balancing, and automated management.

This achievement not only highlights your comprehension of AWS services, but it also showcases your capability to manage and deploy scalable web applications.

Keep exploring, keep learning, and continue making great strides in the world of cloud computing!

Remember, each step you take is bringing you closer to becoming a proficient cloud developer. Enjoy your success and happy coding!
