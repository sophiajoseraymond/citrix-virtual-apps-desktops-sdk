
# Get-Provscheme
Gets the list of provisioning schemes.
## Syntax
```
Get-ProvScheme [[-ProvisioningSchemeName] <String>] [-ProvisioningSchemeUid <Guid>] [-ScopeId <Guid>] [-ScopeName <String>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Lets you retrieve the list of defined provisioning schemes.


## Related Commands

* [New-ProvScheme](./New-ProvScheme/)
* [Remove-ProvScheme](./Remove-ProvScheme/)
* [Add-ProvSchemeMetadata](./Add-ProvSchemeMetadata/)
* [Remove-ProvSchemeMetadata](./Remove-ProvSchemeMetadata/)
* [Add-ProvSchemeControllerAddress](./Add-ProvSchemeControllerAddress/)
* [Remove-ProvSchemeControllerAddress](./Remove-ProvSchemeControllerAddress/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ProvisioningSchemeName | The name of the provisioning scheme. | false | false |  |
| ProvisioningSchemeUid | The unique identifier of the provisioning scheme. | false | false |  |
| ScopeId | Gets only results with a scope matching the specified scope identifier. | false | false |  |
| ScopeName | Gets only results with a scope matching the specified scope name. | false | false |  |
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

### Citrix.Machinecreation.Sdk.Provisioningscheme<br>    This Object Provides Details Of The Provisioning Scheme And Contains The Following Information:<br>    Provisioningschemeuid &lt;Guid&gt;<br>        The Unique Identifier For The Provisioning Scheme.<br>    Provisioningschemename &lt;String&gt;<br>        The Name Of The Provisioning Scheme.<br>    Cpucount &lt;Int&gt;<br>        The Number Of Processors That Vms Will Be Created With When Using This Scheme.<br>    Memorymb &lt;Int&gt;<br>        The Maximum Amount Of Memory That Vms Will Be Created With When Using This Scheme.<br>    Masterimagevm &lt;String&gt;<br>        The Path Within The Hosting Unit Provider To The Copy Of The Vm Snapshot That The Scheme Uses.<br>    Masterimagevmdate &lt;Datetime&gt;<br>        The Date And Time That The Copy Was Made Of The Vm Snapshot Used By The Scheme.<br>    Identitypooluid &lt;Guid&gt;<br>        The Unique Identifier Of The Identity Pool (From The Adidentity Powershell Snap-In) That The Scheme Uses.<br>    Identitypoolname &lt;String&gt;<br>        The Name Of The Identity Pool (From The Adidentity Powershell Snap-In) That The Scheme Uses.<br>    Hostingunituid &lt;Guid&gt;<br>       The Unique Identifier Of The Hosting Unit (From The Hosting Unit Powershell Snap-In) That The Scheme Uses.<br>    Hostingunitname &lt;String&gt;<br>       The Name Of The Hosting Unit (From The Hosting Unit Powershell Snap-In) That The Scheme Uses.<br>    Cleanonboot &lt;Boolean&gt;<br>       Indicates Whether The Vms That Are Created Will Be Reset To A Clean State On Each Boot.<br>    Taskid &lt;Guid&gt;<br>       The Identifier Of Any Current Task That Is Running For The Provisioning Scheme.<br>    Metadata &lt;Citrix.Machinecreation.Sdk.Metadata\[\]&gt;<br>       The Metadata Associated With This Provisioning Scheme.<br>    Controlleraddress &lt;String\[\]&gt;<br>       The Dns Names Of The Controllers Associated With This Provisioning Scheme For Quick Deploy Purposes.<br>    Vmmetadata &lt;Char\[\]&gt;<br>        The Opaque Vm Metadata Block<br>    Usepersonalvdiskstorage &lt;Bool&gt;<br>        True If The Scheme Will Use Personal Vdisk Storage.<br>    Personalvdiskdriveletter &lt;Char&gt;<br>        The Drive Letter For The Personal Vdisk<br>    Personalvdiskdrivesize &lt;Int&gt;<br>        The Size Of The Personal Vdisk In Gb<br>    Profileusagepercentage &lt;Double&gt;<br>        The Percentage Of The Personal Vdisk To Be Used For Profile Data<br>    Dedicatedtenancy &lt;Bool&gt;<br>        Whether To Use Dedicated Tenancy When Creating Machines In Cloud Hypervisors.<br>    Currentmasterimageuid &lt;Guid&gt;<br>        The Unique Identifier Of The Current Master Image Used By The Provisioning Scheme. (See Get-Provschememastervmimagehistory.)<br>    Usewritebackcache &lt;Bool&gt;<br>        True If The Scheme Will Use The Wrote Back Cache Feature.<br>    Writebackcachedisksize &lt;Int&gt;<br>          The Size Of The Write Back Cache Disk If Specified In Gb.<br>    Writebackcachememorysize &lt;Int&gt;<br>          The Size Of The Write Back Memory Cache If Specified In Mb.<br>    Usefulldiskcloneprovisioning &lt;Bool&gt;<br>          Indicates Whether The Machines Are Provisioned Using The Dedicated Full Disk Clone Feature.

## Notes
In the case of failure, the following errors can result.<br>    Error Codes<br>    -----------<br>    PartialData<br>    Only a subset of the available data was returned.<br>    CouldNotQueryDatabase<br>    The query to get the database was not defined.<br>    PermissionDenied<br>    The user does not have administrative rights to perform this operation.<br>    ConfigurationLoggingError<br>    The operation could not be performed because of a configuration logging error.<br>    CommunicationError<br>    An error occurred while communicating with the service.<br>    DatabaseNotConfigured<br>    The operation could not be completed because the database for the service is not configured.<br>    InvalidFilter<br>    A filtering expression was supplied that could not be interpreted for this cmdlet.<br>    ExceptionThrown<br>    An unexpected error occurred.  To locate more details, see the Windows event logs on the controller being used, or examine the XenDesktop logs.
## Examples

### Example 1
```
C:\PS>Get-ProvScheme

ProvisioningSchemeUid        : 7585f0de-192e-4847-a6d8-22713c3a2f42

ProvisioningSchemeName       : Scheme1

CpuCount                     : 1

MemoryMB                     : 1024

MasterImageVM                : /Base.vm/base.snapshot

MasterImageVMDate            : 17/05/2010 09:27:50

IdentityPoolUid              : 03743136-e43b-4a87-af74-ab71686b3c16

IdentityPoolName             : idPool1

HostingUnitUid               : 01a4a008-8ce8-4165-ba9c-cdf15a6b0501

HostingUnitName              : HostUnit1

CleanOnBoot                  : True

TaskId                       : 00000000-0000-0000-0000-000000000000

Metadata                     : {Department = Sales}

ControllerAddress            : {}

VMMetadata                   : {0, 1, 0, 0...}

PersonalVDiskDriveLetter     :

PersonalVDiskDriveSize       : 0

UsePersonalVDiskStorage      : False

NetworkMaps                  : {0}

Scopes                       :

DedicatedTenancy             : False

GpuTypeId                    :

ResetAdministratorPasswords  : False

SecurityGroups               : {}

ServiceOffering              :

CurrentMasterImageUid        : c0571690-4f57-4476-901b-fe64d6aecb79

UseWriteBackCache            : True

WriteBackCacheDiskSize       : 24

WriteBackCacheMemorySize     : 256

UseFullDiskCloneProvisioning : False

ProvisioningSchemeUid        : 43d82099-1fd7-4617-93f0-25b160813905

ProvisioningSchemeName       : Scheme2

CpuCount                     : 1

MemoryMB                     : 1024

MasterImageVM                : /Base.vm/base.snapshot

MasterImageVMDate            : 17/05/2010 09:53:40

IdentityPoolUid              : 03743136-e43b-4a87-af74-ab71686b3c16

IdentityPoolName             : idPool1

HostingUnitUid               : 01a4a008-8ce8-4165-ba9c-cdf15a6b0501

HostingUnitName              : HostUnit1

CleanOnBoot                  : True

TaskId                       : 00000000-0000-0000-0000-000000000000

Metadata                     : {}

ControllerAddress            : {}

VMMetadata                   : {0, 1, 0, 0...}

PersonalVDiskDriveLetter     :

PersonalVDiskDriveSize       : 0

UsePersonalVDiskStorage      : False

NetworkMaps                  : {0}

Scopes                       :

DedicatedTenancy             : False

GpuTypeId                    :

ResetAdministratorPasswords  : False

SecurityGroups               : {}

ServiceOffering              :

CurrentMasterImageUid        : 022cd6e4-34cb-3f7c-e02a-44ac404483b4

UseWriteBackCache            : True

WriteBackCacheDiskSize       : 24

WriteBackCacheMemorySize     : 256

UseFullDiskCloneProvisioning : False
```
#### Description
Returns all of the available provisioning schemes.
### Example 2
```
C:\PS>Get-ProvScheme -ProvisioningSchemeName Scheme[0-1]

ProvisioningSchemeUid        : 7585f0de-192e-4847-a6d8-22713c3a2f42

ProvisioningSchemeName       : Scheme1

CpuCount                     : 1

MemoryMB                     : 1024

MasterImageVM                : /Base.vm/base.snapshot

MasterImageVMDate            : 17/05/2010 09:27:50

IdentityPoolUid              : 03743136-e43b-4a87-af74-ab71686b3c16

IdentityPoolName             : idPool1

HostingUnitUid               : 01a4a008-8ce8-4165-ba9c-cdf15a6b0501

HostingUnitName              : HostUnit1

CleanOnBoot                  : True

TaskId                       : 00000000-0000-0000-0000-000000000000

Metadata                     : {}

ControllerAddress            : {}

VMMetadata                   : {0, 1, 0, 0...}

PersonalVDiskDriveLetter     :

PersonalVDiskDriveSize       : 0

UsePersonalVDiskStorage      : False

NetworkMaps                  : {0}

Scopes                       :

DedicatedTenancy             : False

GpuTypeId                    :

ResetAdministratorPasswords  : False

SecurityGroups               : {}

ServiceOffering              :

CurrentMasterImageUid        : c0571690-4f57-4476-901b-fe64d6aecb79

UseWriteBackCache            : True

WriteBackCacheDiskSize       : 24

WriteBackCacheMemorySize     : 256

UseFullDiskCloneProvisioning : False
```
#### Description
Returns all of the provisioning schemes that have the name 'Scheme0' or 'Scheme1'.
