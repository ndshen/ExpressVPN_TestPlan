# Test Plan for ExpressVPN

> Strongly recommend to view this testplan at: https://hackmd.io/@ndshen/SkTz_GlbP

To test the app compatibility on different version of Android, all of the tests below should be run on at least one device of the lowest available API level(mentioned in Gradle) to the device of the highest availabe API level.


## Initial Usage
### Installation and Launch Test   
**ID**: 1   
**Priority**: <span style="color: red">High</span>  
**Severity**: <span style="color: red">Critical </span>  
\# | Step | Expected Result
-- | ------| ----------------
1 | Install APK from Google Play Store: https://play.google.com/store/apps/details?id=com.expressvpn.vpn |APK instatlled
2 | Launch the application | App launched, check if the first activity is correct. (Appium: appWaitActivity)   

<br>


### Initial Setup Test   
**ID**: 2   
**Priority**: <span style="color: red">High</span>  
**Severity**: <span style="color: red">Critical </span>  
\# | Step | Expected Result
-- | ------| ----------------
1 | Launch the application after installation | User can select "Start Free Trial" or Sign in
2 | Select Free Trial | An editText element shown, for user to input e-mail
3 | Input E-mail for free trial | A new account is created and the user is able to use the free trial VPN for 7 days

<br>

## VPN Functionality
### Basic VPN Connection  Funcitionality Test
**ID**: 3    
**Priority**: <span style="color: red">High</span>  
**Severity**: <span style="color: red">Critical </span>  
\# | Step | Expected Result
-- | ------| ----------------
1 | Check the current IP address on the device | An IP address is recoreded
2 | Launch the application and navigate to the main activity(the one with the 'connect' button) | Main activity is shown
3 | Press the connect button | VPN connection established -> Show 'Connected' message<br>VPN connection failed -> Show 'Connection Fail' message
4 | If the VPN connection established successfully, check the IP adress on the device again | The IP has changed

<br>

### VPN Connection in background Test
**ID**: 4   
**Priority**: <span style="color: red">High</span>  
**Severity**: <span style="color: orange">Critical </span>  
\# | Step | Expected Result
-- | ------| ----------------
1 | Launch the application and navigate to the main activity(the one with the 'connect' button) | Main activity is shown
2 | Press the connect button | Connecting to the server
3 | Wait for the connection to be established | Connection established
4 | Put to appliction to background | The device is still connected to the server. (With a vpn icon on top of the screen)


<br>

### Internet connection fail before VPN connection
**ID**: 5    
**Priority**: <span style="color: yellow">Medium</span>  
**Severity**: <span style="color: yellow">Medium </span>  
\# | Step | Expected Result
-- | ------| ----------------
1 | Launch the application and navigate to the main activity(the one with the 'connect' button) | Main activity is shown
2 | Turn on the airplane mode on the phone | Shut down all the internet connection
3 | Press the 'Connect' button | An error message shown to inform user that there is no internet connection


<br>

### Internet connection fail during VPN connection
**ID**: 6    
**Priority**: <span style="color: yellow">Medium</span>  
**Severity**: <span style="color: yellow">Medium </span>  
\# | Step | Expected Result
-- | ------| ----------------
1 | Launch the application and navigate to the main activity(the one with the 'connect' button) | Main activity is shown
2 | Press the 'Connect' button | VPN connection established
3 | Turn on the airplane mode on the phone | Shut down all the internet connection
4 | Check the connection status on main activity | A message to inform user that the connection failed, and the potential reason.

<br>

## User Account
### Free trial expire Test
**ID**: 7    
**Priority**: <span style="color: yellow">Medium</span>  
**Severity**: <span style="color: Orange">High </span>  
\# | Step | Expected Result
-- | ------| ----------------
1 | Clear application user data and cache | The application is reset
2 | Launch the app and login with a free trial account which is created 7 days ago | User cannot use the VPN, and an upgrade request is sent to the user

<br>

### Free trial expire cheat Test
**ID**: 8   
**Priority**: <span style="color: yellow">Medium</span>  
**Severity**: <span style="color: red">Critical </span>  
\# | Step | Expected Result
-- | ------| ----------------
1 | Clear application user data and cache | The application is reset
2 | Change the device time setting to (current_date - 7 days)| The date setting of the device is changed 
2 | Launch the app and login with a free trial account which is created 7 days ago | User cannot use the VPN, and an upgrade request is sent to the user

<br>

### Upgrade Account
**ID**: 9   
**Priority**: <span style="color: yellow">Medium</span>  
**Severity**: <span style="color: Orange">High </span>  
\# | Step | Expected Result
-- | ------| ----------------
1 | Clear application user data and cache | The application is reset
2 | Launch the app and login with an upgraded account | User should see the upgraded version of the app  

(Since I don't have an upgraded account, I haven't decided how to validate an upgrade version app.)
<br>

## Miscellaneous
### Settings User Data Test
**ID**: 10   
**Priority**: <span style="color: yellow">Medium</span>  
**Severity**: <span style="color: orange">High</span>  
\# | Step | Expected Result
-- | ------| ----------------
1 | Launch the application and navigate to the Settings activity | Settings activity is shown
2 | Modify language settings to Japnanese | Application language changes to Japanese immediately
3 | Close the application (remove in the background) | Applciation shutdown
4 | Relaunch the application, and check the language setting | Language setting remains to be Japanese 

<br>

### Back button navigation
**ID**: 11    
**Priority**: <span style="color: yellow">Medium</span>  
**Severity**: <span style="color: yellow">Medium </span>  
\# | Step | Expected Result
-- | ------| ----------------
1 | Launch the application and navigate to the main activity | Main activity is shown
2 | Navigate though 'Menu' -> 'Settings' -> 'Auto-connect' | Auto-connect setting page is shown
3 | Press the back button 2 times | Go back to main activity by this order: 'Auto-connect' -> 'Settings' -> 'Main'

<br>

### User Interface Visuality Check
**ID**: 12   
**Priority**: <span style="color: green">Low</span>  
**Severity**: <span style="color: green">Low </span>  
\# | Step | Expected Result
-- | ------| ----------------
1 | Navigate though all the pages in the menu by Depth-First-Search method | All pages are shown in this test
2 | At each page(Activity), check the visibility and existence of all the elements that should be in that page according to the spec | Nothing is visually broken

