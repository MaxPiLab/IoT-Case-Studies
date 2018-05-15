
# What is dweet

dweet is a simple messaging service which is being considered as an effective messaging tool in Internet Of Things. Just like you can send a tweet on twitter, you can send a *dweet* from your device to the dweet.io platform.  

The goal of IoT messaging is for a device to send a chunk of data to a server where it’s stored for some period of time. That data can then be retrieved by one or mutliple devices for analysis, display, storage or whatever.Dweet makes a best effort attempt to receive and send messages ignoring problems like message duplicacy and message loss.  

Here are some features of dweet service  

* Uses publish / subscribe mechanism.  
* Messages are published for a particular topic and receiving devices can listen on that particular topic.  
* This topic is called as a '*thing*' in dweet.io's terminology.  
* No registration or login required to send data or consume data with dweet.io.  
* No setup or download required.  
* Name of the thing to publish to can be decided at run time when calling the http post.  
* This name can either be your own name or a random name assigned by dweet.io.  
* Publishing and data is a simple http post operation while reading data is a http get operation.  
* Free to use with unlimited things.  

**NOTE**

1. The name of things chosen by you must be unique.  

   * There should not be any existing thing on dweet.io with the same name.  
	 * One way to ensure this uniqueness is choose as random a name as possible.  
	 * The other way is to let dweet.io choose the name for you.  
   
2. Data is stored on dweet.io only up to last 5 dweets for up to 24 hours only.  

   * If you don't dweet any data for 24 hours, your thing is deleted from dweet.io.  
   
3. The data you post on dweet.io is by default public.  

  * This means that anyone with the thing name can see your data in real time.  
	* Moreover all the public things are listed on dweet.io website itself for anyone to see. (https://dweet.io/see)  

The only way to reserve a specific thing name and hide your data from public is to lock your thing and not surprising but you have to pay for that. With paid things, data is stored on dweet.io for up to 30 days.  

### Visualization options

* Data sent to dweet.io can be visualized on their website https://dweet.io.  This is a very basic graphical representation of your    data.  
* Freeboard.io is a companion tool for generating dashboards for data visualization using the data from dweet.io that your device sends.  * When you send data to dweet.io, the page https://dweet.io/follow/YOUR_THING_NAME shows your data in a graphical way.  
* Click on the button - "Create a Custom Dashboard" and it will take you to freeboard.io website with a dashboard ready to use.   

### How TO

1. Install requests library in Python  

   ```sudo pip install requests```  
    
2. File -  "send_dummy_dweet.py"- Just sends some dummy data to dweet.io.  
   * Add a random unique name for your thing (See code for the line to change)  
	 * Visualize data on dweet.io  
	 * Create a dashboard from dweet.io using button 'Create free dashboard'  
	 * Import dashboard - Select file "dummy_dashboard.json "  

3. Make sure the code in file hcsr04.py (in same directory) is working for your hardware.  
4. File - "send_sensors_dweet.py" - Sends ultrasonic sensor data to dweet.io  
   * Create a dashboard from dweet.io  
	 * Visualize data on dweet.io  
	 * Create a dashboard from dweet.io using button 'Create free dashboard'  
	 * Import dashboard - not available for this example. Customize your own dashboard.  


