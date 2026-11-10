# Automatic Scene Configuration Kit Glossary

<!--Kit: Automatic Scene Configuration Kit-->
<!--Subsystem: Customization-->
<!--Owner: @weredust-->
<!--Designer: @weredust-->
<!--Tester: @weredust-->
<!--Adviser: @weredust-->
<!-- md-trans-meta sourceCommit=3194fdbc42d6357f420eb498f6d963c04a35b419 translatedAt=2026-11-06T12:33:16.132Z pushedAt=2026-11-09T12:06:56.233Z nl=1 -->

This document introduces the terms related to Automatic Scene Configuration Kit.

## A

### allowedApps; Application Trustlist
A set of application package names specified in the Assessment Configuration that are allowed to run during the assessment. Applications not in the trustlist cannot run during the assessment.

### Assessment Mode; Evaluation Mode
After an assessment begins, the system enters an operating state in which some system capabilities are restricted, used to prevent users from cheating or leaking assessment content. Assessment Mode is entered after the user confirms it in a confirmation dialog, and is exited by ending the assessment or when the assessment is interrupted.

### AssessmentConfig; Assessment Configuration
Configuration information passed in when calling the begin interface, containing two fields: the maximum assessment duration and the application trustlist allowedApps.

### AssessmentErrorCode
An enumeration that indicates the result of an assessment operation and the reason for assessment interruption. Its members include OK, USER_CANCEL, TIMEOUT, SYSTEM_ERROR, and ENV_ANOMALY.

### AssessmentInterruptInfo; Assessment Interruption Information
Information passed through the onInterrupted callback when an assessment is interrupted, including the interruption reason code and a detailed description of the interruption reason in message.

## D

### duration; Maximum Assessment Duration
A field in the assessment configuration that specifies the maximum duration of the current assessment, in milliseconds, with an upper limit on the value. When the value is 0, the default duration is used, and the default duration is the same as the upper limit. When the maximum assessment duration is reached, the assessment is interrupted, and the interruption reason code is TIMEOUT.

## I

### IAssessmentCallback
The callback interface registered when the begin API is called, used to receive assessment process events. It contains three methods: onBegin for assessment start, onInterrupted for assessment interruption, and onEnd for assessment end.
