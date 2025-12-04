| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|权限变更|类名：CalendarManager；<br>API声明：createCalendar(calendarAccount: CalendarAccount): Promise\<Calendar>;<br>差异内容：ohos.permission.WRITE_CALENDAR|类名：CalendarManager；<br>API声明：createCalendar(calendarAccount: CalendarAccount): Promise\<Calendar>;<br>差异内容：ohos.permission.WRITE_CALENDAR or ohos.permission.WRITE_WHOLE_CALENDAR|api/@ohos.calendarManager.d.ts|
|权限变更|类名：CalendarManager；<br>API声明：createCalendar(calendarAccount: CalendarAccount, callback: AsyncCallback\<Calendar>): void;<br>差异内容：ohos.permission.WRITE_CALENDAR|类名：CalendarManager；<br>API声明：createCalendar(calendarAccount: CalendarAccount, callback: AsyncCallback\<Calendar>): void;<br>差异内容：ohos.permission.WRITE_CALENDAR or ohos.permission.WRITE_WHOLE_CALENDAR|api/@ohos.calendarManager.d.ts|
|权限变更|类名：CalendarManager；<br>API声明：deleteCalendar(calendar: Calendar): Promise\<void>;<br>差异内容：ohos.permission.WRITE_CALENDAR|类名：CalendarManager；<br>API声明：deleteCalendar(calendar: Calendar): Promise\<void>;<br>差异内容：ohos.permission.WRITE_CALENDAR or ohos.permission.WRITE_WHOLE_CALENDAR|api/@ohos.calendarManager.d.ts|
|权限变更|类名：CalendarManager；<br>API声明：deleteCalendar(calendar: Calendar, callback: AsyncCallback\<void>): void;<br>差异内容：ohos.permission.WRITE_CALENDAR|类名：CalendarManager；<br>API声明：deleteCalendar(calendar: Calendar, callback: AsyncCallback\<void>): void;<br>差异内容：ohos.permission.WRITE_CALENDAR or ohos.permission.WRITE_WHOLE_CALENDAR|api/@ohos.calendarManager.d.ts|
|权限变更|类名：CalendarManager；<br>API声明：getCalendar(calendarAccount?: CalendarAccount): Promise\<Calendar>;<br>差异内容：ohos.permission.READ_CALENDAR|类名：CalendarManager；<br>API声明：getCalendar(calendarAccount?: CalendarAccount): Promise\<Calendar>;<br>差异内容：ohos.permission.READ_CALENDAR or ohos.permission.READ_WHOLE_CALENDAR|api/@ohos.calendarManager.d.ts|
|权限变更|类名：CalendarManager；<br>API声明：getCalendar(calendarAccount: CalendarAccount, callback: AsyncCallback\<Calendar>): void;<br>差异内容：ohos.permission.READ_CALENDAR|类名：CalendarManager；<br>API声明：getCalendar(calendarAccount: CalendarAccount, callback: AsyncCallback\<Calendar>): void;<br>差异内容：ohos.permission.READ_CALENDAR or ohos.permission.READ_WHOLE_CALENDAR|api/@ohos.calendarManager.d.ts|
|权限变更|类名：CalendarManager；<br>API声明：getCalendar(callback: AsyncCallback\<Calendar>): void;<br>差异内容：ohos.permission.READ_CALENDAR|类名：CalendarManager；<br>API声明：getCalendar(callback: AsyncCallback\<Calendar>): void;<br>差异内容：ohos.permission.READ_CALENDAR or ohos.permission.READ_WHOLE_CALENDAR|api/@ohos.calendarManager.d.ts|
|权限变更|类名：CalendarManager；<br>API声明：getAllCalendars(): Promise\<Calendar[]>;<br>差异内容：ohos.permission.READ_CALENDAR|类名：CalendarManager；<br>API声明：getAllCalendars(): Promise\<Calendar[]>;<br>差异内容：ohos.permission.READ_CALENDAR or ohos.permission.READ_WHOLE_CALENDAR|api/@ohos.calendarManager.d.ts|
|权限变更|类名：CalendarManager；<br>API声明：getAllCalendars(callback: AsyncCallback\<Calendar[]>): void;<br>差异内容：ohos.permission.READ_CALENDAR|类名：CalendarManager；<br>API声明：getAllCalendars(callback: AsyncCallback\<Calendar[]>): void;<br>差异内容：ohos.permission.READ_CALENDAR or ohos.permission.READ_WHOLE_CALENDAR|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：Calendar；<br>API声明：queryEventInstances(start: number, end: number, ids?: number[], eventKey?: (keyof Event)[]): Promise\<Event[]>;<br>差异内容：queryEventInstances(start: number, end: number, ids?: number[], eventKey?: (keyof Event)[]): Promise\<Event[]>;|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：Event；<br>API声明：instanceStartTime?: number;<br>差异内容：instanceStartTime?: number;|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：Event；<br>API声明：instanceEndTime?: number;<br>差异内容：instanceEndTime?: number;|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：Attendee；<br>API声明：type?: AttendeeType;<br>差异内容：type?: AttendeeType;|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：Attendee；<br>API声明：status?: AttendeeStatus;<br>差异内容：status?: AttendeeStatus;|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：calendarManager；<br>API声明：export enum AttendeeType<br>差异内容：export enum AttendeeType|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：AttendeeType；<br>API声明：REQUIRED = 1<br>差异内容：REQUIRED = 1|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：AttendeeType；<br>API声明：OPTIONAL = 2<br>差异内容：OPTIONAL = 2|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：AttendeeType；<br>API声明：RESOURCE = 3<br>差异内容：RESOURCE = 3|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：calendarManager；<br>API声明：export enum AttendeeStatus<br>差异内容：export enum AttendeeStatus|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：AttendeeStatus；<br>API声明：UNKNOWN = 0<br>差异内容：UNKNOWN = 0|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：AttendeeStatus；<br>API声明：TENTATIVE = 1<br>差异内容：TENTATIVE = 1|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：AttendeeStatus；<br>API声明：ACCEPTED = 2<br>差异内容：ACCEPTED = 2|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：AttendeeStatus；<br>API声明：DECLINED = 3<br>差异内容：DECLINED = 3|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：AttendeeStatus；<br>API声明：UNRESPONSIVE = 4<br>差异内容：UNRESPONSIVE = 4|api/@ohos.calendarManager.d.ts|
