# TaskerNightscoutNotificationPlugin
This is a plugin for Nightscout to be used in combination with Tasker and the Notification Listener Plugin. This currently has only been tested with Guardian Connect (ie without a pump).

This requires the following on your Android phone: 

https://play.google.com/store/apps/details?id=net.dinglisch.android.taskerm
https://play.google.com/store/apps/details?id=com.balda.notificationlistener

In Tasker -> Profiles
-> ( + ) Event
   -> Notification Listener
     * Event: Any Apps: Guardian CGM

Add Task
 1. Variable Set
   * Name %GuardianVlaue to %nltitle
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
   
