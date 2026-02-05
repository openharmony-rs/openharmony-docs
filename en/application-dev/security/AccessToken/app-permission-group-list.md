# Application Permission Groups

<!--Kit: Ability Kit-->
<!--Subsystem: Security-->
<!--Owner: @xia-bubai-->
<!--Designer: @linshuqing; @hehehe-li-->
<!--Tester: @leiyuqian-->
<!--Adviser: @zengyawen-->

## Usage Guidelines

- It will be helpful if you understand [permission groups and permissions](app-permission-mgmt-overview.md#permission-groups-and-permissions) before requesting permission groups for your application.

- It helps minimize the number of dialogs that are presented to the user when an application requests closely related permissions. The user simply needs to grant the permissions all at once, except for the Location, Contacts, <!--Del-->Call Logs, Phone, Messaging,<!--DelEnd--> and Calendar permission groups.

  The following uses the Location and Camera permission groups as an example.

  - When an application requests only the ohos.permission.APPROXIMATELY_LOCATION permission (belong to the Location permission group), a dialog box containing only the requested permission will be displayed to request user authorization.
  - When an application requests the ohos.permission.APPROXIMATELY_LOCATION and ohos.permission.LOCATION permissions (belonging to the Location permission group), a dialog box containing only the requested permissions will be displayed to request user authorization.
  - When an application requests ohos.permission.APPROXIMATELY_LOCATION (belonging to the Location permission group) and ohos.permission.CAMERA (belonging to the Camera permission group), two dialog boxes will be displayed to request the location and camera permissions, respectively.

- The following lists the permission groups supported by the system. For details about the meaning of each permission, see [the permission list](permissions-for-all-user.md).

## Location <!--Del-->Information<!--DelEnd-->

- [ohos.permission.LOCATION_IN_BACKGROUND](permissions-for-all-user.md#ohospermissionlocation_in_background)

- [ohos.permission.LOCATION](permissions-for-all-user.md#ohospermissionlocation)

- [ohos.permission.APPROXIMATELY_LOCATION](permissions-for-all-user.md#ohospermissionapproximately_location)

## Camera

- [ohos.permission.CAMERA](permissions-for-all-user.md#ohospermissioncamera)

## Microphone

- [ohos.permission.MICROPHONE](permissions-for-all-user.md#ohospermissionmicrophone)

## Contacts

- [ohos.permission.READ_CONTACTS](restricted-permissions.md#ohospermissionread_contacts)

- [ohos.permission.WRITE_CONTACTS](restricted-permissions.md#ohospermissionwrite_contacts)

## Calendar

- [ohos.permission.READ_CALENDAR](permissions-for-all-user.md#ohospermissionread_calendar)
 
- [ohos.permission.WRITE_CALENDAR](permissions-for-all-user.md#ohospermissionwrite_calendar)
 
- [ohos.permission.READ_WHOLE_CALENDAR](restricted-permissions.md#ohospermissionread_whole_calendar)

- [ohos.permission.WRITE_WHOLE_CALENDAR](restricted-permissions.md#ohospermissionwrite_whole_calendar)

<!--RP1-->
## Fitness

- [ohos.permission.ACTIVITY_MOTION](permissions-for-all-user.md#ohospermissionactivity_motion)

## Body Sensors

- [ohos.permission.READ_HEALTH_DATA](permissions-for-all-user.md#ohospermissionread_health_data)
<!--RP1End-->

## Images and Videos

- [ohos.permission.WRITE_IMAGEVIDEO](restricted-permissions.md#ohospermissionwrite_imagevideo)

- [ohos.permission.READ_IMAGEVIDEO](restricted-permissions.md#ohospermissionread_imagevideo)

- [ohos.permission.MEDIA_LOCATION](permissions-for-all-user.md#ohospermissionmedia_location)

<!--RP4--><!--RP4End-->

## Music and Audio

- [ohos.permission.WRITE_AUDIO](restricted-permissions.md#ohospermissionwrite_audio)

- [ohos.permission.READ_AUDIO](restricted-permissions.md#ohospermissionread_audio)

<!--RP2-->
## Ad Tracking

- [ohos.permission.APP_TRACKING_CONSENT](permissions-for-all-user.md#ohospermissionapp_tracking_consent)
<!--RP2End-->

<!--Del-->
## Installed Bundle List

- [ohos.permission.GET_INSTALLED_BUNDLE_LIST](permissions-for-system-apps-user.md#ohospermissionget_installed_bundle_list)
<!--DelEnd-->

<!--RP3-->
## Multi-device Collaboration

- [ohos.permission.DISTRIBUTED_DATASYNC](permissions-for-all-user.md#ohospermissiondistributed_datasync)

## Bluetooth

- [ohos.permission.ACCESS_BLUETOOTH](permissions-for-all-user.md#ohospermissionaccess_bluetooth)

## NearLink

- [ohos.permission.ACCESS_NEARLINK](permissions-for-all-user.md#ohospermissionaccess_nearlink)
<!--RP3End-->

<!--Del-->
## Phone

- [ohos.permission.ANSWER_CALL](permissions-for-system-apps-user.md#ohospermissionanswer_call)

- [ohos.permission.MANAGE_VOICEMAIL](permissions-for-system-apps-user.md#ohospermissionmanage_voicemail)

## Call Logs

- [ohos.permission.READ_CALL_LOG](permissions-for-system-apps-user.md#ohospermissionread_call_log)

- [ohos.permission.WRITE_CALL_LOG](permissions-for-system-apps-user.md#ohospermissionwrite_call_log)

## Messaging

- [ohos.permission.READ_CELL_MESSAGES](permissions-for-system-apps-user.md#ohospermissionread_cell_messages)

- [ohos.permission.READ_MESSAGES](permissions-for-system-apps-user.md#ohospermissionread_messages)

- [ohos.permission.RECEIVE_MMS](permissions-for-system-apps-user.md#ohospermissionreceive_mms)

- [ohos.permission.RECEIVE_SMS](permissions-for-system-apps-user.md#ohospermissionreceive_sms)

- [ohos.permission.RECEIVE_WAP_MESSAGES](permissions-for-system-apps-user.md#ohospermissionreceive_wap_messages)

- [ohos.permission.SEND_MESSAGES](permissions-for-system-apps-user.md#ohospermissionsend_messages)
<!--DelEnd-->

## Pasteboard

- [ohos.permission.READ_PASTEBOARD](restricted-permissions.md#ohospermissionread_pasteboard)

## Screenshots

- [ohos.permission.CUSTOM_SCREEN_CAPTURE](permissions-for-all-user.md#ohospermissioncustom_screen_capture)

## Directory

> **NOTE**
> <br>The permissions are available only to 2-in-1 device applications.

- [ohos.permission.READ_WRITE_DOWNLOAD_DIRECTORY](permissions-for-all-user.md#ohospermissionread_write_download_directory)

- [ohos.permission.READ_WRITE_DESKTOP_DIRECTORY](restricted-permissions.md#ohospermissionread_write_desktop_directory)
- [ohos.permission.READ_WRITE_DOCUMENTS_DIRECTORY](permissions-for-all-user.md#ohospermissionread_write_documents_directory)

## Files<sup>(deprecated)</sup>

> **NOTE**
> Since API version 9, alternatives are supported.

<!--Del-->
- ohos.permission.READ_DOCUMENT

- ohos.permission.WRITE_DOCUMENT
<!--DelEnd-->
- ohos.permission.READ_MEDIA

- ohos.permission.WRITE_MEDIA

**Alternative solution**:

- To read or write images/videos in the media library:

  - Recommended solution (no permission required): Use [Picker](../../media/medialibrary/photoAccessHelper-photoviewpicker.md) to read images and videos from the media library. Use the [Save button/Authorization dialog box](../../media/medialibrary/photoAccessHelper-savebutton.md) to save images and videos from the media library.
  - Request the restricted permission [ohos.permission.READ_IMAGEVIDEO](restricted-permissions.md#ohospermissionread_imagevideo) or [ohos.permission.WRITE_IMAGEVIDEO](restricted-permissions.md#ohospermissionwrite_imagevideo).

- To read and write audio clips in the media library:

  Request the restricted permission [ohos.permission.READ_AUDIO](restricted-permissions.md#ohospermissionread_audio) or [ohos.permission.WRITE_AUDIO](restricted-permissions.md#ohospermissionwrite_audio).

- Read files in the file manager.

  Use the file Picker to read documents in **Files**. For details, see [Selecting Documents](../../file-management/select-user-file.md#selecting-documents) and [Saving Documents](../../file-management/save-user-file.md#saving-documents).
