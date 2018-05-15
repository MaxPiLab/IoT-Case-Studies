

# AWS and Raspberry Pi

## What is AWS?


## 

1. Turn on your Raspberry Pi and confirm you have an Internet connection.  

2. Sign in to the AWS Management Console and open the AWS IoT console at https://aws.amazon.com/iot. On the Welcome page, choose Get started.  

3. If this is your first time using the AWS IoT console, you see the Welcome to the AWS IoT Console page. In the left navigation pane, choose Manage to expand the choices, and then choose Things.  

4. On the page that says You don't have any things yet, choose Register a thing. (If you have created a thing before, choose Create.)  

A thing represents a device whose status or data is stored in the AWS Cloud. This stored status or data is called the device's shadow. The Device Shadow service maintains a shadow for each device connected to AWS IoT.  

1. Type a name for the thing, and then choose Create thing.  

2. On the Details page, choose Interact.  

3. Make a note of the REST API endpoint. You need this value later. Choose Security.  

4. Choose Create certificate. This generates an X.509 certificate and key pair.  

5. Create a working directory called deviceSDK where your files will be stored. Choose the links to download your public and private keys, certificate, and root CA and save them in the deviceSDK directory. Choose Activate to activate the X.509 certificate, then choose Attach a policy.  

6. Choose Create new policy.  

7. On the Create a policy page, in the Name field, type a name for the policy. In the Action field, type iot:*. In the Resource ARN field, type *. Select the Allow check box. This allows your Raspberry Pi to publish messages to AWS IoT.  

8. Choose Create.  

9. Choose the left arrow to return to the Policies page.  

10. In the left navigation pane, under Security, choose Certificates.  

11. In the box for the certificate you created, choose ... to open a drop-down menu, and then choose Attach policy.  

12. In the Attach policies to certificate(s) dialog box, select the check box next to the policy you created, and then choose Attach.  

13. In the box for the certificate you created, choose ... to open a drop-down menu, and then choose Attach thing.  

14. In the Attach things to certificate(s) dialog box, select the check box next to the thing you created to represent your Raspberry Pi, and then choose Attach.  



