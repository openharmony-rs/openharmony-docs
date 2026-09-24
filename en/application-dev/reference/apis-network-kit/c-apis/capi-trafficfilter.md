# TrafficFilter

## Overview

Defines the APIs for traffic filtering.

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Since**: 26.0.0

## Files

| Name | Description |
| -- | -- |
| [net_trafficfilter.h](capi-net-trafficfilter-h.md) | Declares the C APIs for network traffic filtering and redirection. This header file provides APIs for creating and destroying a packet controller, registering packet callbacks, adding and deleting filtering rules, creating and destroying a traffic redirector, and adding and deleting redirection rules. <br>It is applicable to scenarios where network packets need to be intercepted, filtered, and redirected at the system level. |
| [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md) | Declares the common types and error codes required for network traffic filtering and redirection. This header file defines the match condition structs (such as IP addresses, ports, and interfaces) used in traffic filtering and redirection, configuration structs (such as packet filter rules and redirection rules), and error codes returned by operations. <br>This header file is used to construct parameters and parse return values when APIs such as {@link OH_TrafficFilter_CreateRedirector} are called. |
