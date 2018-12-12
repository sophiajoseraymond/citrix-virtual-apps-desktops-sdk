
# Set-Applibappdisk
Changes the parameter values for an AppDisk.
## Syntax
```
Set-AppLibAppDisk [-AppDiskName] <String> [-Description <String>] [-PassThru] [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]

Set-AppLibAppDisk -AppDiskUid <Guid> [-Description <String>] [-PassThru] [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Provides the ability to update the parameters of an existing AppDisk.

This allows the following parameters to be updated:

Description of the AppDisk.

To change the name of the AppDisk see Rename-AppLibAppDisk.


## Related Commands

* [Get-AppLibAppDisk](./Get-AppLibAppDisk/)
* [Rename-AppLibAppDisk](./Rename-AppLibAppDisk/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| AppDiskName | The name of the AppDisk to be updated. | true | false |  |
| AppDiskUid | The identifier of the AppDisk to be updated. | true | false |  |
| Description | The description to apply; may be empty. | false | false |  |
| PassThru | Returns the affected record. By default, this cmdlet does not generate any output. | false | false | False |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Citrix.Applibrary.Sdk.Appdisk<br>          This Object Provides Details Of The Appdisk And Contains The Following Information:<br>          Appdiskuid &lt;Guid&gt;<br>          The Unique Identifier For The Appdisk.<br>          Appdiskname &lt;String&gt;<br>          The Name Of The Appdisk.<br>          Description &lt;String&gt;<br>          A Description Of The Appdisk.<br>          Hostingunituid &lt;Guid&gt;<br>          The Unique Identifier Of The Hosting Unit (From The Hosting Unit Powershell Snap-In) That The Scheme Uses.<br>          Hostingunitname &lt;String&gt;<br>          The Name Of The Hosting Unit (From The Hosting Unit Powershell Snap-In) That The Scheme Uses.<br>          Virtualdiskid &lt;Datetime&gt;<br>          The Mcs Disk Identifier For The Appdisk.<br>          Taskid &lt;Guid&gt;<br>          The Identifier Of Any Current Task That Is Running For The Appdisk.<br>          Disklocaluid  &lt;Guid&gt;<br>          The Appdna Identifier For The Disk.<br>          Disklocalversion  &lt;Guid&gt;<br>          The Appdna Version Specifier For The Disk.<br>          Scopes &lt;Scopereference\[\]&gt;<br>          The Delegated Administration Scopes In Which The Appdisk Falls<br>          Task &lt;Task&lt;<br>          The State Of Any Current Task That Is Running For The Appdisk.<br>          State &lt;Appdiskstate&gt;<br>          The Overall Lifecycle State Of The Appdisk<br>          Statestring &lt;String&gt;<br>          The Overall Lifecycle State Of The Appdisk As A String<br>          Appdnastate &lt;Appdnastate&gt;<br>          The Appdna Lifecycle State Of The Appdisk<br>          Appdnastatestring &lt;String&gt;<br>          The Appdna Lifecycle State Of The Appdisk As A String<br>          Newversioncreationinprogress &lt;Bool&gt;<br>          A Value Indicating Whether A New Version Of This Appdisk Is Currently Being Created

## Notes
In the case of failure, the following errors can result.<br>    Error Codes<br>    -----------<br>    AppDiskNotFound<br>    The specified AppDisk could not be located.<br>    DatabaseError<br>    An error occurred in the service while attempting a database operation.<br>    DatabaseNotConfigured<br>    The operation could not be completed because the database for the service is not configured.<br>    ServiceStatusInvalidDb<br>    An error occurred in the service while attempting a database operation - communication with the database failed<br>    for various reasons.<br>    CommunicationError<br>    An error occurred while communicating with the service.<br>    PermissionDenied<br>    The user does not have administrative rights to perform this operation.<br>    ConfigurationLoggingError<br>    The operation could not be performed because of a configuration logging error<br>    ExceptionThrown<br>    An unexpected error occurred.  To locate more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.
## Examples

### Example 1
```
C:\PS> Set-AppLibAppDisk -AppDiskName MyDisk -Description "Experimental"
```
#### Description
Updates as AppDisk called "MyDisk" to have the description "Experimental".
