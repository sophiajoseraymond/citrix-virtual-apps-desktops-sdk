
# Set-Provscheme
Changes the parameter values for a provisioning scheme.
## Syntax

```
Set-ProvScheme [-ProvisioningSchemeName] <String> [-VMCpuCount <Int32>] [-VMMemoryMB <Int32>] [-CustomProperties <String>] [-ServiceOffering <String>] [-PassThru] [-MachineProfile <String>] [-LoggingId <Guid>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]  
  
Set-ProvScheme [-ProvisioningSchemeName] <String> -IdentityPoolName <String> [-VMCpuCount <Int32>] [-VMMemoryMB <Int32>] [-CustomProperties <String>] [-ServiceOffering <String>] [-PassThru] [-MachineProfile <String>] [-LoggingId <Guid>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]  
  
Set-ProvScheme [-ProvisioningSchemeName] <String> -IdentityPoolUid <Guid> [-VMCpuCount <Int32>] [-VMMemoryMB <Int32>] [-CustomProperties <String>] [-ServiceOffering <String>] [-PassThru] [-MachineProfile <String>] [-LoggingId <Guid>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]  
  
Set-ProvScheme -ProvisioningSchemeUid <Guid> [-VMCpuCount <Int32>] [-VMMemoryMB <Int32>] [-CustomProperties <String>] [-ServiceOffering <String>] [-PassThru] [-MachineProfile <String>] [-LoggingId <Guid>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]  
  
Set-ProvScheme -ProvisioningSchemeUid <Guid> -IdentityPoolName <String> [-VMCpuCount <Int32>] [-VMMemoryMB <Int32>] [-CustomProperties <String>] [-ServiceOffering <String>] [-PassThru] [-MachineProfile <String>] [-LoggingId <Guid>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]  
  
Set-ProvScheme -ProvisioningSchemeUid <Guid> -IdentityPoolUid <Guid> [-VMCpuCount <Int32>] [-VMMemoryMB <Int32>] [-CustomProperties <String>] [-ServiceOffering <String>] [-PassThru] [-MachineProfile <String>] [-LoggingId <Guid>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
Provides the ability to update the parameters of an existing provisioning scheme.

This allows the following parameters to be updated:

Number of CPUs that will be used for VMs created from the provisioning scheme. Maximum amount of memory that will be used for VMs created from the provisioning scheme.

To change the name of the provisioning scheme see Rename-ProvScheme.


## Related Commands

* [New-ProvScheme](../New-ProvScheme/)
* [Remove-ProvScheme](../Remove-ProvScheme/)
* [Get-ProvScheme](../Get-ProvScheme/)
* [Rename-ProvScheme](../Rename-ProvScheme/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ProvisioningSchemeName | The name of the provisioning scheme to be updated. | true | false |  |
| IdentityPoolName | The name of an identity pool to associate with the provisioning scheme, replacing the present one. | true | false |  |
| IdentityPoolUid | The identifier of an identity pool to associate with the provisioning scheme, replacing the present one. | true | false |  |
| ProvisioningSchemeUid | The identifier of the provisioning scheme to be updated. | true | false |  |
| VMCpuCount | The number of processors that virtual machines created from the provisioning scheme should use. | false | false |  |
| VMMemoryMB | The maximum amount of memory that virtual machines created from the provisioning scheme should use. | false | false |  |
| CustomProperties | The properties of the provisioning scheme that are specific to the target hosting infrastructure. See about\_Prov\_CustomProperties for more information | false | false |  |
| ServiceOffering | The name of the cloud service offering to use when creating machines. | false | false |  |
| PassThru | Returns the affected record. By default, this cmdlet does not generate any output. | false | false | False |
| MachineProfile | The inventory path to the source that is used as a template. This profile identifies the values for the VMs created by the catalog. This must be a path to an item in the same hosting unit that the hosting unit name or hosting unit UID refers to. Valid paths are of the format: XDHyp:\\HostingUnits\\&lt;HostingUnitName&gt;\\&lt;path&gt; | false | false |  |
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
    ProvisioningSchemeUid  
    ProvisioningSchemeName  
        The name of the provisioning scheme.  
    CpuCount  
        The numer of processors that VMs will be created with when using this scheme.  
    MemoryMB  
        The maximum amount of memory that VMs will be created with when using this scheme.  
    MasterImageVM  
        The path within the hosting unit provider to the VM or snapshot of which the scheme is currently using a copy.  
    MasterImageVMDate  
        The date and time that the copy of the VM image was made for the scheme.  
    IdentityPoolUid  
        The unique identifier of the identity pool (from the ADIdentity PowerShell snap-in) that the scheme uses.  
    IdentityPoolName  
        The name of the identity pool (from the ADIdentity PowerShell snap-in) that the scheme uses.  
    HostingUnitUid  
       The unique identifier of the hosting unit (from the Hosting Unit PowerShell snap-in) that the new provisioning scheme will use.  
    HostingUnitName  
       The name of the hosting unit (from the Hosting Unit PowerShell snap-in) that the new provisioning scheme will use.  
    CleanOnBoot  
       Indicates whether the VMs created are to be reset to a clean state on each boot.  
    TaskId  
       The identifier of any current task that is running for the provisioning scheme.
## Notes
In the case of failure, the following errors can result.  
    Error Codes  
    -----------  
    ProvisioningSchemeNotFound  
    The specified provisioning scheme could not be located.  
    DatabaseError  
    An error occurred in the service while attempting a database operation.  
    DatabaseNotConfigured  
    The operation could not be completed because the database for the service is not configured.  
    ServiceStatusInvalidDb  
    An error occurred in the service while attempting a database operation - communication with the database failed for  
    for various reasons.  
    CommunicationError  
    An error occurred while communicating with the service.  
    PermissionDenied  
    The user does not have administrative rights to perform this operation.  
    ConfigurationLoggingError  
    The operation could not be performed because of a configuration logging error  
    HostingUnitNotFound  
    The hosting unit referenced by the provisioning scheme could not be resolved  
    ExceptionThrown  
    An unexpected error occurred.  To locate more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.
## Examples

### Example 1

```
C:\PS> Set-ProvScheme -ProvisioningSchemeName MyScheme -VMCpuCount 2
```

#### Description
Updates a provisioning scheme called "MyScheme" to use two processors on the VMs that are created from the provisioning scheme.
