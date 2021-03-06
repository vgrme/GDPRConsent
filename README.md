[![CircleCI](https://circleci.com/gh/DavidEdwards/GDPRConsent/tree/master.svg?style=svg)](https://circleci.com/gh/DavidEdwards/GDPRConsent/tree/master)

# GDPR Consent

This project does not guarantee in any way that your App is immune or compliant with GDPR regulations. Ensure that you READ the associated laws yourself thoroughly.

This is a great resource to learn about it: https://gdpr-info.eu/

![Example animation](https://github.com/DavidEdwards/GDPRConsent/blob/master/example.gif)

## Implement in your project

```
maven { url 'https://jitpack.io' }

implementation 'com.github.DavidEdwards:GDPRConsent:1.0'
```

These dependencies must be registered in your own app level gradle.build.

```
implementation 'com.android.support:design:27.1.1'
implementation "com.android.support:cardview-v7:27.1.1"
implementation 'com.android.support.constraint:constraint-layout:1.1.0'
implementation "android.arch.lifecycle:extensions:1.1.1"
```

These must also be added to your android block in the app level gradle.build.

```
compileOptions {
    sourceCompatibility = '1.8'
    targetCompatibility = '1.8'
}
dataBinding {
    enabled = true
}
```

Ensure that you are also using the latest gradle plugin.

```
classpath 'com.android.tools.build:gradle:3.2.0-alpha14'
```

There is an example App in this repository that you can test with.

## Goals

* Providing a granular consent system. Each individual system should be disable-able.
* Consent items must be able to be marked as required, in the case where your App couldn't function. For example, navigation software that needs your location.
* Making it easy to see what a specific consent entails, what is stored, why it is stored.
* Details of consent are immutable. Once it has been saved once, it remains. The developer cannot change the language of consent without creating a new consent, that in turn must be consented to.
* New consent can be added at any time after release of the App. New items will be presented to the user the next time that they run the App after updating.
* User can revoke consent as easy as they gave it.
* Providing a neutral interface. It is designed with Material "2" in mind. Primarily white, colours used to indicate importance.
* Providing an external link to more information if the user needs it.

## Known issues

* Not built specifically for different display types. It works on tablets, certainly. However, it could be optimized.

## Doesn't attempt to solve:

* Automatically blocking access to services and APIs until consent is given. This must be done manually still. I am using a helper class to get the consent state of a key to determine whether a service is allowed to function.
* Correcting personal data. This should be provided by the App itself.
* Deleting personal data. This should be provided by the App itself.
