| Change Type | Old Version | New Version | d.ts File |
| ---- | ------ | ------ | -------- |
|New API |NA|Class name: Calendar;<br>API declaration: queryEventInstances(start: number, end: number, ids?: number[], eventKey?: (keyof Event)[]): Promise\<Event[]>;<br>DIfferences: queryEventInstances(start: number, end: number, ids?: number[], eventKey?: (keyof Event)[]): Promise\<Event[]>;|api/@ohos.calendarManager.d.ts|
|New API |NA|Class name: Event;<br>API declaration: instanceStartTime?: number;<br>DIfferences: instanceStartTime?: number;|api/@ohos.calendarManager.d.ts|
|New API |NA|Class name: Event;<br>API declaration: instanceEndTime?: number;<br>DIfferences: instanceEndTime?: number;|api/@ohos.calendarManager.d.ts|
|New API |NA|Class name: Attendee;<br>API declaration: type?: AttendeeType;<br>DIfferences: type?: AttendeeType;|api/@ohos.calendarManager.d.ts|
|New API |NA|Class name: Attendee;<br>API declaration: status?: AttendeeStatus;<br>DIfferences: status?: AttendeeStatus;|api/@ohos.calendarManager.d.ts|
|New API |NA|Class name: calendarManager;<br>API declaration: export enum AttendeeType<br>DIfferences: export enum AttendeeType|api/@ohos.calendarManager.d.ts|
|New API |NA|Class name: AttendeeType;<br>API declaration: REQUIRED = 1<br>DIfferences: REQUIRED = 1|api/@ohos.calendarManager.d.ts|
|New API |NA|Class name: AttendeeType;<br>API declaration: OPTIONAL = 2<br>DIfferences: OPTIONAL = 2|api/@ohos.calendarManager.d.ts|
|New API |NA|Class name: AttendeeType;<br>API declaration: RESOURCE = 3<br>DIfferences: RESOURCE = 3|api/@ohos.calendarManager.d.ts|
|New API |NA|Class name: calendarManager;<br>API declaration: export enum AttendeeStatus<br>DIfferences: export enum AttendeeStatus|api/@ohos.calendarManager.d.ts|
|New API |NA|Class name: AttendeeStatus;<br>API declaration: UNKNOWN = 0<br>DIfferences: UNKNOWN = 0|api/@ohos.calendarManager.d.ts|
|New API |NA|Class name: AttendeeStatus;<br>API declaration: TENTATIVE = 1<br>DIfferences: TENTATIVE = 1|api/@ohos.calendarManager.d.ts|
|New API |NA|Class name: AttendeeStatus;<br>API declaration: ACCEPTED = 2<br>DIfferences: ACCEPTED = 2|api/@ohos.calendarManager.d.ts|
|New API |NA|Class name: AttendeeStatus;<br>API declaration: DECLINED = 3<br>DIfferences: DECLINED = 3|api/@ohos.calendarManager.d.ts|
|New API |NA|Class name: AttendeeStatus;<br>API declaration: UNRESPONSIVE = 4<br>DIfferences: UNRESPONSIVE = 4|api/@ohos.calendarManager.d.ts|
