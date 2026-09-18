# OH_CommonEvent

## Overview

This module provides APIs of the Common Event Service, which are implemented in C. It provides cross-process event communication capabilities for apps based on the publication-subscription model. After a publisher publishes a common event, the system delivers the event to all subscribers who have subscribed to the event based on the event name. In this way, decoupled communication between apps and between apps and the system is implemented.

**Since**: 12

## Files

| Name | Description |
| -- | -- |
| [oh_commonevent.h](capi-oh-commonevent-h.md) | Defines key operation functions for publishing, subscribing to, and unsubscribing from common events, event callback data access, and ordered event control, enumerates error codes, and defines core data types. |
| [oh_commonevent_support.h](capi-oh-commonevent-support-h.md) | Provides common event constants defined by the system. |
