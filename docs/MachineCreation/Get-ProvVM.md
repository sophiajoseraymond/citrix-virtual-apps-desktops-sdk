
# Get-Provvm
Gets the VMs that were created using Citrix XenDesktop Machine Creation Services.
## Syntax
```
Get-ProvVM [[-ProvisioningSchemeName] <String>] [-ProvisioningSchemeUid <Guid>] [-VMName <String>] [-Locked <Boolean>] [-Tag <String>] [-OutOfDate] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Provides the ability to obtain a list of the VMs that were created using Machine Creation Services.


## Related Commands

* [New-ProvVM](../New-ProvVM/)
* [Remove-ProvVM](../Remove-ProvVM/)
* [Lock-ProvVM](../Lock-ProvVM/)
* [Unlock-ProvVM](../Unlock-ProvVM/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ProvisioningSchemeName | The name of the provisioning scheme. | false | false |  |
| ProvisioningSchemeUid | The unique identifier of the provisioning scheme. | false | false |  |
| VMName | The name of the VM in the hypervisor context. | false | false |  |
| Locked | Indicates whether only VMs that are marked as locked are returned or not (see Lock-ProvVM and Unlock-ProvVM for details). | false | false |  |
| Tag | The tag string that was associated with the VM when it was locked. | false | false |  |
| OutOfDate | Indicates that the image currently assigned to the VM is out of date.  The image will be updated the next time the VM is restarted. | false | false |  |
| ReturnTotalRecordCount | See about\_Prov\_Filtering for details. | false | false | false |
| MaxRecordCount | See about\_Prov\_Filtering for details. | false | false | false |
| Skip | See about\_Prov\_Filtering for details. | false | false | 0 |
| SortBy | See about\_Prov\_Filtering for details. | false | false |  |
| Filter | See about\_Prov\_Filtering for details. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snap-in connects to.  You can provide this as a host name or an IP address. | false | false | LocalHost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Citrix.Machinecreation.Sdk.Provisionedvirtualmachine<br>   The Object Has The Following Properties:<br>   Adaccountsid &lt;String&gt;<br>       The Sid Of The Ad Computer Account That The Vm Is Using.<br>   Adaccountname &lt;String&gt;<br>       The Name Of The Ad Computer Account That The Vm Is Using.<br>   Cpucount &lt;Int&gt;<br>       The Number Of Processors That The Vm Has Been Allocated.<br>   Creationdate &lt;Datetime&gt;<br>       The Date And Time That The Vm Was Created.<br>   Domain &lt;String&gt;<br>       The Domain Of The Ad Computer Account That The Vm Is Using.<br>   Imageoutofdate &lt;Boolean&gt;<br>       Indicates If The Image Will Be Updated Next Time The Vm Is Started.<br>   Lock &lt;Boolean&gt;<br>       Indicates Whether The Vm Is Locked Or Not.<br>   Memorymb &lt;Int&gt;<br>       The Maximum Amount Of Memory That Vms Will Be Created With When Using This Scheme.<br>   Provisioningschemename &lt;String&gt;<br>       The Name Of The Provisioning Scheme That The Vm Is Part Of.<br>   Provisioningschemeuid &lt;Guid&gt;<br>       The Unique Identifier For The Provisioning Scheme That The Vm Is Part Of.<br>   Tag &lt;String&gt;<br>       Provides The String Associated With A Locked Vm.<br>   Vmid &lt;String&gt;<br>       The Identifier For The Vm (Hypervisor Context).<br>   Vmname &lt;String&gt;<br>       The Name Of The Vm (Hypervisor Context).<br>   Assignedimage &lt;String&gt;<br>       The Identifier (In The Hypervisor) For The Hard Disk Image That The Vm Is Currently Assigned.<br>   Bootedimage &lt;String&gt;<br>       The Identifier (In The Hypervisor) For The Hard Disk Image With Which The Vm Is Currently Started.<br>   Hostingunituid &lt;Guid&gt;<br>       The Unique Identifier For The Hosting Unit That Was Used To Create The Vm.<br>   Hypervisorconnectionuid &lt;Guid&gt;<br>       The Unique Identifier Of The Hypervisor Connection That Was Used To Create The Vm.<br>   Lastboottime &lt;Datetime&gt;<br>       The Date And Time Of The Last Start Of The Vm.<br>   Osdiskindex &lt;Int&gt;<br>       The Disk Index At Which The Hard Disk Image, From Which The Vm Is Currently Started, Is Attached (Or \[Int\]::Minvalue For Vms Inherited From Versions Of Xendesktop Before 5.6)<br>   Personalvdiskindex &lt;Int&gt;<br>       The Disk Index At Which The Personal Vdisk Is Attached (Defaults To \[Int\]::Minvalue For Vms Without A Personal Vdisk)<br>   Personalvdiskstorage &lt;String&gt;<br>       The Identifier (In The Hypervisor) For The Storage On Which The Personal Virtual Disk Image From Which The Vm Is Currently Started Is Located.  This Is Set Only If The Vm Has A Personal Vdisk Attached<br>   Storageid &lt;String&gt;<br>       The Identifier (In The Hypervisor) For The Storage On Which The Hard Disk Image, From Which The Vm Is Currently Started, Is Located.

## Notes
In the case of failure, the following errors can result.<br>    Error Codes<br>    -----------<br>    PartialData<br>    Only a subset of the available data was returned.<br>    CouldNotQueryDatabase<br>    The query required to get the database was not defined.<br>    PermissionDenied<br>    The user does not have administrative rights to perform this operation.<br>    ConfigurationLoggingError<br>    The operation could not be performed because of a configuration logging error<br>    CommunicationError<br>    An error occurred while communicating with the service.<br>    DatabaseNotConfigured<br>    The operation could not be completed because the database for the service is not configured.<br>    InvalidFilter<br>    A filtering expression was supplied that could not be interpreted for this cmdlet.<br>    ExceptionThrown<br>    An unexpected error occurred.  To locate more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.
## Examples

### Example 1
```
C:\PS>Get-ProvVM -provisioningSchemeName MyScheme

ADAccountName           : MYDomain\computer2$

ADAccountSid            : S-1-5-21-3751941309-1176885247-1409628468-3179

CpuCount                : 1

CreationDate            : 17/05/2012 09:35:22

Domain                  : steve.dum.local

ImageOutOfDate          : False

Lock                    : True

MemoryMB                : 512

ProvisioningSchemeName  : XenPS

ProvisioningSchemeUid   : 5135a865-ba49-4e5f-87f2-2d65ee7a4e51

Tag                     : Brokered

VMId                    : a830de93-ddc5-b763-dc1a-35580a31401c

VMName                  : IP0051

AssignedImage           : 57fc60c3-eb9b-4d38-8646-0afceec85335

BootedImage             : 57fc60c3-eb9b-4d38-8646-0afceec85335

HostingUnitUid          : ea17840f-cf2d-4d80-94e0-3b752b32e0af

HypervisorConnectionUid : 99f9f826-31fc-4453-8ca0-9ba54306c3ac

IdentityDiskIndex       : 1

LastBootTime            : 17/05/2012 09:35:22

OSDiskIndex             : 0

PersonalVDiskIndex      : -2147483648

PersonalVDiskStorage    :

StorageId               : 33ad07a7-edd7-589b-716a-86cad4739f5e
```
#### Description
Gets all the Virtual Machines that were provisioned into the Provisioning Scheme called 'MyScheme'.
### Example 2
```
C:\PS>Get-ProvVM -Locked $true

ADAccountName           : MYDomain\computer1$

ADAccountSid            : S-1-5-21-3751941309-1176885247-1409628468-3178

CpuCount                : 1

CreationDate            : 17/05/2012 09:35:30

Domain                  : steve.dum.local

ImageOutOfDate          : False

Lock                    : True

MemoryMB                : 512

ProvisioningSchemeName  : XenPS

ProvisioningSchemeUid   : 5135a865-ba49-4e5f-87f2-2d65ee7a4e51

Tag                     : Brokered

VMId                    : a830de93-ddc5-b763-dc1a-35580a31401c

VMName                  : IP0051

AssignedImage           : 57fc60c3-eb9b-4d38-8646-0afceec85335

BootedImage             : 57fc60c3-eb9b-4d38-8646-0afceec85335

HostingUnitUid          : ea17840f-cf2d-4d80-94e0-3b752b32e0af

HypervisorConnectionUid : 99f9f826-31fc-4453-8ca0-9ba54306c3ac

IdentityDiskIndex       : 1

LastBootTime            : 17/05/2012 09:35:22

OSDiskIndex             : 0

PersonalVDiskIndex      : -2147483648

PersonalVDiskStorage    :

StorageId               : 33ad07a7-edd7-589b-716a-86cad4739f5e
```
#### Description
Gets all the Virtual Machines that were locked, regardless of which Provisioning Scheme the VM is part of.
