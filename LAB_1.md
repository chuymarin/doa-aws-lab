# Lab 1: IAM Getting Started

**Managing IAM Users**
* Go to AWS / Services / IAM / Users
* In there you can see a list of all the current users in your AWS Account
* In the searchbox write down your username to find your user and click on it
* You will see 4 tabs
  * Permissions: You will see the current permissions that your user has
  * Groups: These are the groups where you are a member
  * Security Credentials: In there you can change your password, generate access keys, and managing MFA Devices
  * Access Advisor: This  tab shows the last AWS services you have used
 
 **Changing your user password**
 * Go to the Security Credentials tab
 * In Console password click in Manage password link
   * In Set Password select custom password
   * Write your new password (And don't forget it!)
   * Click Apply button
 * Log off and log in again with your new password
 
 **Enabling MFA**
* Go to your user configuration again
* Go to the Security Credentials tab
* In Assigned MFA device click in pencil icon
  * Select A virtual MFA Device
  * Click in Next step button
  * The it shows you a message, read it and click in Next step button
  * It will show you a QR Code and some required fields
  * Now using your phone download Goole Authenticator App
  * Open Google Authenticator
  * Click in Add icon and select Scan a barcode
  * Use the camera on your phone to scan the QR Code from AWS
  * Then you will be requested to write **two consecutive** codes, you can find those in your phone's Google Authenticator
  * Click in Apply button 
* Now that you have enabled Multifactor Authenticator, each time you log in you will be request to use your phone to get a security code to log in
* Log off and log in again, and use your phone to get a security code

**Creating an IAM Role**

**Adding IAM Policies to your Role

**Review your IAM Role**

  
