# Tasker Nightscout Notification Plugin (javascript)
This is a plugin for Nightscout to be used in combination with Tasker and the Notification Listener Plugin. This currently has only been tested with Guardian Connect (ie without a pump).

This requires the following on your Android phone: 

https://play.google.com/store/apps/details?id=net.dinglisch.android.taskerm

https://play.google.com/store/apps/details?id=com.balda.notificationlistener

Add a listener for the values from the Guardian Application:

In Tasker -> Profiles
-> ( + ) Event
   -> Notification Listener
     * Event: Any Apps: Guardian CGM
Add Task
 1. Variable Set
   * Name %GuardianValue to %nltitle
 2. Java Scriptlet
   * Insert contents of jar file below indicated line. 
   * Make sure to set API_SECRET value
 3. HTTP Request
   * Method POST URL https://YOURSITE.herokuapp.com/api/v1/entries.json
   * Headers
    * api-secret: %SHA1SECRET
  *  Body
    * %JSONvalue
  * If
    * DoUpload EQ true
 4. Variable Set
  * %Response To %http_response_code
   

Slightly more detailed instructions for the steps Up to Java Scriptlet
1. Open Tasker
2. Go to the Profiles tab
3. Press the (+) button
4. Choose Event
5. In the 'Filter' box type 'Notification Listener' & select the resulting 'Notification Listener' result
6. In the resulting Configuration: (a) Notification Event: Any, (b) Apps, press second button to search for app and then find Guardian Connect and save result, this will result in 'com.medtronic.diabetes.guardianconnect' being in the textbox
7. Press save (tick)
8. Add Task (+)
9. (1) Variable Set
10. (1) %GuardianValue to %nltitle






See https://github.com/NightscoutFoundation/xDrip/issues/1684
