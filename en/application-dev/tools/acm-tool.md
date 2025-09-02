# Account Manager

<!--Kit: Basic Services Kit-->
<!--Subsystem: Account-->
<!--Owner: @steven-q-->
<!--Designer: @JiDong-CS1-->
<!--Tester: @zhaimengchao-->
<!--Adviser: @zengyawen-->

Account Manager (acm) is a tool that provides basic capabilities of managing local accounts, such as creating, deleting, and querying accounts.

> **NOTE**
>
> Before using this tool, you must obtain [hdc](../dfx/hdc.md) and run the **hdc shell** command.


**Commands**

| Command| Description|
| -------- | -------- |
| help | Displays the commands supported by acm.|
| create | Creates an account. This command can be used only after the root permission is obtained.|
| delete | Deletes an account. This command can be used only after the root permission is obtained.|
| dump | Dumps the account information. This command can be used only after the root permission is obtained.|
| switch | Switches accounts. This command can be used only after the root permission is obtained.|
| deactivate | Deactivates an account. This command can be used only after the root permission is obtained.|
| set | Sets constraints for an account. This command can be used only after the root permission is obtained.|


## help

**Usage**

```bash
acm help
```

**Return Result**

Displays the acm help information.


## create

**Usage**

```bash
# Display the help information.
acm create -h
# Create an account with a specified name and type.
acm create -n <accountName> -t <accountType> [-s <shortName>] [-d <disallowed-pre-install-hap-bundles>] [-p <allowed-pre-install-hap-bundles>]
```

**Return Result**

If the account is created successfully, "create the local account successfully." is displayed. Otherwise, an error message is displayed.

**Parameters of the Create Command**

| Parameter                               | Description                      |
| ----------------------------------- | -------------------------- |
| -h | This parameter is optional. It is used to display the parameters supported by the **create** command.|
| -n | This parameter is mandatory. It specifies the name of a new account. |
| -t | This parameter is mandatory. Specifies the type of the new account. Account types include admin (administrator account), normal (common account), guest (guest account), and private (private account).|
| -s | This parameter is optional. It specifies the short name of a new account.|
| -d | This parameter is optional. Specifies the list of preset applications that are forbidden for the new account.|
| -p | This parameter is optional. List of preset applications allowed for the new account.|


## delete

**Usage**

```bash
# Display the help information.
acm delete -h
# Delete an account with a specified ID.
acm delete -i <accountId>
```

**Return Result**

If the account is deleted successfully, "delete the local account successfully." is displayed. Otherwise, an error message is displayed.

**Parameters of the Delete Command**

| Parameter                               | Description                      |
| ----------------------------------- | -------------------------- |
| -h | This parameter is optional. It is used to display the parameters supported by the **delete** command.|
| -i | This parameter is mandatory. It specifies the ID of the account to be deleted.|


## dump

**Usage**

```bash
# Display the help information.
acm dump -h
# Dump the information about all accounts.
acm dump -a
# Querying information about an account with a specified account ID
acm dump -i <accountId>
```

**Return Result**

If the query is successful, the corresponding account information is displayed. Otherwise, an error message is displayed.

**Parameters of the Dump Command**

| Parameter                               | Description                      |
| ----------------------------------- | -------------------------- |
| -h | This parameter is optional. It is used to display the parameters supported by the **dump** command.|
| -a | This parameter is mandatory. Indicates that information about all accounts is queried.|
| -i | This parameter is mandatory. It is used to dump the information about an account with a specified ID.|


## switch

**Usage**

```bash
# Display the help information.
acm switch -h
# Switch to an account with a specified ID.
acm switch -i <accountId>
```

**Return Result**

If the account is switched successfully, "switch the local account successfully." is displayed. Otherwise, an error message is displayed.

**Parameters of the Switch Command**

| Parameter                               | Description                      |
| ----------------------------------- | -------------------------- |
| -h | This parameter is optional. It is used to display the parameters supported by the **switch** command.|
| -i | This parameter is mandatory. ID of the account to be switched to.|


## deactivate

**Usage**

```bash
# Display the help information.
acm deactivate -h
# Deregistering All Accounts
acm deactivate -a
# Deregistering an account with a specified ID
acm deactivate -i <accountId>
```

**Return Result**

If the account is deactivated successfully, "deactivate the local account successfully." is displayed. Otherwise, an error message is displayed.

**Parameters of the Deactivate Command**

| Parameter                               | Description                      |
| ----------------------------------- | -------------------------- |
| -h | This parameter is optional. It is used to display the parameters supported by the **deactivate** command.|
| -a | This parameter is mandatory. It is used to deactivate all accounts.|
| -i | This parameter is mandatory. It is used to deactivate an account with a specified ID.|


## set

**Usage**

```bash
# Display the help information.
acm set -h
# Set constraints for an account with a specified ID.
acm set -i <accountId> -c <constraints> [-e]
```

**Return Result**

If the constraint is set successfully, "set constraints for the local account successfully." is displayed. Otherwise, an error message is displayed.

**Parameters of the Set Command**

| Parameter                               | Description                      |
| ----------------------------------- | -------------------------- |
| -h | This parameter is optional. It is used to display the parameters supported by the **set** command.|
| -i | This parameter is mandatory. Specifies the account ID.|
| -c | This parameter is mandatory. It specifies the constraints to be set. Each constraint is separated by a comma (,). For details, see [Constraints](../reference/apis-basic-services-kit/js-apis-osAccount.md#constraints).|
| -e | This parameter is optional. If this parameter is carried, the command is used to add a constraint; otherwise, the command is used to delete a constraint.|
