# Screen Capture FAQs

<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @zzs_911-->
<!--Designer: @stupig001-->
<!--Tester: @xdlinc-->
<!--Adviser: @w_Machine_cc-->

## Error Code AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT Is Reported When Starting Screen Capture

This error occurs when the number of instances exceeds the system limit. The current specification allows a maximum of two instances per data format. You are advised to release any extra instances before creating new ones.

Screen capture session limit policy:

1. A maximum of four client applications are allowed. Examples include simultaneous use of screen sharing in a meeting, screen casting, background music recognition, and system screen capture.

2. Each application can create up to two instances per operational mode (saving to files or saving as streams). A typical use case is simultaneously recording meeting content while sharing the screen during an online meeting.
