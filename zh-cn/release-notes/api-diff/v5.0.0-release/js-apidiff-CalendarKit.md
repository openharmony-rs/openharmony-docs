| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|权限变更|类名：CalendarManager；<br>API声明：createCalendar(calendarAccount: CalendarAccount): Promise\<Calendar>;<br>差异内容：ohos.permission.WRITE_CALENDAR or ohos.permission.WRITE_WHOLE_CALENDAR|类名：CalendarManager；<br>API声明：createCalendar(calendarAccount: CalendarAccount): Promise\<Calendar>;<br>差异内容：ohos.permission.WRITE_CALENDAR|api/@ohos.calendarManager.d.ts|
|权限变更|类名：CalendarManager；<br>API声明：createCalendar(calendarAccount: CalendarAccount, callback: AsyncCallback\<Calendar>): void;<br>差异内容：ohos.permission.WRITE_CALENDAR or ohos.permission.WRITE_WHOLE_CALENDAR|类名：CalendarManager；<br>API声明：createCalendar(calendarAccount: CalendarAccount, callback: AsyncCallback\<Calendar>): void;<br>差异内容：ohos.permission.WRITE_CALENDAR|api/@ohos.calendarManager.d.ts|
|权限变更|类名：CalendarManager；<br>API声明：deleteCalendar(calendar: Calendar): Promise\<void>;<br>差异内容：ohos.permission.WRITE_CALENDAR or ohos.permission.WRITE_WHOLE_CALENDAR|类名：CalendarManager；<br>API声明：deleteCalendar(calendar: Calendar): Promise\<void>;<br>差异内容：ohos.permission.WRITE_CALENDAR|api/@ohos.calendarManager.d.ts|
|权限变更|类名：CalendarManager；<br>API声明：deleteCalendar(calendar: Calendar, callback: AsyncCallback\<void>): void;<br>差异内容：ohos.permission.WRITE_CALENDAR or ohos.permission.WRITE_WHOLE_CALENDAR|类名：CalendarManager；<br>API声明：deleteCalendar(calendar: Calendar, callback: AsyncCallback\<void>): void;<br>差异内容：ohos.permission.WRITE_CALENDAR|api/@ohos.calendarManager.d.ts|
|权限变更|类名：CalendarManager；<br>API声明：getCalendar(calendarAccount?: CalendarAccount): Promise\<Calendar>;<br>差异内容：ohos.permission.READ_CALENDAR or ohos.permission.READ_WHOLE_CALENDAR|类名：CalendarManager；<br>API声明：getCalendar(calendarAccount?: CalendarAccount): Promise\<Calendar>;<br>差异内容：ohos.permission.READ_CALENDAR|api/@ohos.calendarManager.d.ts|
|权限变更|类名：CalendarManager；<br>API声明：getCalendar(calendarAccount: CalendarAccount, callback: AsyncCallback\<Calendar>): void;<br>差异内容：ohos.permission.READ_CALENDAR or ohos.permission.READ_WHOLE_CALENDAR|类名：CalendarManager；<br>API声明：getCalendar(calendarAccount: CalendarAccount, callback: AsyncCallback\<Calendar>): void;<br>差异内容：ohos.permission.READ_CALENDAR|api/@ohos.calendarManager.d.ts|
|权限变更|类名：CalendarManager；<br>API声明：getCalendar(callback: AsyncCallback\<Calendar>): void;<br>差异内容：ohos.permission.READ_CALENDAR or ohos.permission.READ_WHOLE_CALENDAR|类名：CalendarManager；<br>API声明：getCalendar(callback: AsyncCallback\<Calendar>): void;<br>差异内容：ohos.permission.READ_CALENDAR|api/@ohos.calendarManager.d.ts|
|权限变更|类名：CalendarManager；<br>API声明：getAllCalendars(): Promise\<Calendar[]>;<br>差异内容：ohos.permission.READ_CALENDAR or ohos.permission.WRITE_WHOLE_CALENDAR|类名：CalendarManager；<br>API声明：getAllCalendars(): Promise\<Calendar[]>;<br>差异内容：ohos.permission.READ_CALENDAR|api/@ohos.calendarManager.d.ts|
|权限变更|类名：CalendarManager；<br>API声明：getAllCalendars(callback: AsyncCallback\<Calendar[]>): void;<br>差异内容：ohos.permission.READ_CALENDAR or ohos.permission.READ_WHOLE_CALENDAR|类名：CalendarManager；<br>API声明：getAllCalendars(callback: AsyncCallback\<Calendar[]>): void;<br>差异内容：ohos.permission.READ_CALENDAR|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：CalendarManager；<br>API声明：editEvent(event: Event): Promise\<number>;<br>差异内容：editEvent(event: Event): Promise\<number>;|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：Event；<br>API声明：identifier?: string;<br>差异内容：identifier?: string;|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：Event；<br>API声明：isLunar?: boolean;<br>差异内容：isLunar?: boolean;|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：RecurrenceRule；<br>API声明：count?: number;<br>差异内容：count?: number;|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：RecurrenceRule；<br>API声明：interval?: number;<br>差异内容：interval?: number;|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：RecurrenceRule；<br>API声明：excludedDates?: number[];<br>差异内容：excludedDates?: number[];|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：RecurrenceRule；<br>API声明：daysOfWeek?: number[];<br>差异内容：daysOfWeek?: number[];|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：RecurrenceRule；<br>API声明：daysOfMonth?: number[];<br>差异内容：daysOfMonth?: number[];|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：RecurrenceRule；<br>API声明：daysOfYear?: number[];<br>差异内容：daysOfYear?: number[];|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：RecurrenceRule；<br>API声明：weeksOfMonth?: number[];<br>差异内容：weeksOfMonth?: number[];|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：RecurrenceRule；<br>API声明：weeksOfYear?: number[];<br>差异内容：weeksOfYear?: number[];|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：RecurrenceRule；<br>API声明：monthsOfYear?: number[];<br>差异内容：monthsOfYear?: number[];|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：Attendee；<br>API声明：role?: AttendeeRole;<br>差异内容：role?: AttendeeRole;|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：calendarManager；<br>API声明：export enum AttendeeRole<br>差异内容：export enum AttendeeRole|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：AttendeeRole；<br>API声明：ORGANIZER = 'organizer'<br>差异内容：ORGANIZER = 'organizer'|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：AttendeeRole；<br>API声明：PARTICIPANT = 'participant'<br>差异内容：PARTICIPANT = 'participant'|api/@ohos.calendarManager.d.ts|
