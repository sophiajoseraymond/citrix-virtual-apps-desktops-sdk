
# Get-Provschememastervmimagehistory
Gets the list of master VM snapshots that have been used to provide hard disks to provisioning schemes.
## Syntax
```
Get-ProvSchemeMasterVMImageHistory [-ProvisioningSchemeName <String>] [-ProvisioningSchemeUid <Guid>] [-MasterImageVM <String>] [-VMImageHistoryUid <Guid>] [-ImageStatus <String>] [-ShowAll] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Provides the ability to discover the master VM snapshots used to provide the hard disk image for provisioning schemes.  This information includes the date and time when the image was introduced.

By default, this cmdlet returns only those snapshots that have been used previously.  This information can be used to roll back a provisioning scheme to a previous image.

The ShowAll parameter may be supplied to also show the snapshot for the image currently in use, and the snapshots for any images prepared for later use.


## Related Commands

* [Publish-ProvMasterVMImage](./Publish-ProvMasterVMImage/)
* [Remove-ProvSchemeMasterVMImageHistory](./Remove-ProvSchemeMasterVMImageHistory/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ProvisioningSchemeName | The name of the provisioning scheme. | false | false |  |
| ProvisioningSchemeUid | The unique identifier of the provisioning scheme. | false | false |  |
| MasterImageVM | The path to the snapshot item in the hosting unit PowerShell provider. | false | false |  |
| VMImageHistoryUid | The unique identifier for the Image History item. | false | false |  |
| ImageStatus | The status of the provisioning scheme image. | false | false |  |
| ShowAll | Show all images. This includes images currently in use, and images prepared for later use. | false | false | false |
| ReturnTotalRecordCount | See about\_Prov\_Filtering for details. | false | false | false |
| MaxRecordCount | See about\_Prov\_Filtering for details. | false | false | false |
| Skip | See about\_Prov\_Filtering for details. | false | false | 0 |
| SortBy | See about\_Prov\_Filtering for details. | false | false |  |
| Filter | See about\_Prov\_Filtering for details. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snap-in connects to.  You can provide this as a host name or an IP address. | false | false | LocalHost. When a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Citrix.Machinecreation.Sdk.Vmimage<br>    This Object Represents A Master Vm History. It Contains The Following Parameters:<br>    Vmimagehistoryuid &lt;Guid&gt;<br>        The Unique Identifier For The History Item.<br>    Provisioningschemeuid &lt;Guid&gt;<br>        The Unique Identifier For The Provisioning Scheme That The Vm Was Used For.<br>    Provisioningschemename &lt;String&gt;<br>        The Name Of The Provisioning Scheme That The Vm Was Used For.<br>    Masterimagevm &lt;String&gt;<br>        The Path To The Snapshot Item That Was Used As The Master Vm Image.<br>    Date &lt;Datetime&gt;<br>        The Date And Time That The Vm Or Snapshot Was Used In The Provisioning Scheme.<br>    Imagestatus &lt;String&gt;<br>        The Status Of The Provisioning Scheme Image.<br>    Masterimageid &lt;String&gt;<br>        The Unique Identifier For The Snapshot, As Assigned By The Hosting Unit.<br>    Functionallevel &lt;String&gt;<br>        The Functionallevel Of The Vda Installed On The Vm.

## Notes
In the case of failure, the following errors can result.<br>    Error Codes<br>    -----------<br>    PartialData<br>    Only a subset of the available data was returned.<br>    PermissionDenied<br>    The user does not have administrative rights to perform this operation.<br>    ConfigurationLoggingError<br>    The operation could not be performed because of a configuration logging error.<br>    CouldNotQueryDatabase<br>    The query required to get the database was not defined.<br>    CommunicationError<br>    An error occurred while communicating with the service.<br>    DatabaseNotConfigured<br>    The operation could not be completed because the database for the service is not configured.<br>    InvalidFilter<br>    A filtering expression was supplied that could not be interpreted for this cmdlet.<br>    ExceptionThrown<br>    An unexpected error occurred.  To locate more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.
## Examples

### Example 1
```
C:\PS>Get-ProvSchemeMasterVMImageHistory

VMImageHistoryUid      : 3cba3a75-89cd-4868-989b-27feb378fec5

ProvisioningSchemeUid  : 7585f0de-192e-4847-a6d8-22713c3a2f42

ProvisioningSchemeName : MyScheme

MasterImageVM          : /Base.vm/base.snapshot

Date                   : 17/05/2010 09:27:50
```
#### Description
Gets all the hard disk images that have been used across all provisioning schemes.
### Example 2
```
C:\PS>Get-ProvSchemeMasterVMImageHistory -ProvisioningSchemeName MyScheme -masterImageVM "/BaseXp.vm/update1.snapshot" | Publish-ProvMasterVMImage
```
#### Description
Roll back the provisioning scheme to use the hard disk from the update1.snapshot for the provisioning scheme called "MyScheme".
