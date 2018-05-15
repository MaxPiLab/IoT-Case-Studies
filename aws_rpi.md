

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

The AWS IoT Device SDK helps you to connect devices to AWS IoT. It provides features so that devices can seamlessly and securely work with the Device Gateway and Device Shadow provided by AWS IoT.

## Installing the AWS IoT Device SDK and Building a Sample Application

Installing the AWS IoT Device SDK and building a sample application consists of a few steps. One must:  

### 1. Upload Certificates and a key pair to the device.  

Use Secure Copy `(scp)` to move the keys and certificates to your device:  

`scp privkey.pem pi@raspberrypi.local:/home/pi  
scp pubkey.pem pi@raspberrypi.local:/home/pi  
scp crt.crt pi@raspberrypi.local:/home/pi  
scp ca.pem pi@raspberrypi.local:/home/pi  
 `
 
 **NOTE: The default password for the default `pi` user in Raspbian is `raspberry`.**  

### 2. Download the AWS IoT SDK onto the device and install it.  

Open a Secure Shell `(ssh)` with the Raspberry Pi:  

`ssh pi@raspberrypi.local`  

Next, in the SSH shell, download the AWS IoT Device SDK for C in a tarball (linux_mqtt_openssl-latest.tar). Save it in your deviceSDK directory.  

`wget https://s3.amazonaws.com/aws-iot-device-sdk-embedded-c/linux_mqtt_openssl-latest.tar`  

Move the tarbell into `/opt/devicesdk` and extract it:  

`mkdir /opt/devicesdk  
 mv linux_mqtt_openssl-latest.tar /opt/devicesdk  
 cd /opt/devicesdk  
 tar -xvf linux_mqtt_openssl-latest.tar  
 `  
Move the certificates and key pair into `/opt/devicesdk/certs`:

`mv /home/pi/privkey.pem /opt/devicesdk  
 mv /home/pi/pubkey.pem /opt/devicesdk  
 mv /home/pi/crt.crt /opt/devicesdk  
 mv /home/pi/ca.pem /opt/devicesdk  
 `  
Before you can use the AWS IoT Embedded C SDK, you must install the OpenSSL library on Raspberry Pi:  

`sudo apt-get install -y libssl-dev`  

### 3. Configure the sample application with the needed AWS IoT variables.  

Navigate to `/opt/devicesdk/sample_apps/shadow_sample` and edit the `aws_iot_config.h`, using an editor that is installed on Raspbian by default, such as `nano`:  

`cd /opt/devicesdk/sample_apps/shadow_sample
 nano aws_iot_config.h
 `  
Providing the following information:  

`#define AWS_IOT_MQTT_HOST “ENDPOINT.iot.us-east-1.amazonaws.com”  
 #define AWS_IOT_MQTT_PORT 8883  
 #define AWS_IOT_MQTT_CLIENT_ID “THING NAME”  
 #define AWS_IOT_MY_THING_NAME “THING NAME”  
 #define AWS_IOT_ROOT_CA_FILENAME “ca.pem”  
 #define AWS_IOT_CERTIFICATE_FILENAME “cert.crt”  
 #define AWS_IOT_PRIVATE_KEY_FILENAME “privkey.pem”  
 `  
 
Supply the endpoint you gathered in the first part of this tutorial, when interacting with AWS IoT via the AWS CLI. If you need to get it again, use the AWS CLI:  

`aws iot describe_endpoint`  

The file names for `AWS_IOT_ROOT_CA_FILENAME`, `AWS_IOT_CERTIFICATE_FILENAME`, and `AWS_IOT_PRIVATE_KEY_FILENAME` should not contain paths, but should be bare file names instead. The specific values to provide may be different from this example.  

Save the file and exit the editor.  

### 4. Compile and run the sample application.  

Compile the example and run:  

`make -f Makefile`  

This will produce an executable called `shadow_sample`, which you can run:  

`./shadow_sample`  

You should be able to log into the AWS management console, open the IoT service and see entries being written by your device. It should look something like this:  









