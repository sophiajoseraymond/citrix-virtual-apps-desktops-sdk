
# Get-Provscheme
Gets the list of provisioning schemes.
## Syntax

```
Get-ProvScheme [[-ProvisioningSchemeName] <String>] [-ProvisioningSchemeUid <Guid>] [-ScopeId <Guid>] [-ScopeName <String>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-FilterScope <Guid>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
Lets you retrieve the list of defined provisioning schemes.


## Related Commands

* [New-ProvScheme](../New-ProvScheme/)
* [Remove-ProvScheme](../Remove-ProvScheme/)
* [Add-ProvSchemeMetadata](../Add-ProvSchemeMetadata/)
* [Remove-ProvSchemeMetadata](../Remove-ProvSchemeMetadata/)
* [Add-ProvSchemeControllerAddress](../Add-ProvSchemeControllerAddress/)
* [Remove-ProvSchemeControllerAddress](../Remove-ProvSchemeControllerAddress/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ProvisioningSchemeName | The name of the provisioning scheme. | false | false |  |
| ProvisioningSchemeUid | The unique identifier of the provisioning scheme. | false | false |  |
| ScopeId | Gets only results with a scope matching the specified scope identifier. | false | false |  |
| ScopeName | Gets only results with a scope matching the specified scope name. | false | false |  |
| ReturnTotalRecordCount | See [about\_Prov\_Filtering](../about_Prov_Filtering/) for details. | false | false | false |
| MaxRecordCount | See [about\_Prov\_Filtering](../about_Prov_Filtering/) for details. | false | false | false |
| Skip | See [about\_Prov\_Filtering](../about_Prov_Filtering/) for details. | false | false | 0 |
| SortBy | See [about\_Prov\_Filtering](../about_Prov_Filtering/) for details. | false | false |  |
| Filter | See [about\_Prov\_Filtering](../about_Prov_Filtering/) for details. | false | false |  |
| FilterScope | Gets only results allowed by the specified scope id. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| TraceParent | Specifies the trace parent assigned for internal diagnostic tracing use | false | false |  |
| TraceState | Specifies the trace state assigned for internal diagnostic tracing user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snap-in connects to.  You can provide this as a host name or an IP address. | false | false | LocalHost. When a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Citrix.Machinecreation.Sdk.Provisioningscheme
This object provides details of the provisioning scheme and contains the following information:  
    ProvisioningSchemeUid &lt;Guid&gt;  
        The unique identifier for the provisioning scheme.  
    ProvisioningSchemeName &lt;string&gt;  
        The name of the provisioning scheme.  
    CpuCount &lt;int&gt;  
        The number of processors that VMs will be created with when using this scheme.  
    MemoryMB &lt;int&gt;  
        The maximum amount of memory that VMs will be created with when using this scheme.  
    MasterImageVM &lt;string&gt;  
        The path within the hosting unit provider to the copy of the VM snapshot that the scheme uses.  
    MasterImageVMDate &lt;DateTime&gt;  
        The date and time that the copy was made of the VM snapshot used by the scheme.  
    IdentityPoolUid &lt;Guid&gt;  
        The unique identifier of the identity pool (from the ADIdentity PowerShell snap-in) that the scheme uses.  
    IdentityPoolName &lt;string&gt;  
        The name of the identity pool (from the ADIdentity PowerShell snap-in) that the scheme uses.  
    HostingUnitUid &lt;Guid&gt;  
       The unique identifier of the hosting unit (from the Hosting Unit PowerShell snap-in) that the scheme uses.  
    HostingUnitName &lt;string&gt;  
       The name of the hosting unit (from the Hosting Unit PowerShell snap-in) that the scheme uses.  
    CleanOnBoot &lt;Boolean&gt;  
       Indicates whether the VMs that are created will be reset to a clean state on each boot.  
    TaskId &lt;Guid&gt;  
       The identifier of any current task that is running for the provisioning scheme.  
    Metadata &lt;Citrix.MachineCreation.Sdk.Metadata\[\]&gt;  
       The metadata associated with this provisioning scheme.  
    ControllerAddress &lt;string\[\]&gt;  
       The DNS names of the controllers associated with this provisioning scheme for Quick Deploy purposes.  
    VMMetadata &lt;char\[\]&gt;  
        The opaque VM metadata block  
    UsePersonalVDiskStorage &lt;bool&gt;  
        True if the scheme will use personal vDisk storage.  
    PersonalVDiskDriveLetter &lt;char&gt;  
        The drive letter for the personal vDisk  
    PersonalVDiskDriveSize &lt;int&gt;  
        The size of the personal vDisk in GB  
    ProfileUsagePercentage &lt;double&gt;  
        The percentage of the personal vDisk to be used for profile data  
    DedicatedTenancy &lt;bool&gt;  
        Whether to use dedicated tenancy when creating machines in Cloud Hypervisors.  
    CurrentMasterImageUid &lt;Guid&gt;  
        The unique identifier of the current master image used by the provisioning scheme. (See Get-ProvSchemeMasterVMImageHistory.)  
    UseWriteBackCache &lt;bool&gt;  
        True if the scheme will use the wrote back cache feature.  
    WriteBackCacheDiskSize &lt;int&gt;  
          The size of the write back cache disk if specified in GB.  
    WriteBackCacheMemorySize &lt;int&gt;  
          The size of the write back memory cache if specified in MB.  
    UseFullDiskCloneProvisioning &lt;bool&gt;  
          Indicates whether the machines are provisioned using the dedicated full disk clone feature.  
    MachineProfile &lt;string&gt;  
          The inventory path within the hosting unit provider to the source that the scheme uses as a template.
## Notes
In the case of failure, the following errors can result.  
    Error Codes  
    -----------  
    PartialData  
    Only a subset of the available data was returned.  
    CouldNotQueryDatabase  
    The query to get the database was not defined.  
    PermissionDenied  
    The user does not have administrative rights to perform this operation.  
    ConfigurationLoggingError  
    The operation could not be performed because of a configuration logging error.  
    CommunicationError  
    An error occurred while communicating with the service.  
    DatabaseNotConfigured  
    The operation could not be completed because the database for the service is not configured.  
    InvalidFilter  
    A filtering expression was supplied that could not be interpreted for this cmdlet.  
    ExceptionThrown  
    An unexpected error occurred.  To locate more details, see the Windows event logs on the controller being used, or examine the XenDesktop logs.
## Examples

### Example 1

```
C:\PS>Get-ProvScheme  
  
ProvisioningSchemeUid        : 7585f0de-192e-4847-a6d8-22713c3a2f42  
  
ProvisioningSchemeName       : Scheme1  
  
CpuCount                     : 1  
  
MemoryMB                     : 1024  
  
MachineProfile               : XDHyp:/.../MachineProfile.vm  
  
MasterImageVM                : XDHyp:/.../Base.vm/base.snapshot  
  
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
  
MachineProfile               :  
  
MasterImageVM                : XDHyp:/.../Base.vm/base.snapshot  
  
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
  
MachineProfile               : XDHyp:/.../MachineProfile.vm  
  
MasterImageVM                : XDHyp:/.../Base.vm/base.snapshot  
  
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
