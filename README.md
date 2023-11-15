# BandwidthSession & BandwidthUA Integration Guide

Welcome to the BandwidthSession and BandwidthUA integration guide. This comprehensive guide will assist developers in seamlessly integrating the powerful `BandwidthSession` and `BandwidthUA` services provided by BandwidthSDK into their Swift applications.

![Bandwidth Logo](https://example.com/bandwidth_logo.png)

## Table of Contents`

1. [Introduction](#introduction)
2. [Configuration](#configuration)
   - [Setting Variables](#setting-variables)
   - [Configuration Steps](#configuration-steps)
3. [Event Handling](#event-handling)
   - [Listening to Call Events](#listening-to-call-events)
4. [Usage](#usage)
   - [Making a Call](#making-a-call)
   - [Ending a Call](#ending-a-call)
   - [Additional Functions](#additional-functions)
5. [Error Handling](#error-handling)
## Introduction

Integrating Bandwidth's communication services into your Swift applications has never been easier. With this guide, you'll learn how to harness the full potential of `BandwidthSession` and `BandwidthUA` to enable voice communication capabilities within your application.

## Configuration

### Setting Variables

Before configuring the SDK, let's understand the essential variables:

- **BandwidthSession**: This variable may initially be null as it will store the result later.
- **BandwidthUA**: This represents the main instance of the Bandwidth SDK.

### Configuration Steps

To use the BandwidthSDK effectively, you must initialize the connection by following these simple steps:

1. **Configure AudioCodesUA**: Provide the connection data to establish the communication link.
2. **Configure OAuth Authentication**: Set up the necessary authentication details to ensure secure access.

## Event Handling

### Listening to Call Events

To monitor the status of an ongoing call and react accordingly, you need to implement the `BandwidthSessionEventListener` in your main application class. Here, you can listen to critical call events, such as:

- `callTerminated`: Detect when a call has ended.
- `callProgress`: Monitor the progress of an ongoing call.
- `incomingNotify`: Receive notifications about incoming calls.

## Usage

### Making a Call

Now that your SDK is configured, you can initiate calls seamlessly. To make a call, use the `makeCall` function provided by `BandwidthUA`. This function takes the phone number and domain as parameters and returns a `BandwidthSession` instance. Don't forget to set up the listeners to handle call events effectively.

```swift
func makeCall() {
    session = bandwidthUA.makeCall(phoneNumber, domain: domain)
    if let session = session {
        session.addSessionEventListener(listener: self)
    }
}
```

### Ending a Call

To gracefully terminate an active call, use the `terminate` method of the `BandwidthSession` variable stored when making the call. This action will also trigger the `callTerminated` listener.

```swift
/// Terminate the active call.
func terminateCall() {
    if let session = session {
        session.terminate()
    }
}
```

### Additional Functions

`BandwidthSession` exposes additional functions such as `muteAudio(mute: Bool)`, `hold(hold: Bool)`, and `sendDTMF(dtmf: dtmf)` that empower you to customize and enhance your voice communication session.

## Error Handling

In any application, errors are inevitable, especially in networked operations. Make sure to implement robust error handling mechanisms to catch, manage, and inform users about any errors that may occur. This will ensure a seamless user experience.
