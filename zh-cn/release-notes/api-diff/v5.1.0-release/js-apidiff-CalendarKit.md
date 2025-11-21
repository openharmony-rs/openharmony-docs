| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|权限变更|类名：CalendarManager；<br>API声明：createCalendar(calendarAccount: CalendarAccount): Promise\<Calendar>;<br>差异内容：ohos.permission.WRITE_CALENDAR or ohos.permission.WRITE_WHOLE_CALENDAR|类名：CalendarManager；<br>API声明：createCalendar(calendarAccount: CalendarAccount): Promise\<Calendar>;<br>差异内容：ohos.permission.WRITE_CALENDAR|api/@ohos.calendarManager.d.ts|
|权限变更|类名：CalendarManager；<br>API声明：createCalendar(calendarAccount: CalendarAccount, callback: AsyncCallback\<Calendar>): void;<br>差异内容：ohos.permission.WRITE_CALENDAR or ohos.permission.WRITE_WHOLE_CALENDAR|类名：CalendarManager；<br>API声明：createCalendar(calendarAccount: CalendarAccount, callback: AsyncCallback\<Calendar>): void;<br>差异内容：ohos.permission.WRITE_CALENDAR|api/@ohos.calendarManager.d.ts|
|权限变更|类名：CalendarManager；<br>API声明：deleteCalendar(calendar: Calendar): Promise\<void>;<br>差异内容：ohos.permission.WRITE_CALENDAR or ohos.permission.WRITE_WHOLE_CALENDAR|类名：CalendarManager；<br>API声明：deleteCalendar(calendar: Calendar): Promise\<void>;<br>差异内容：ohos.permission.WRITE_CALENDAR|api/@ohos.calendarManager.d.ts|
|权限变更|类名：CalendarManager；<br>API声明：deleteCalendar(calendar: Calendar, callback: AsyncCallback\<void>): void;<br>差异内容：ohos.permission.WRITE_CALENDAR or ohos.permission.WRITE_WHOLE_CALENDAR|类名：CalendarManager；<br>API声明：deleteCalendar(calendar: Calendar, callback: AsyncCallback\<void>): void;<br>差异内容：ohos.permission.WRITE_CALENDAR|api/@ohos.calendarManager.d.ts|
|权限变更|类名：CalendarManager；<br>API声明：getCalendar(calendarAccount?: CalendarAccount): Promise\<Calendar>;<br>差异内容：ohos.permission.READ_CALENDAR or ohos.permission.READ_WHOLE_CALENDAR|类名：CalendarManager；<br>API声明：getCalendar(calendarAccount?: CalendarAccount): Promise\<Calendar>;<br>差异内容：ohos.permission.READ_CALENDAR|api/@ohos.calendarManager.d.ts|
|权限变更|类名：CalendarManager；<br>API声明：getCalendar(calendarAccount: CalendarAccount, callback: AsyncCallback\<Calendar>): void;<br>差异内容：ohos.permission.READ_CALENDAR or ohos.permission.READ_WHOLE_CALENDAR|类名：CalendarManager；<br>API声明：getCalendar(calendarAccount: CalendarAccount, callback: AsyncCallback\<Calendar>): void;<br>差异内容：ohos.permission.READ_CALENDAR|api/@ohos.calendarManager.d.ts|
|权限变更|类名：CalendarManager；<br>API声明：getCalendar(callback: AsyncCallback\<Calendar>): void;<br>差异内容：ohos.permission.READ_CALENDAR or ohos.permission.READ_WHOLE_CALENDAR|类名：CalendarManager；<br>API声明：getCalendar(callback: AsyncCallback\<Calendar>): void;<br>差异内容：ohos.permission.READ_CALENDAR|api/@ohos.calendarManager.d.ts|
|权限变更|类名：CalendarManager；<br>API声明：getAllCalendars(): Promise\<Calendar[]>;<br>差异内容：ohos.permission.READ_CALENDAR or ohos.permission.READ_WHOLE_CALENDAR|类名：CalendarManager；<br>API声明：getAllCalendars(): Promise\<Calendar[]>;<br>差异内容：ohos.permission.READ_CALENDAR|api/@ohos.calendarManager.d.ts|
|权限变更|类名：CalendarManager；<br>API声明：getAllCalendars(callback: AsyncCallback\<Calendar[]>): void;<br>差异内容：ohos.permission.READ_CALENDAR or ohos.permission.READ_WHOLE_CALENDAR|类名：CalendarManager；<br>API声明：getAllCalendars(callback: AsyncCallback\<Calendar[]>): void;<br>差异内容：ohos.permission.READ_CALENDAR|api/@ohos.calendarManager.d.ts|
|删除API|类名：Calendar；<br>API声明：queryEventInstances(start: number, end: number, ids?: number[], eventKey?: (keyof Event)[]): Promise\<Event[]>;<br>差异内容：queryEventInstances(start: number, end: number, ids?: number[], eventKey?: (keyof Event)[]): Promise\<Event[]>;|NA|api/@ohos.calendarManager.d.ts|
|删除API|类名：Event；<br>API声明：instanceStartTime?: number;<br>差异内容：instanceStartTime?: number;|NA|api/@ohos.calendarManager.d.ts|
|删除API|类名：Event；<br>API声明：instanceEndTime?: number;<br>差异内容：instanceEndTime?: number;|NA|api/@ohos.calendarManager.d.ts|
|删除API|类名：Attendee；<br>API声明：type?: AttendeeType;<br>差异内容：type?: AttendeeType;|NA|api/@ohos.calendarManager.d.ts|
|删除API|类名：Attendee；<br>API声明：status?: AttendeeStatus;<br>差异内容：status?: AttendeeStatus;|NA|api/@ohos.calendarManager.d.ts|
|删除API|类名：calendarManager；<br>API声明：export enum AttendeeType<br>差异内容：export enum AttendeeType|NA|api/@ohos.calendarManager.d.ts|
|删除API|类名：AttendeeType；<br>API声明：REQUIRED = 1<br>差异内容：REQUIRED = 1|NA|api/@ohos.calendarManager.d.ts|
|删除API|类名：AttendeeType；<br>API声明：OPTIONAL = 2<br>差异内容：OPTIONAL = 2|NA|api/@ohos.calendarManager.d.ts|
|删除API|类名：AttendeeType；<br>API声明：RESOURCE = 3<br>差异内容：RESOURCE = 3|NA|api/@ohos.calendarManager.d.ts|
|删除API|类名：calendarManager；<br>API声明：export enum AttendeeStatus<br>差异内容：export enum AttendeeStatus|NA|api/@ohos.calendarManager.d.ts|
|删除API|类名：AttendeeStatus；<br>API声明：UNKNOWN = 0<br>差异内容：UNKNOWN = 0|NA|api/@ohos.calendarManager.d.ts|
|删除API|类名：AttendeeStatus；<br>API声明：TENTATIVE = 1<br>差异内容：TENTATIVE = 1|NA|api/@ohos.calendarManager.d.ts|
|删除API|类名：AttendeeStatus；<br>API声明：ACCEPTED = 2<br>差异内容：ACCEPTED = 2|NA|api/@ohos.calendarManager.d.ts|
|删除API|类名：AttendeeStatus；<br>API声明：DECLINED = 3<br>差异内容：DECLINED = 3|NA|api/@ohos.calendarManager.d.ts|
|删除API|类名：AttendeeStatus；<br>API声明：UNRESPONSIVE = 4<br>差异内容：UNRESPONSIVE = 4|NA|api/@ohos.calendarManager.d.ts|
