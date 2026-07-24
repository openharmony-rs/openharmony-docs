# Glossary

<!--Kit: AVSession Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @ccfriend; @devil_red-->
<!--Designer: @ccfriend-->
<!--Tester: @chenmingxi1_huawei-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=45526eba67080b876eb51af31a33be43ae26f701 translatedAt=2026-07-13T13:20:22.365Z pushedAt=2026-07-20T14:00:02.457Z -->

## A

### Audio & Video Session (AVSession)

A communication channel between a media application and a media controller for exchanging playback information and control commands. One end is connected to the media application, and the other is connected to a controller, such as the playback control center or a voice assistant. It is the core concept of AVSession Kit and provides unified media presentation and playback control capabilities.

### AVMetadata

A collection of metadata that describes a media item. It includes properties such as the media ID (`assetId`), title (`title`), author (`author`), album (`album`), writer (`writer`), duration (`duration`), lyrics (`lyric`), cover image (`mediaImage`), and audio source tag (`displayTags`). Media applications use this metadata to present media information in the playback control center.

### AVMusicTemplate

A class that encapsulates interactions with the playback control center. It includes properties such as the session ID (`sessionId`) and session tag (`sessionTag`), and provides APIs for exchanging data with the playback control center. Media applications can use this class to report media information and respond to playback control commands, reducing application-side implementation effort.

### AVPlaybackState

A collection of properties that describes the current playback state. It includes the playback state (`state`), playback position (`position`), playback speed (`speed`), buffered time (`bufferedTime`), loop mode (`loopMode`), favorite status (`isFavorite`), active media ID (`activeItemId`), and custom media data (`extras`). It is used to present playback progress and playback controls in the playback control center.

### AVSessionController

An object held by a media session controller to control playback in the application that provides the media session. It can obtain playback information and listen for playback state changes in the media application, keeping media session information synchronized between the media application and the playback control center.

### AVSessionDescriptor

An object that describes a media session. It includes properties such as the media session ID (`sessionId`), media session type (`type`), custom media session name (`sessionTag`), information about the application to which the media session belongs (`elementName`), and whether the session is the top session (`isTopSession`).

### AVSessionManager

A module that provides media session management capabilities. It can create media sessions (`AVSession`) and media session controllers (`AVSessionController`), send system control events, and listen for media session state changes.

### AVSessionType

An enumeration that defines media session types, including `audio` for audio sessions, `video` for video sessions, `voice_call` for voice call sessions, `video_call` for video call sessions, and `photo` for photo sessions. The session type determines the playback control template displayed in the playback control center.

## B

### BackgroundPlayMode

An enumeration that specifies whether playback continues after an application enters the background. It includes `ENABLE_BACKGROUND_PLAY`, which allows background playback, and `DISABLE_BACKGROUND_PLAY`, which disables background playback. The system uses this mode to determine whether to display a system live window after the application enters the background.

## D

### DisplayTag

A tag that identifies the audio source of media content. It is used to display audio source information in the playback control center. Currently, `TAG_AUDIO_VIVID` is supported to indicate that the audio source uses Audio Vivid.

## P

### ProtocolType

An enumeration that defines the protocol types supported by a remote device. It includes `TYPE_LOCAL` for a local device, `TYPE_CAST_PLUS_STREAM` for Cast+ Stream mode, `TYPE_DLNA` for the DLNA protocol, and `TYPE_CAST_PLUS_AUDIO` for PCM mode. It is used to identify the communication protocols supported by a casting device.

## T

### TopSession

The media session with the highest priority in the system, typically a session that is currently playing. A media session controller can communicate directly with the top session without first obtaining its corresponding controller. For example, it can send playback control commands and key events directly to the top session.