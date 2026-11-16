# Common Event Service Glossary
<!--Kit: Basic Services Kit-->
<!--Subsystem: Notification-->
<!--Owner: @HuYueRong-->
<!--Designer: @wangsen1994-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=4faed534b39ef26ef8f9b647802a53e9f8d2b792 translatedAt=2026-11-16T04:20:11.814Z pushedAt=2026-11-16T07:27:51.947Z nl=1 -->

## C

### Common Event Service (CES)

A notification subsystem service that provides cross-process event communication capabilities. Based on the publish-subscribe model, it delivers events published by publishers to subscribed subscribers according to event names, enabling decoupled communication between applications and between applications and the system.

## O

### Ordered Common Event

A common event delivered to subscribers in order of subscriber priority. A subscriber can set the result code and result data to be passed to subsequent subscribers in the callback, or abort the delivery of the event to subsequent subscribers. After each callback is processed, the completion interface must be called before the event can continue to be delivered to the next subscriber.

## S

### Static Subscription

A common event subscription method declared by an application through configuration. Its enabled or disabled state can be set as needed to control whether the subscribed common events are received.

### Sticky Common Event

A common event that is persistently stored after being published. New subscribers can still receive the event after subscribing, which is suitable for scenarios where subscribers that join later need to obtain historical events. Only system applications or system services can publish it.

### System Common Event

A common event predefined by the system and provided as fixed-name constants (such as battery level changes, screen on/off, Wi-Fi status, USB status, etc.). It is available for applications to subscribe to in order to perceive system status changes, without the need for applications to define event names themselves.

## U

### Unordered Common Event

A common event that is delivered to all subscribed subscribers simultaneously. It does not involve delivery order or subscriber priority, and is suitable for event broadcast scenarios that do not require ordered processing.