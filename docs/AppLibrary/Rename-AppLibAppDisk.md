
# Rename-Applibappdisk
Renames a AppDisk.
## Syntax
```
Rename-AppLibAppDisk [-AppDiskName] <String> [-NewAppDiskName] <String> [-PassThru] [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]

Rename-AppLibAppDisk -AppDiskUid <Guid> [-NewAppDiskName] <String> [-PassThru] [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Provides the ability to change the name of an existing AppDisk.  The unique identifier for the AppDisk never changes after it has been created so, regardless of any name changes, the AppDisk can always be identified by its unique identifier.


## Related Commands

* [New-AppLibAppDisk](../New-AppLibAppDisk/)
* [Set-AppLibAppDisk](../Set-AppLibAppDisk/)
* [Get-AppLibAppDisk](../Get-AppLibAppDisk/)
* [Test-AppLibAppDiskNameAvailable](../Test-AppLibAppDiskNameAvailable/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| AppDiskName | The current name of the AppDisk. | true | false |  |
| AppDiskUid | The identifier for the AppDisk that is to be renamed. | true | false |  |
| NewAppDiskName | The new name for the AppDisk.  This must be a name that is not being used by an existing AppDisk, and it must not contain any of the following characters \\/;:#.\*?=&lt;&gt;|\[\]()""' | true | false |  |
| PassThru | Defines whether or not the command returns a result showing the new state of the updated AppDisk. | false | false | true |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snap-in connects to.  You can provide this as a host name or an IP address. | false | false | LocalHost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Citrix.Applibrary.Sdk.Appdisk<br>          This Object Provides Details Of The Appdisk And Contains The Following Information:<br>          Appdiskuid &lt;Guid&gt;<br>          The Unique Identifier For The Appdisk.<br>          Appdiskname &lt;String&gt;<br>          The Name Of The Appdisk.<br>          Description &lt;String&gt;<br>          A Description Of The Appdisk.<br>          Hostingunituid &lt;Guid&gt;<br>          The Unique Identifier Of The Hosting Unit (From The Hosting Unit Powershell Snap-In) That The Scheme Uses.<br>          Hostingunitname &lt;String&gt;<br>          The Name Of The Hosting Unit (From The Hosting Unit Powershell Snap-In) That The Scheme Uses.<br>          Virtualdiskid &lt;Datetime&gt;<br>          The Mcs Disk Identifier For The Appdisk.<br>          Taskid &lt;Guid&gt;<br>          The Identifier Of Any Current Task That Is Running For The Appdisk.<br>          Disklocaluid  &lt;Guid&gt;<br>          The Appdna Identifier For The Disk.<br>          Disklocalversion  &lt;Guid&gt;<br>          The Appdna Version Specifier For The Disk.<br>          Scopes &lt;Scopereference\[\]&gt;<br>          The Delegated Administration Scopes In Which The Appdisk Falls<br>          Task &lt;Task&lt;<br>          The State Of Any Current Task That Is Running For The Appdisk.<br>          State &lt;Appdiskstate&gt;<br>          The Overall Lifecycle State Of The Appdisk<br>          Statestring &lt;String&gt;<br>          The Overall Lifecycle State Of The Appdisk As A String<br>          Appdnastate &lt;Appdnastate&gt;<br>          The Appdna Lifecycle State Of The Appdisk<br>          Appdnastatestring &lt;String&gt;<br>          The Appdna Lifecycle State Of The Appdisk As A String<br>          Newversioncreationinprogress &lt;Bool&gt;<br>          A Value Indicating Whether A New Version Of This Appdisk Is Currently Being Created

## Notes
In the case of failure, the following errors can result.<br>    Error Codes<br>    -----------<br>    AppDiskNotFound<br>    The specified AppDisk could not be located.<br>    AppDiskNameAlreadyExists<br>    A AppDisk with the same name as the new AppDisk name already exists.<br>    DatabaseError<br>    An error occurred in the service while attempting a database operation.<br>    DatabaseNotConfigured<br>    The operation could not be completed because the database for the service is not configured.<br>    ServiceStatusInvalidDb<br>    An error occurred in the service while attempting a database operation - communication with the database failed<br>    for various reasons.<br>    CommunicationError<br>    An error occurred while communicating with the service.<br>    PermissionDenied<br>    The user does not have administrative rights to perform this operation.<br>    ConfigurationLoggingError<br>    The operation could not be performed because of a configuration logging error<br>    ExceptionThrown<br>    An unexpected error occurred.  To locate more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.
## Examples

### Example 1
```
C:\PS>Rename-AppLibAppDisk -AppDiskName CurrentName -NewAppDiskName NewName
```
#### Description
Renames a AppDisk from "currentName" to "NewName".
### Example 2
```
C:\PS>Rename-AppLibAppDisk -AppDiskName CurrentName -NewAppDiskName NewName -PassThru

          AppDiskUid             : 7585f0de-192e-4847-a6d8-22713c3a2f42

          AppDiskName            : NewName

          Description                 : Microsoft Office 2013

          MasterStorageID             : 03743136-e43b-4a87-af74-ab71686b3c16

          MasterDiskID                : c0571690-4f57-4476-901b-fe64d6aecb79

          HostingUnitUid              : 01a4a008-8ce8-4165-ba9c-cdf15a6b0501

          HostingUnitName             : HostUnit1

          TaskId                      : 00000000-0000-0000-0000-000000000000

          DiskLocalUid                : 4F8323D9-6978-4CA0-8231-22F9185C71B6

          DiskLocalVersion            : DDA81A28-6BF4-41E1-A120-67F72C164DF6

          Scopes                      :
```
#### Description
Renames a AppDisk from "currentName" to "NewName" and displays the resulting state.
