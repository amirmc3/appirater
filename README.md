Introduction
---------------

SwiftRate is a class that you can drop into any iPhone app (iOS 8.0 or later) that will help remind your users
to review your app on the App Store. The code is released under the MIT/X11, so feel free to
modify and share your changes with the world. Read on below for how to get started. If you need any help using, the library, post your questions on [Stack Overflow] [stackoverflow] under the `SwiftRate` tag.

Getting Started
---------------


Configuration
-------------
1. Add This code to your App Delegate 'SwiftRate.RegisterSwiftRate()' or  SwiftRate.RegisterSwiftRate(debug: true) for quickly turn on debug mode
2. SwiftRate provides class methods to configure its behavior. See [SwiftRate.swift] for more information.

```swift
SwiftRate.config_AppID(appID: "1234567890")
SwiftRate.config_DaysUntilPrompt(value:1)
SwiftRate.config_UsesUntilPrompt(value: 10)
SwiftRate.config_longTermSignificantEventsUntilPrompt(value: -1)
SwiftRate.config_shortTermSignificantEventsUntilPrompt(value: -1)
SwiftRate.config_TimeBeforeReminding(value: 2)
SwiftRate.config_DebugMode(debug: true)
```

3. Call `SwiftRate.config_AppID(appID: "your App ID")` with the app id provided by Apple. A good place to do this is at the beginning of your app delegate's `application:didFinishLaunchingWithOptions:` method.
4. (OPTIONAL) Call `SwiftRate.userDidSignificantEvent(eventType: .shortTerm)` when the user does something 'significant' in the app since app opened.
5. (OPTIONAL) Call `SwiftRate.userDidSignificantEvent(eventType: .longTerm)` when the user does something 'significant' since the app was installed/updated.

###Development
Setting `SwiftRate.config_DebugMode(debug: true)` will ensure that the rating request is shown each time the app is launched.

###Production
Make sure you set `SwiftRate.config_DebugMode(debug: false)` to ensure the request is not shown every time the app is launched. Also make sure that each of these components are set in the `application:didFinishLaunchingWithOptions:` method.

This example states that the rating request is only shown when the app has been launched 5 times **and** after 7 days.

```swift
SwiftRate.config_AppID(appID: "1234567890")
SwiftRate.config_DaysUntilPrompt(value:7)
SwiftRate.config_UsesUntilPrompt(value: 5)
SwiftRate.config_longTermSignificantEventsUntilPrompt(value: -1)
SwiftRate.config_shortTermSignificantEventsUntilPrompt(value: -1)
SwiftRate.config_TimeBeforeReminding(value: 2)
SwiftRate.config_DebugMode(debug: false)

```

If you wanted to show the request after 5 days only you can set the following:

```swift
SwiftRate.config_AppID(appID: "1234567890")
SwiftRate.config_DaysUntilPrompt(value:5)
SwiftRate.config_UsesUntilPrompt(value: 0)
SwiftRate.config_longTermSignificantEventsUntilPrompt(value: -1)
SwiftRate.config_shortTermSignificantEventsUntilPrompt(value: -1)
SwiftRate.config_TimeBeforeReminding(value: 2)
SwiftRate.config_DebugMode(debug: false)
```

Help and Support Group
----------------------
Requests for help, questions about usage, suggestions and other relevant topics should be posted at the [SwiftRate group] [SwiftRategroup]. As much as I'd like to help everyone who emails me, I can't respond to private emails, but I'll respond to posts on the group where others can benefit from the Q&As.

License
-------
Copyright 2017. Amir Kamali [Amir Kamali].
This library is distributed under the terms of the MIT/X11.
This library is based on Appirater library with major update


[stackoverflow]: http://stackoverflow.com/
[homepage]: https://arashpayan.com/blog/2009/09/07/presenting-SwiftRate/
[Amir Kamali]: http://Kamali.io
[SwiftRate.swift]: https://github.com/AmirKamali/SwiftRate/blob/master/SwiftRate.swift
