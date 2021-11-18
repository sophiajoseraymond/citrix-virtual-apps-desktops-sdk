
# Import-Provscheme
Import a provisioning scheme into the site
## Syntax

```
Import-ProvScheme [-ProvisioningSchemeData <String>] [-Scope <String[]>] [-LoggingId <Guid>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
This cmdlet imports a provisioning scheme into the site, the data passed to this cmdlet should be obtained via the Export-ProvScheme cmdlet generally obtained from a different site


## Related Commands

* [Export-ProvScheme](../Export-ProvScheme/)
* [Export-AcctIdentityPool](../Export-AcctIdentityPool/)
* [Import-AcctIdentityPool](../Import-AcctIdentityPool/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ProvisioningSchemeData | Json encoded string of a provisioning scheme | false | true (ByPropertyName) |  |
| Scope | The administration scopes to be applied to the new identity pool. | false | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| TraceParent | Specifies the trace parent assigned for internal diagnostic tracing use | false | false |  |
| TraceState | Specifies the trace state assigned for internal diagnostic tracing user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

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
## Notes
In the case of failure, the following errors can result.  
    Error Codes  
    CouldNotQueryDatabase  
    The query required to get the database was not defined.  
    PermissionDenied  
    The user does not have administrative rights to perform this operation.  
    ConfigurationLoggingError  
    The operation could not be performed because of a configuration logging error  
    CommunicationError  
    An error occurred while communicating with the service.  
    DatabaseNotConfigured  
    The operation could not be completed because the database for the service is not configured.
## Examples

### Example 1

```
Import-ProvScheme -ProvisioningSchemeData $provisioningSchemeData
```

#### Description
Import the json encoded data that is in \$provisioningSchemeData
