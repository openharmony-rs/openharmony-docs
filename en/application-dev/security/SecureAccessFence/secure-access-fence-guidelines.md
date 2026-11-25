# Obtaining CLI Credentials (Ticket)

<!--Kit: Ability Kit-->
<!--Subsystem: Security-->
<!--Owner: @gcw_3MIoLA9y-->
<!--Designer: @wkr321_ent-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=ee3646b2ac8dc8dfc90ec5c9facb07df160a93db translatedAt=2026-11-20T03:34:34.131Z pushedAt=2026-11-20T06:11:26.222Z nl=1 -->

Starting from API version 26.1.0, the secure access fence service capability is provided.

The system provides a rich set of CLI command-line tools (such as `ohos-batteryManager total-energy`) for querying system capabilities such as battery information and device status. Third-party applications need to call these CLI tools to complete business logic in scenarios such as device management and O&M diagnosis. However, CLI tools involve system-level permissions, and direct execution by applications poses risks of permission escalation and security issues.

The secure access fence service controls the execution permissions of CLI tools through the [requestToolTicket()](../../reference/apis-ability-kit/js-apis-abilityToolAccessCtrl.md#abilitytoolaccessctrlrequesttoolticket) API. After the application passes in the list of CLI commands to be executed, the system automatically checks the authorization status of the corresponding permissions: if all required permissions are authorized, the authenticated ticket is directly returned; if unauthorized permissions exist, the list of permissions to be authorized is returned, and the application can guide the user to complete authorization and then obtain the ticket again.

## Basic Concepts

- **CLI command:** A command-line interface (CLI) tool, such as the system command `ohos-batteryManager total-energy`. The secure access fence service controls the execution permissions of CLI commands.
- **Ticket:** An execution authentication credential issued by the secure access fence service, used for permission verification during CLI tool execution. When an application needs to execute controlled CLI commands, it must first obtain a valid ticket.

## Implementation Principle

The workflow of the secure access fence service is as follows:

1. The application calls the [requestToolTicket()](../../reference/apis-ability-kit/js-apis-abilityToolAccessCtrl.md#abilitytoolaccessctrlrequesttoolticket) API and passes in the list of CLI commands that require execution authentication.
2. If the user has not yet authorized the permissions required by the CLI tool, the API returns the `permissionResults` list, which contains the names of the permissions requiring authorization and their statuses. The application can guide the user to complete permission authorization.
3. If the user has authorized all required permissions, the API directly returns the authenticated `ticket` string.
4. The application uses the obtained ticket to execute the CLI tool.

## How to Develop

The development process for obtaining a CLI tool execution authentication ticket is as follows:

1. Import the secure access fence service module.
2. Build the CLI command information ([CliCmdInfo](../../reference/apis-ability-kit/js-apis-abilityToolAccessCtrl.md#clicmdinfo)) and specify the CLI command to be executed and its subcommands.
3. Build the ticket options ([TicketOptions](../../reference/apis-ability-kit/js-apis-abilityToolAccessCtrl.md#ticketoptions)) and set the ticket expiration time.
4. Call the [requestToolTicket()](../../reference/apis-ability-kit/js-apis-abilityToolAccessCtrl.md#abilitytoolaccessctrlrequesttoolticket) API to obtain the ticket.
5. Process the returned result: if the ticket is not empty, use it directly to execute the CLI tool; if the ticket is empty, guide the user to authorize and then obtain it again.
6. Add error handling logic to handle abnormal scenarios such as invalid input parameters and device screen lock.

## How to Develop

Calling the [requestToolTicket()](../../reference/apis-ability-kit/js-apis-abilityToolAccessCtrl.md#abilitytoolaccessctrlrequesttoolticket) API requires the `ohos.permission.EXEC_PUBLIC_CLI_TOOL` permission. For the application method, see [Declaring Permissions](../AccessToken/declare-permissions.md).

Take obtaining the execution authentication ticket for the CLI command `ohos-batteryManager total-energy` as an example, with a ticket validity period of 10 seconds.

1. Import the secure access fence service module and the BusinessError error type.

   After importing, you can use the `requestToolTicket` API provided by the `abilityToolAccessCtrl` module to obtain the authentication ticket for CLI tool execution.

   <!-- @[import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/AssetStoreKit/AssetStoreArkTS/entry/src/main/ets/operations/request_tool_ticket.ets) -->

   ```typescript
   import { abilityToolAccessCtrl } from '@kit.AbilityKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   ```

2. Construct the CLI command information.

   `cliCmdName` is the CLI command name. It must be a CLI command name supported by the system, such as `ohos-batteryManager`, and cannot be empty or exceed 512 bytes. `subCliCmdName` is the CLI subcommand name, such as `total-energy`, and can be an empty string but cannot exceed 512 bytes. The `cliCmdInfos` array cannot exceed 300 entries. For details about the parameters, see [CliCmdInfo](../../reference/apis-ability-kit/js-apis-abilityToolAccessCtrl.md#clicmdinfo).

   ```typescript
   let cliCmdInfos: abilityToolAccessCtrl.CliCmdInfo[] = [{
     cliCmdName: 'ohos-batteryManager',
     subCliCmdName: 'total-energy'
   }];
   ```

3. Construct the ticket options.

   `ticketExpireTimeMs` is the ticket expiration time in milliseconds. The value ranges from 1 to 60000 (60 seconds), and the default value is 10000. For details about the parameters, see [TicketOptions](../../reference/apis-ability-kit/js-apis-abilityToolAccessCtrl.md#ticketoptions).

   ```typescript
   let ticketOptions: abilityToolAccessCtrl.TicketOptions = {
     ticketExpireTimeMs: 10000
   };
   ```

4. Call the [requestToolTicket()](../../reference/apis-ability-kit/js-apis-abilityToolAccessCtrl.md#abilitytoolaccessctrlrequesttoolticket) API to obtain the ticket, and handle the returned result and errors.

   ```typescript
   abilityToolAccessCtrl.requestToolTicket(cliCmdInfos, ticketOptions)
     .then((data: abilityToolAccessCtrl.TicketQueryResult) => {
       if (data.ticket) {
         // The user has authorized all required permissions, and an authenticated ticket is obtained for executing CLI tools.
         console.info('ticket: ' + data.ticket);
       } else {
         // The user has not authorized all permissions. Check the list of permissions that require authorization.
         for (let i = 0; i < data.permissionResults.length; i++) {
           let permission = data.permissionResults[i].permission;
           let status = data.permissionResults[i].permissionStatus;
           console.info(`permission: ${permission}, status: ${status}`);
         }
         // After guiding the user to complete permission authorization, call requestToolTicket again to obtain the ticket.
       }
     })
     .catch((err: BusinessError): void => {
       console.error(`requestToolTicket fail, code: ${err.code}, message: ${err.message}`);
       if (err.code === 24010000) {
         // Input parameter error. Check whether ticketExpireTimeMs is within the scope of 1 to 60000 and whether the cliCmdInfos length exceeds 300.
       } else if (err.code === 24010006) {
         // The device is in the locked screen state. Call again after unlocking the device.
       }
     });
   ```

   The API returns a [TicketQueryResult](../../reference/apis-ability-kit/js-apis-abilityToolAccessCtrl.md#ticketqueryresult) object, which includes the `ticket` and `permissionResults` fields. When the user has granted all required permissions, the `ticket` field returns the authenticated ticket string, and the application can use the ticket to execute CLI tools. When the user has not authorized all permissions, `ticket` is an empty string, and the `permissionResults` list includes the names and statuses of the permissions to be authorized. The application needs to call the API again after guiding the user to complete authorization. For details about the API, see [requestToolTicket()](../../reference/apis-ability-kit/js-apis-abilityToolAccessCtrl.md#abilitytoolaccessctrlrequesttoolticket).

   > **Note:**
   >
   > Common error codes and their handling methods are as follows.
   > - 24010000: Invalid input parameter. Check whether the value of `ticketExpireTimeMs` is within the range of 1 to 60000, whether the `cliCmdInfos` list is empty or its length exceeds 300, and whether the CLI command name is empty.
   > - 24010006: The device is in the locked state. Unlock the device and call the API again.
   > - 24010001: The system service is abnormal. You can retry later. If the problem persists, check the system logs.
   > - For the complete list of error codes, see [Secure Access Fence Service Error Codes](../../reference/apis-ability-kit/errorcode-abilityToolAccessCtrl.md).

   <!--no_check-->
