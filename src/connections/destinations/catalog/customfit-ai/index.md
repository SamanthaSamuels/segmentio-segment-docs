---
title: CustomFit Destination
rewrite: true
---
[CustomFit.ai](https://customfit.ai/?utm_source=segmentio&utm_medium=docs&utm_campaign=partners) is an intelligent `App Experience Engine` for B2C apps(Mobile/Web/IoT), with which one can effortlessly craft hyper-personalized app experiences & alternative user journeys to each of their user or segment of users with zero code. Every user is unique, so should be your app.

This destination is maintained by CustomFit.ai. For any issues with the destination, please [reach out to their team](mailto:reach@customfit.ai).

_**NOTE:** The CustomFit.ai Destination is currently in beta, which means that they are still actively developing the destination. This doc was last updated on August 26, 2019. If you are interested in joining their beta program or have any feedback to help improve the CustomFit.ai Destination and its documentation, please [let  their team know](mailto:reach@customfit.ai)!_

## Getting Started

{% include content/connection-modes.md %}

1. From your Segment UI's Destinations page click on "Add Destination".
2. Search for "CustomFit.ai" within the Destinations Catalog and confirm the Source you'd like to connect to.
3. Drop in the "Server Key" into your Segment Settings UI which you can find from your [CustomFit.ai dashboard](https://dashboard.customfit.ai/settings/app-settings).

## Identify

`Identify` lets you tie a user to their actions and record traits about them. It includes a unique User ID and any optional traits you know about them like their email, name, etc., Please take a look to understand what the [Identify method](https://segment.com/docs/spec/identify/) does. An example call would look like:

```js
analytics.identify("user_id", {
  name: "Peter Gibbons",
  email: "peter@initech.com",
  plan: "premium",
  logins: 5
});
```
Segment handles the following mapping:
1. Segment `identify` event userId to CustomFit.ai `user_customer_id` field.
2. Segment `identify` event traits to CustomFit.ai `properties`.

Identify calls will be sent to CustomFit.ai as an `identify` event. You can find the user details in [users profile page](https://dashboard.customfit.ai/users/profiles).

## Track

The `track` API call is used to record any actions your users perform, along with any properties that describe the action. Each action is known as an event. Please take a look to understand what the [Track method](https://segment.com/docs/spec/track/) does. An example call would look like:

```js
analytics.track("Registered", {
  user_id : "97980cfea0067",
  plan: "Pro Annual",
  accountType: "Facebook"
});
```
Segment handles the following mapping:
1. Segment `track` event to CustomFit.ai `event_customer_id`.
2. Segment `track` event userId to CustomFit.ai `user_customer_id`.
3. Segment `track` event properties to CustomFit.ai event `data`

> Note : We expect `identify` event to be invoked before `track` event for a particular user.
>

Track calls will be sent to CustomFit.ai as an `track` event. You can find the user level track details under events tab of user profile.

## Page

The `page` call lets you record whenever a user sees a page of your website, along with any optional properties about the page. Please take a look to understand what the [Page method](https://segment.com/docs/spec/page/) does. An example call would look like:

```js
analytics.page("Home", {
  title : "CustomFit.ai",
  url : "http://customfit.ai"
});
```
Segment handles the following mapping:
1. Segment `page` event name to CustomFit.ai `name`.

Page calls will be sent to CustomFit.ai as a `pageview` event.

## Screen

The `screen` call lets you record whenever a user sees a screen, the mobile equivalent of page, in your mobile app, along with any properties about the screen. Please take a look to understand what the [Screen method](https://segment.com/docs/spec/screen/) does. An example call would look like:

```objc
[[SEGAnalytics sharedAnalytics] screen:@"Home"
                            properties:@{ @"Feed Type": @"private" }];
```
Segment handles the following mapping:
1. Segment `screen` event name to CustomFit.ai `name`.

Screen calls will be sent to CustomFit.ai as a `screenview` event.