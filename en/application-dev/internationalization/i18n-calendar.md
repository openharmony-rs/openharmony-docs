# Calendar Setting

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @yliupy-->
<!--Designer: @sunyaozu-->
<!--Tester: @lpw_work-->
<!--Adviser: @ningningW-->

## Feature Description

Users in different locales use different calendars. Most locales use the Gregorian calendar, while users in some other locales use other calendars, such as the Chinese calendar, Islamic calendar, or Hebrew calendar. The time and date on a calendar are calculated based on the calendar system and adjusted for time zones and daylight saving time. Therefore, users need to set a calendar that conforms to local conventions. The i18n module provides the [Calendar](../reference/apis-localization-kit/js-apis-i18n.md#calendar) class, which allows you to set the calendar, date, time zone, first day of the week, and the minimum number of days in the first week of the year. In addition, you can determine whether a specific day is a weekend in the calendar and calculate the difference in days. During application development, you can choose to use different functions based on your service requirements.

## How to Develop

The following uses viewing the Chinese calendar date corresponding to a Gregorian calendar date as an example to illustrate how to use the [Calendar](../reference/apis-localization-kit/js-apis-i18n.md#calendar) class APIs.

1. Import the module.

   <!-- @[import_module](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/International/Internationalization/entry/src/main/ets/i18napplication/CalendarSetting.ets) -->

   ``` TypeScript
   import { i18n } from '@kit.LocalizationKit';
   ```

2. Work with calendar dates.

- Use Gregorian calendar dates.

   <!-- @[check_and_set_date](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/International/Internationalization/entry/src/main/ets/i18napplication/CalendarSetting.ets) -->

   ``` TypeScript
   let calendar: i18n.Calendar = i18n.getCalendar('zh-Hans', 'gregory');
   // Set the date and time of the Calendar object to 2022.06.13 08:00:00.
   calendar.setTime(new Date(2022, 5, 13, 8, 0, 0));
   calendar.setTime(10540800000);

   // Set the date and time of the Calendar object to 2022.06.13 08:00:00.
   calendar.set(2022, 5, 13, 8, 0, 0);

   // Set the time zone for the Calendar object.
   calendar.setTimeZone('Asia/Shanghai');

   // Obtain the time zone for the Calendar object.
   let timezone = calendar.getTimeZone(); // timezone = 'Asia/Shanghai'

   // Obtain the start day of a week for the Calendar object.
   let firstDayOfWeek = calendar.getFirstDayOfWeek(); // firstDayOfWeek = 1

   // Set the start day of a week for the Calendar object.
   calendar.setFirstDayOfWeek(1);

   // Obtain the minimum number of days in the first week of a year for the Calendar object.
   let minimalDaysInFirstWeek = calendar.getMinimalDaysInFirstWeek(); // minimalDaysInFirstWeek = 1

   // Set the minimum number of days in the first week of a year for the Calendar object.
   calendar.setMinimalDaysInFirstWeek(3);

   // Obtain the value of the specified field in the Calendar object.
   let year = calendar.get('year'); // year = 2022

   // Obtain the localized name of the Calendar object.
   let calendarName = calendar.getDisplayName('zh-Hans'); // calendarName = 'Gregorian calendar'gorian calendar'

   // Check whether a given date is a weekend for the Calendar object.
   let isWeekend = calendar.isWeekend(new Date(2023, 9, 15)); // isWeekend = true

   // Perform addition and subtraction operations on the specified field of the Calendar object.
   calendar.set(2023, 10, 15);
   calendar.add('date', 2);
   let day = calendar.get('date'); // day = 17

   // Check the number of days between the Calendar object and the specified date.
   let daysDifference = calendar.compareDays(new Date(2023, 10, 15)); // daysDifference = -3
   ```

- Obtain the Chinese calendar date corresponding to a Gregorian calendar date.

   <!-- @[get_lunar_date](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/International/Internationalization/entry/src/main/ets/i18napplication/CalendarSetting.ets) -->

   ``` TypeScript
   let calendarChinese: i18n.Calendar = i18n.getCalendar('zh-Hans', 'chinese');
   // Set the Gregorian calendar date to the calendar object, with the date and time as 2023.07.25 08:00:00
   calendarChinese.setTime(new Date(2023, 6, 25, 8, 0, 0));

   // Obtain the year, month, and day of the lunar calendar.
   let yearChinese = calendarChinese.get('year'); // year = 40, refers to the sexagenary cycle year 40, ranging from 1 to 60
   let monthChinese = calendarChinese.get('month'); // month = 5, refers to June
   let dayChinese = calendarChinese.get('date'); // day = 8, refers to the 8th day
   ```

**Table 1** List of supported calendars

| Type| Name| 
| -------- | -------- |
| buddhist | Buddhist calendar| 
| chinese | Lunar calendar| 
| coptic | Coptic calendar| 
| ethiopic | Ethiopian calendar| 
| hebrew | Hebrew calendar| 
| gregory | Gregorian calendar| 
| indian | Indian calendar| 
| islamic_civil | Islamic calendar (civil epoch)| 
| islamic_tbla | Islamic calendar (tabular)| 
| islamic_umalqura | Islamic calendar (Umm al-Qura)| 
| japanese | Japanese calendar| 
| persian | Persian calendar| 

<!--RP1--><!--RP1End-->