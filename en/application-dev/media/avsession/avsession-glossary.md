# Glossary
<!--Kit: AVSession Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @ccfriend; @devil_red-->
<!--Designer: @ccfriend-->
<!--Tester: @chenmingxi1_huawei-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=092adc6b47e5b0c088b6fe6b4574b30796b51a5e translatedAt=2026-09-02T08:33:02.636Z pushedAt=2026-09-03T02:12:25.664Z -->

## A

### Audio & Video Session (AVSession)

A communication channel between a media application and a media controller for exchanging playback information and control commands. One end is connected to the media application, and the other is connected to a controller, such as Media Controller or AI Voice. It is the core concept of AVSession Kit and provides unified media presentation and playback control capabilities.

### AVMetadata

A collection of metadata that describes a media item. It includes properties such as the media ID (`assetId`), title (`title`), author (`author`), album (`album`), writer (`writer`), duration (`duration`), lyrics (`lyric`), cover image (`mediaImage`), and audio source tag (`displayTags`). Media applications use this metadata to present media information in the Media Controller.

### AVMusicTemplate

A class that encapsulates interactions with the Media Controller. It includes properties such as the session ID (`sessionId`) and session tag (`sessionTag`), and provides APIs for exchanging data with the Media Controller. Media applications can use this class to report media information and respond to playback control commands, reducing application-side implementation effort.

### AVPlaybackState

A collection of properties that describes the current playback state. It includes the playback state (`state`), playback position (`position`), playback speed (`speed`), buffered time (`bufferedTime`), loop mode (`loopMode`), favorite status (`isFavorite`), active media ID (`activeItemId`), and custom media data (`extras`). It is used to present playback progress and playback controls in the Media Controller.

### AVSessionController

An object held by an AVSession controller to control playback in the application that provides the AVSession. It can obtain playback information and listen for playback state changes in the media application, keeping AVSession information synchronized between the media application and the Media Controller.

### AVSessionDescriptor

An object that describes an AVSession. It includes properties such as the AVSession ID (`sessionId`), session type (`type`), custom session name (`sessionTag`), information about the application to which the AVSession belongs (`elementName`), and whether the session is the top session (`isTopSession`).

### AVSessionManager

A module that provides AVSession management capabilities. It can create AVSessions (`AVSession`) and AVSession controllers (`AVSessionController`), send system control events, and listen for AVSession state changes.

### AVSessionType

Parameters that define the AVSession type, including five types: `audio` (audio session), `video` (video session), `voice_call` (voice call session), `video_call` (video call session), and `photo` (photo session). Different types determine the control template style displayed in the Media Controller.

## B

### BackgroundPlayMode

An enumeration that specifies whether playback continues after an application enters the background. It includes `ENABLE_BACKGROUND_PLAY`, which allows background playback, and `DISABLE_BACKGROUND_PLAY`, which disables background playback. The system uses this mode to determine whether to display a system live window after the application enters the background.

## D

### DisplayTag

A tag that identifies the media audio source, used to display media audio information in the Media Controller. Currently, the `TAG_AUDIO_VIVID` tag is supported, indicating that the audio source is Audio Vivid.

## P

### ProtocolType

An enumeration that defines the protocol types supported by a remote device. It includes `TYPE_LOCAL` for a local device, `TYPE_CAST_PLUS_STREAM` for Cast+ Stream mode, `TYPE_DLNA` for the DLNA protocol, and `TYPE_CAST_PLUS_AUDIO` for PCM mode. It is used to identify the communication protocols supported by a casting device.

## T

### TopSession

The AVSession with the highest priority in the system, typically a session that is currently playing. An AVSession controller can communicate directly with the top session without first obtaining its corresponding controller. For example, it can send playback control commands and key events directly to the top session.