# Glossary
<!--Kit: Telephony Kit-->
<!--Subsystem: Telephony-->
<!--Owner: @shao-yikai-->
<!--Designer: @wnazgul-->
<!--Tester: @jiang_99-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=a2ca33e3346b2c99b7393d42503470ef91eddb88 translatedAt=2026-11-02T07:51:58.827Z pushedAt=2026-11-03T01:17:25.782Z nl=1 -->

## A

### Access Point Name (APN)

A string that identifies the access point of a packet data network in mobile communications. It must be configured when a device establishes a cellular data connection, and it determines through which gateway the device accesses the carrier network or a private network.

## D

### Data SMS

An SMS message that carries binary byte data instead of text content. When sending such a message, you must specify a destination port for port-based addressing. It is used to transfer structured data (such as WAP Push) between terminal applications, and is distinguished from text SMS messages.

### Default Cellular Data SIM

The SIM card currently designated for cellular data services on the device, identified by `slotId`. On a dual-SIM device, one SIM must be designated as the default data SIM, which serves as the default target of other cellular data interfaces.

## M

### Multimedia Messaging Service (MMS)

A service that transmits messages containing multimedia content such as text, images, audio, and video over a mobile network. Unlike plain-text `SMS`, it encapsulates messages in `PDU` based on `WAP/HTTP` and delivers them through store-and-forward via the `MMSC`.

## V

### vCard

A standard file format for representing contact information (such as name, phone number, address, URL, and photo). In OpenHarmony, the vCard module supports importing this format into the contact database or exporting it back.

### vCard File (VCF)

A contact information file that conforms to the vCard standard (with the `.vcf` extension). It organizes contact fields as plain-text key-value pairs and is used for import and export operations.

### Voice over LTE (VoLTE)

A voice service provided over the LTE data bearer based on the IMS architecture. Unlike traditional CS-domain voice, its support and enablement are controlled by carrier configuration items.