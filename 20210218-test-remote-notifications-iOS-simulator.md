# How to test remote notifications on iOS simulator

[https://www.avanderlee.com/workflow/testing-push-notifications-ios-simulator/](https://www.avanderlee.com/workflow/testing-push-notifications-ios-simulator/)

[https://warchimede.hashnode.dev/how-to-test-deep-links-when-an-ios-app-is-killed](https://warchimede.hashnode.dev/how-to-test-deep-links-when-an-ios-app-is-killed)

`xcrun simctl push booted <bundle id> payload.json`

**avec par exemple pour  payload.json :**

{

"aps": {

"alert": {

"body": "Test of remote push notification",

"title": "Push test"

}

}

}

add deeplink using ^d

{

“Simulator Target Bundle”: “[np.com](http://np.com/).sagunrajlage.TestPushNotifications”,

“^d”: “[yatta://video/2001971?t=](yatta://video/2001971?t=)”,

“aps”: {

“alert”: “Push Notifications Test”,

“sound”: “default”,

“badge”: 1

}

}