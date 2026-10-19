# Distributed AVSession Overview (for System Applications Only)
<!--Kit: AVSession Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @gcw_7KSyM10J; @devil_red-->
<!--Designer: @gcw_7KSyM10J-->
<!--Tester: @chenmingxi1_huawei-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=6db95933f92c36be892f64316b822565946ecf49 translatedAt=2026-09-03T09:01:43.972Z pushedAt=2026-09-03T09:04:52.943Z -->

With distributed AVSession, OpenHarmony allows users to project locally played media to a distributed device for a better playback effect. For example, users can project audio played on a tablet to a smart speaker.

After the user initiates a casting, the media information is synchronized to the distributed device in real time, and the user can control the playback (for example, previous, next, play, and pause) on the distributed device. From the perspective of the user, the playback control operation on the distributed device is the same as that on the local device.


## Interaction Process

After the local device is paired with a distributed device, the controller on the local device projects media to the distributed device through AVSessionManager, thereby implementing a distributed AVSession. The interaction process is shown below.

![Distributed AVSession Interaction Process](figures/distributed-avsession-interaction-process.png)

The AVSession service on the distributed device automatically creates an AVSession object for information synchronization with the local device. The information to synchronize includes the session information, control commands, and events.

## Distributed AVSession Process

After a user initiates distributed casting, a corresponding media session is automatically created on the distributed device. The media sessions on both sides can interact with each other in the following ways:

1. After receiving an audio device switching command, the AVSession service on the local device synchronizes the session information to the distributed device.

2. The controller (for example, Media Controller) on the distributed device detects the new AVSession object and creates an AVSessionController object for it.

3. Through the AVSessionController object, the controller on the distributed device sends a control command to the AVSession object on the local device.

4. After receiving a remote control command, the local media session on the local device notifies the local audio app through a callback.

5. The AVSession object on the local device synchronizes the new session information to the controller on the distributed device in real time.

6. After the connection to the distributed device is disconnected, the audio is switched back to the local device and paused. (The audio module completes the switchback, and the media session notifies the app to pause.)

## Distributed AVSession Scenarios

There are two scenarios for casting implemented using the distributed AVSession:

- System-level casting: The controller (for example, Media Controller) initiates a distributed casting.

  This type of casting takes effect for all applications. After a system casting, all audio files on the local device are played from the distributed device by default.

- App casting: An audio/video app initiates distributed casting within the app by integrating the casting component. (This feature is not yet supported.)

  This type of casting takes effect for a single application. After an application casting, audio of the application on the local device is played from the distributed device, and audio of other applications is still played from the local device.

In addition, casting supports preemption. An app that initiates casting later can preempt the previously casting app and play audio on the distributed device.

## Relationship Between Distributed AVSession and Distributed Audio Playback

When the media session service implements distributed media sessions for cross-device casting, the internal logic can be described as follows:

- APIs related to [distributed audio playback (for system applications only)](../audio/distributed-audio-playback-sys.md) are called to project audio streams to the distributed device.

- The distributed capability is used to project the session metadata to the distributed device for display.

Therefore, casting through a distributed media session not only enables audio playback on the distributed device, but also allows the distributed device to display playback information. In addition, with the media session mechanism, you can control the audio being played on the distributed device.
