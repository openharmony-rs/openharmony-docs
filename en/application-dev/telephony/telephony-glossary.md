# Glossary
<!--Kit: Telephony Kit-->
<!--Subsystem: Telephony-->
<!--Owner: @shao-yikai-->
<!--Designer: @wnazgul-->
<!--Tester: @jiang_99-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=ff44b6ea2c38b42e6a4562b9ab98bf001b9d9382 translatedAt=2026-08-31T03:15:04.662Z pushedAt=2026-09-01T03:15:49.799Z -->

## A

### Access Point Name (APN)

A string that identifies the access point of a packet data network in mobile communications. It must be configured when a device establishes a cellular data connection, and it determines the gateway through which the device accesses the carrier network or a private network.

## D

### Data SMS

A short message that carries binary byte data instead of text content. When sending such a message, you must specify a destination port for port addressing. It is used to transfer structured data (such as WAP Push) between terminal applications, and is distinguished from text messages.

### Default Cellular Data SIM

The SIM card designated by the device for cellular data services, identified by `slotId`. On a dual-SIM device, one SIM must be designated as the default data SIM, which serves as the default target of other cellular data interfaces.

## M

### Multimedia Messaging Service (MMS)

A service that transmits messages containing multimedia content such as text, images, audio, and video over a mobile network. Unlike plain-text `SMS`, it encapsulates messages in `PDU` based on `WAP`/`HTTP` and delivers them through store-and-forward by the `MMSC`.

## V

### vCard

A file format standard for representing contact information (name, phone number, address, URL, photo, and so on). In OpenHarmony, the `VCard` module supports importing vCards into the contact database or exporting them in reverse.

### vCard File (VCF)

A contact information file that conforms to the vCard standard (with the .vcf extension). It organizes contact fields as plain-text key-value pairs and is used for import and export operations.

### Voice over LTE (VoLTE)

A voice service provided over the LTE data bearer based on the IMS architecture. Unlike traditional CS domain voice, its support and switch are controlled by operator configuration items.