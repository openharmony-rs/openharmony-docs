# Glossary

<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leo_ysl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=021205bc8ebadd9980b6ea541ea0bcdd8a361b93 translatedAt=2026-08-22T02:07:55.287Z pushedAt=2026-08-22T06:47:49.892Z -->

## C

### Camera Input

An input device object in the camera framework that manages the opening, closing, and error callbacks of a camera device. It serves as the input source for camera outputs such as preview, photo capture, and video recording.

### Camera Manager

The core management class of the camera framework. It obtains the camera device list, creates input/output streams, manages sessions and flash status, and serves as the primary entry point for using camera features.

### Camera Output Capability

The set of preview, photo capture, and video recording profiles and metadata types supported by a camera device, used to determine the output capabilities available on the device before creating a session.

### Camera Position

The installation position type of a camera device on a terminal, such as front, rear, or external, used to distinguish and select cameras at different positions.

### Camera Type

The functional type of a camera device, such as wide-angle, ultra-wide-angle, and telephoto, used to identify the camera type.

### Capture Session

The core session object in the camera framework that connects inputs and outputs. It is responsible for stream configuration, submission, and running control. All preview, photo capture, and video recording operations must be completed in the session.

### Connection Type

The way a camera device connects to the system, such as built-in, USB external, or remote connection, used to determine whether the camera is an external device.

## E

### Exposure Mode

The method for controlling camera exposure, including locked exposure, automatic exposure, continuous automatic exposure, and manual exposure.

## F

### Flash Mode

The working mode of the camera flash, such as off, auto, and always on, used to supplement lighting in low-light environments.

### Focus Mode

The control method for camera focusing, including manual focus, continuous auto focus, and auto focus.

### Frame Rate Range

The range between the minimum and maximum frame rates of camera output, used to control the smoothness of preview or video recording.

## I

### Image Rotation

The rotation angle (0°/90°/180°/270°) applied to an image based on the device orientation during photo capture or preview, ensuring that the image orientation matches the device holding direction.

## M

### Metadata Output

A stream object in the camera framework used to output metadata such as face detection, which calls back the detected metadata objects to the application in real time.

### Metadata Object Type

The target type of metadata detection, such as face, human body, and pet, used to specify the category of metadata to be detected.

### Moving Photo

A combined media format of a "high-definition still photo" and a "short video". When a moving photo is captured, approximately 1.5 seconds of frames and audio before and after the shutter is pressed are recorded.

## P

### Photo Capture Setting

Parameter settings for a single photo capture, including the quality level, rotation angle, geographic location, and mirror switch, to customize the photo output effect.

### Photo Output

A stream object in the camera framework used to output captured images. It handles capture triggering, callback notification, and photo quality and mirroring control.

### Preview Output

A stream object in the camera framework used to output the real-time preview, rendering the frames captured by the camera to the screen in real time for user preview.

## S

### Smooth Zoom

A zoom method that continuously adjusts the focal length ratio to achieve smooth image scaling. It enables smooth zoom transitions during video recording, avoiding abrupt jumps in the image.

## V

### Video Output

An object in the camera framework that outputs video streams, responsible for starting and stopping recording, frame rate control, and video rotation information.

### Video Stabilization Mode

A functional mode that compensates for image shake through algorithms during video recording, used to improve image stability when recording handheld videos.