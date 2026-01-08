# Calendar Setting

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @yliupy-->
<!--Designer: @sunyaozu-->
<!--Tester: @lpw_work-->
<!--Adviser: @Brilliantry_Rui-->

## Use Cases

Users in different locales use different calendars. To be specific, the Gregorian calendar is used in most locales, whereas calendars such as the lunar, Islamic, and Hebrew calendars are used in some other locales. The time and date on the calendar are calculated based on the calendar and may vary according to the time zone and DST. Therefore, the system should allow users to choose calendars that comply with their local habits. This is made real with the complete set of APIs provided by the [Calendar](../reference/apis-localization-kit/js-apis-i18n.md#calendar8) class. Besides setting the calendar type, date (year, month, and day), time zone, start date of a week, and minimum number of days in the first week of a year, users can even determine whether a day is a weekend on the calendar and calculate the day difference between two dates. During application development, you can choose functions that suit your needs in a flexible manner.

## How to Develop

The following illustrates how to view the lunar calendar date corresponding to the Gregorian calendar date as an example to help you understand the usage of [Calendar](../reference/apis-localization-kit/js-apis-i18n.md#calendar8) APIs.

1. Import the related modules.

   <!-- @[import_module](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/International/Internationalization/entry/src/main/ets/i18napplication/CalendarSetting.ets) -->
   
   ``` TypeScript
   import { i18n } from '@kit.LocalizationKit';
   ```

2. Application scenario.
- Configure the Gregorian calendar.

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
   let calendarName = calendar.getDisplayName('zh-Hans'); // calendarName = 'Gregorian calendar'
   
   // Check whether a given date is a weekend for the Calendar object.
   let isWeekend = calendar.isWeekend(new Date(2023, 9, 15)); // isWeekend = true
   
   // Perform addition and subtraction operations on the specified field of the Calendar object.
   calendar.set(2023, 10, 15);
   calendar.add('date', 2);
   let day = calendar.get('date'); // day = 17
   
   // Check the number of days between the Calendar object and the specified date.
   let daysDifference = calendar.compareDays(new Date(2023, 10, 15)); // daysDifference = -3
   ```

- Obtain the lunar calendar date corresponding to a Gregorian calendar date.

   <!-- @[get_lunar_date](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/International/Internationalization/entry/src/main/ets/i18napplication/CalendarSetting.ets) -->
   
   ``` TypeScript
   let calendarChinese: i18n.Calendar = i18n.getCalendar('zh-Hans', 'chinese');
   // Pass the Gregorian calendar date to the Calendar object, with the date and time being 2023.07.25 08:00:00.
   calendarChinese.setTime(new Date(2023, 6, 25, 8, 0, 0));
   
   // Obtain the year, month, and day of the lunar calendar.
   let yearChinese = calendarChinese.get('year'); // year = 40 indicates the age of the trunk branch. The value ranges from 1 to 60.
   let monthChinese = calendarChinese.get('month'); // month = 5 indicates June.
   let dayChinese = calendarChinese.get('date'); // day = 8 indicates the eighth day.
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
