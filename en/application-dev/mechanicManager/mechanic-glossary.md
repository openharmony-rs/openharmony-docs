# Glossary
<!--Kit: Mechanic Kit-->
<!--Subsystem: Mechanic-->
<!--Owner: @qxqxqxqxqx-->
<!--Designer: @peter__1024-->
<!--Tester: @Aullar-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=1cf8d115c7de6fdcd15a83e20db0f6251dd6dd61 translatedAt=2026-11-03T09:17:02.335Z pushedAt=2026-11-03T09:17:02.335Z nl=1 -->

## C

### Camera Tracking
A feature that uses a camera to identify a target and automatically rotates a mechanic device to keep the target in the frame. It supports enabling and disabling tracking and configuring the layout for intelligent camera tracking.

## G

### Gimbal Device
A portable mechanic device with a stabilized, three-axis rotating platform that can carry a camera for stable photography and intelligent tracking.

## M

### Mechanic Device
A smart hardware device, such as a gimbal, that connects to a host over Bluetooth and receives rotation control commands to support stable photography and target tracking with a camera.

### Mechanic Kit
A kit for interacting with mechanic devices. It provides device connection management, camera tracking control, rotation control, and state monitoring for developing applications that work with mechanic devices.

### Mechanic Kit Protocol
A compatibility specification for mechanic devices and Mechanic Kit. Devices must comply with this protocol to be recognized and controlled by Mechanic Kit. It is distinct from Mechanic Kit, the software that implements the specification, and a mechanic device, the hardware that complies with it.

## R

### Rotation Axis
A direction of rotational freedom of a mechanic device, including yaw, roll, and pitch. Each axis can be independently enabled or disabled and has its own limit state, allowing the device's spatial rotation capabilities to be described and controlled.

### Rotation Axis Limit
A runtime state indicating whether a rotation axis has reached its maximum angle in a direction. The three states are unrestricted, restricted in the negative direction, and restricted in the positive direction. This state determines whether the device can continue rotating in that direction. Unlike a static rotation angle limit, it describes the axis's current restriction state.
