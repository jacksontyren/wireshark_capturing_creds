<h1>🔓Unlocking Insights: Capturing Clear Text Credentials Using Wireshark</h1>


<h2>Overview</h2>
The primary objective of the lab was to simulate a scenario where potential threats could compromise sensitive information transmitted over a network. By leveraging the powerful tools Wireshark the exercise aimed to provide a practical understanding of how malicious actors might attempt to capture clear text credentials exchanged between users and applications.
<br />


<h2>Tools Used</h2>

- <b>Kali Linux VM</b> 
- <b>Wireshark</b>


<h2>Walk-through</h2>

<p align="center">
<strong>Step 1:</strong> Open the terminal and enter the command to open Wireshark.<br/>
sudo wireshark <br/>
 <img src="https://github.com/jacksontyren/wireshark_capturing_creds/assets/121649532/9aabf879-f3ce-44a8-b580-ec158532473e" height="80%" width="80%">
<br />
<br />
<strong>Step 2:</strong> Select the interface you would like to use to capture packets on. I used the eth0 interface.  <br/>
<img src="https://github.com/jacksontyren/jacksontyren/assets/121649532/9547b5b0-88dd-4d38-9400-99868cac02d9" height="80%" width="80%"/>
<br />
<br />

<img src="https://github.com/jacksontyren/jacksontyren/assets/121649532/7236b0cf-5ebb-4a74-9028-a5cb91f0a05d" height="80%" width="80%" />
<br />
 <p align="center">On the main screen we can see that the application has begun listening on the network. The top section is used to display a list of the packets captured. These packets are displayed as a table. Information about each packet is displayed here, such as the packet number, packet source and destination, the time captured, and the packet’s protocol. </br>
<p align="center">
<strong>Step 3:</strong> Open Firefox and visit the following site:
http://testphp.vulnweb.com/login.php.
This is a login page. We notice the lock with the red line at the top left of the page, indicating that this page is communicating through HTTP (port 80). HTTP does not encrypt data coming through like its secure counterpart HTTPS (port 443).<br/>
<img src="https://github.com/jacksontyren/jacksontyren/assets/121649532/87685577-7103-4384-81da-7bc4da51b50d" height="80%" width="80%"/>
<br />
<br />
Enter a random username and password into this form and click login. Once this is done, return to Wireshark.  <br/>
<img src="https://github.com/jacksontyren/jacksontyren/assets/121649532/b421162a-2808-4960-97f3-0653edf5dfbc" height="80%" width="80%"/>
<br />
<br />
<strong>Step 4:</strong> Click the stop button to end the packet capture. We can see that there is many more packets of data available for analysis. On the top in the filter tab enter "http" to filter for only HTTP requests.  <br/>
<img src="https://github.com/jacksontyren/jacksontyren/assets/121649532/c043656f-9a53-4b34-9bc1-373113396b04" height="80%" width="80%"/>
<br />
<br />
<strong>Step 5:</strong> Look for the packet with POST included in the info section of the first pane (1). Once you find it, select this packet. POST is an HTTP method used to send data to a web server for processing by a resource. In this case, this is when credentials were entered and the login button was clicked.
In the second pane under the tab called Hypertext Transfer Protocol, when it is clicked the login information is displayed that was entered on the vulnerable website (2). <br/>
<img src="https://github.com/jacksontyren/jacksontyren/assets/121649532/335f92a8-a7ad-460e-bba8-7887ef8e00d7" height="80%" width="80%"/>
</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
