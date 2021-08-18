
# Import-Provscheme
Import a provisioning scheme into the site
## Syntax
```
Import-ProvScheme [-ProvisioningSchemeData <String>] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
This cmdlet imports a provisioning scheme into the site, the data passed to this cmdlet should be obtained via the Export-ProvScheme cmdlet generally obtained form a different site


## Related Commands

* [Export-ProvScheme](../Export-ProvScheme/)
* [Export-AcctIdentityPool](../Export-AcctIdentityPool/)
* [Import-AcctIdentityPool](../Import-AcctIdentityPool/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ProvisioningSchemeData | Json encoded string of a provisioning scheme | false | true (ByPropertyName) |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Citrix.Machinecreation.Sdk.Provisioningscheme
This object provides details of the provisioning scheme and contains the following information:<br>    ProvisioningSchemeUid &lt;Guid&gt;<br>        The unique identifier for the provisioning scheme.<br>    ProvisioningSchemeName &lt;string&gt;<br>        The name of the provisioning scheme.<br>    CpuCount &lt;int&gt;<br>        The number of processors that VMs will be created with when using this scheme.<br>    MemoryMB &lt;int&gt;<br>        The maximum amount of memory that VMs will be created with when using this scheme.<br>    MasterImageVM &lt;string&gt;<br>        The path within the hosting unit provider to the copy of the VM snapshot that the scheme uses.<br>    MasterImageVMDate &lt;DateTime&gt;<br>        The date and time that the copy was made of the VM snapshot used by the scheme.<br>    IdentityPoolUid &lt;Guid&gt;<br>        The unique identifier of the identity pool (from the ADIdentity PowerShell snap-in) that the scheme uses.<br>    IdentityPoolName &lt;string&gt;<br>        The name of the identity pool (from the ADIdentity PowerShell snap-in) that the scheme uses.<br>    HostingUnitUid &lt;Guid&gt;<br>       The unique identifier of the hosting unit (from the Hosting Unit PowerShell snap-in) that the scheme uses.<br>    HostingUnitName &lt;string&gt;<br>       The name of the hosting unit (from the Hosting Unit PowerShell snap-in) that the scheme uses.<br>    CleanOnBoot &lt;Boolean&gt;<br>       Indicates whether the VMs that are created will be reset to a clean state on each boot.<br>    TaskId &lt;Guid&gt;<br>       The identifier of any current task that is running for the provisioning scheme.<br>    Metadata &lt;Citrix.MachineCreation.Sdk.Metadata\[\]&gt;<br>       The metadata associated with this provisioning scheme.<br>    ControllerAddress &lt;string\[\]&gt;<br>       The DNS names of the controllers associated with this provisioning scheme for Quick Deploy purposes.<br>    VMMetadata &lt;char\[\]&gt;<br>        The opaque VM metadata block<br>    UsePersonalVDiskStorage &lt;bool&gt;<br>        True if the scheme will use personal vDisk storage.<br>    PersonalVDiskDriveLetter &lt;char&gt;<br>        The drive letter for the personal vDisk<br>    PersonalVDiskDriveSize &lt;int&gt;<br>        The size of the personal vDisk in GB<br>    ProfileUsagePercentage &lt;double&gt;<br>        The percentage of the personal vDisk to be used for profile data<br>    DedicatedTenancy &lt;bool&gt;<br>        Whether to use dedicated tenancy when creating machines in Cloud Hypervisors.<br>    CurrentMasterImageUid &lt;Guid&gt;<br>        The unique identifier of the current master image used by the provisioning scheme. (See Get-ProvSchemeMasterVMImageHistory.)<br>    UseWriteBackCache &lt;bool&gt;<br>        True if the scheme will use the wrote back cache feature.<br>    WriteBackCacheDiskSize &lt;int&gt;<br>          The size of the write back cache disk if specified in GB.<br>    WriteBackCacheMemorySize &lt;int&gt;<br>          The size of the write back memory cache if specified in MB.<br>    UseFullDiskCloneProvisioning &lt;bool&gt;<br>          Indicates whether the machines are provisioned using the dedicated full disk clone feature.
## Notes
In the case of failure, the following errors can result.<br>    Error Codes<br>    CouldNotQueryDatabase<br>    The query required to get the database was not defined.<br>    PermissionDenied<br>    The user does not have administrative rights to perform this operation.<br>    ConfigurationLoggingError<br>    The operation could not be performed because of a configuration logging error<br>    CommunicationError<br>    An error occurred while communicating with the service.<br>    DatabaseNotConfigured<br>    The operation could not be completed because the database for the service is not configured.
## Examples

### Example 1
```
Import-ProvScheme -ProvisioningSchemeData $provisioningSchemeData
```
#### Description
Import the json encoded data that is in \$provisioningSchemeData
