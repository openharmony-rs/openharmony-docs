# Glossary
<!--Kit: AVSession Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @gcw_7KSyM10J; @devil_red-->
<!--Designer: @gcw_7KSyM10J-->
<!--Tester: @chenmingxi1_huawei-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=6e63a0e266900a11bfa74fe24b3b676187cc5558 translatedAt=2026-09-14T09:48:32.671Z pushedAt=2026-09-15T13:38:01.699Z -->

## A

### Audio & Video Session (AVSession)

A channel for information exchange between audio and video apps and their controllers. One end connects to the controlled audio or video app, and the other end connects to the app's controller (such as the media control center, voice assistant, etc.). It is the core concept of AVSession Kit, enabling unified display and control of audio and video content.

### AVMetadata

A collection of information that describes media data-related attributes, including media ID (`assetId`), title (`title`), album artist (`author`), album name (`album`), lyricist (`writer`), media duration (`duration`), lyrics (`lyric`), media cover (`mediaImage`), media audio source identifier (`displayTags`), and other attributes. A media app sets metadata to display media-related information in the control center.

### AVMusicTemplate

A class that describes the capabilities related to audio templates. It contains attributes such as the ID identifying the current media session (`sessionId`) and the session tag (`sessionTag`), as well as methods for data interaction with the control center. Through the audio template, a media app can report media-related information to the control center and respond to control commands from the control center, reducing the development workload on the app side.

### AVPlaybackState

A collection of information that describes media playback state attributes, including the playback state (`state`), playback position (`position`), playback speed (`speed`), buffered time (`bufferedTime`), loop mode (`loopMode`), whether it is a favorite (`isFavorite`), active media ID (`activeItemId`), custom media data (`extras`), and other attributes. It is used to display playback progress and control state in the control center.

### AVSessionController

An object held by the media session controller, used to control the playback behavior of the media session provider app, obtain the app's playback information, listen for changes in the playback state of audio/video apps, and ensure synchronization of media session information between audio/video apps and the control center.

### AVSessionDescriptor

An object that describes information related to a media session, including attributes such as the session ID (`sessionId`), media session type (`type`), custom media session name (`sessionTag`), app information to which the media session belongs (`elementName`), and whether it is a top session (`isTopSession`).

### AVSessionManager

A module that provides media session management capabilities. It allows you to create media sessions (AVSession), create media session controllers (AVSessionController), send system control events, and listen for media session state changes.

### AVSessionType

Parameters that define the media session type, including five types: `audio` (audio session), `video` (video session), `voice_call` (voice call session), `video_call` (video call session), and `photo` (photo session). Different types determine the control template style displayed in the control center.

## B

### BackgroundPlayMode

Indicates whether to continue playback when the app goes to the background. It includes two modes: `ENABLE_BACKGROUND_PLAY` (supports background playback) and `DISABLE_BACKGROUND_PLAY` (does not support background playback). The system determines whether to display the system Live View when the app goes to the background based on this mode.

## D

### DisplayTag

A tag that identifies the media audio source, used to display media audio information in the control center. Currently, the `TAG_AUDIO_VIVID` tag is supported, indicating that the audio source is Audio Vivid.

## P

### ProtocolType

An enumeration of protocol types supported by remote devices, including `TYPE_LOCAL` (local device), `TYPE_CAST_PLUS_STREAM` (Cast+ Stream mode), `TYPE_DLNA` (DLNA protocol), and `TYPE_CAST_PLUS_AUDIO` (PCM mode). It is used to identify the communication protocols supported by a casting device.

## T

### TopSession

The media session with the highest priority in the system, for example, the session that is currently playing. A media session controller can communicate directly with the top session without obtaining the corresponding controller, for example, by sending playback control commands and key events directly to the top session.