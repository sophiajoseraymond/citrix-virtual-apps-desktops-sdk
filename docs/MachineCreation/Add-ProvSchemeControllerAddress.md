
# Add-Provschemecontrolleraddress
Adds a list of host names (as DNS addresses) to a provisioning scheme.
## Syntax

```
Add-ProvSchemeControllerAddress [-ProvisioningSchemeName] <String> [-ControllerAddress] <String[]> [-LoggingId <Guid>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]  
  
Add-ProvSchemeControllerAddress -ProvisioningSchemeUid <Guid> [-ControllerAddress] <String[]> [-LoggingId <Guid>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
Provides the ability to associate controller hosts (and hence implicitly a set of brokers) with a specific provisioning scheme.  This optional data is passed to the machines created by the Machine Creation Services, where it is used to associate the newly created machine with a broker.  The list is returned along with the provisioning scheme that it is assigned to.


## Related Commands

* [Get-ProvScheme](../Get-ProvScheme/)
* [Remove-ProvSchemeControllerAddress](../Remove-ProvSchemeControllerAddress/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ProvisioningSchemeName | The name for the provisioning scheme that the list of addresses is to be added to. | true | true (ByPropertyName) |  |
| ProvisioningSchemeUid | The unique identifier for the provisioning scheme that the list of addresses is to be added to. | true | false |  |
| ControllerAddress | Specifies the array of DNS names to be added to the provisioning scheme. | true | true (ByPropertyName) |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| TraceParent | Specifies the trace parent assigned for internal diagnostic tracing use | false | false |  |
| TraceState | Specifies the trace state assigned for internal diagnostic tracing user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snap-in connects to.  You can provide this as a host name or an IP address. | false | false | LocalHost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### Citrix.Machinecreation.Sdk.Provisioningscheme  
    You Can Pipe An Object Containing A Parameter Called 'Provisioningschemename' To Add-Provschemecontrolleraddress.

## Return Values

### Citrix.Machinecreation.Sdk.Provisioningscheme
Add-ProvSchemeControllerAddress returns the updated ProvisioningScheme object containing the union of the old and new controller address lists.  
    ProvisioningSchemeUid &lt;Guid&gt;  
        The unique identifier for the provisioning scheme.  
    ProvisioningSchemeName &lt;string&gt;  
        The name of the provisioning scheme.  
    CpuCount &lt;int&gt;  
        The number of processors that VMs will be created with when using this scheme.  
    MemoryMB &lt;int&gt;  
        The maximum amount of memory that VMs will be created with when using this scheme.  
    MasterImageVM &lt;string&gt;  
        The path within the hosting unit provider to the VM or snapshot of which the scheme is currently using a copy.  
    MasterImageVMDate &lt;DateTime&gt;  
        The date and time that the copy of the VM image was made for the scheme.  
    IdentityPoolUid &lt;Guid&gt;  
        The unique identifier of the identity pool (from the ADIdentity PowerShell snap-in) that the scheme uses.  
    IdentityPoolName &lt;string&gt;  
        The name of the identity pool (from the ADIdentity PowerShell snap-in) that the scheme uses.  
    HostingUnitUid &lt;Guid&gt;  
       The unique identifier of the hosting unit (from the Hosting Unit PowerShell snap-in) that the scheme will use.  
    HostingUnitName &lt;string&gt;  
       The name of the hosting unit (from the Hosting Unit PowerShell snap-in) that the scheme will use.  
    CleanOnBoot &lt;Boolean&gt;  
       Indicates whether or not the VMs created are to be reset to a clean state on each boot.  
    TaskId &lt;Guid&gt;  
       The identifier of any current task that is running for the provisioning scheme.  
    Metadata &lt;Citrix.MachineCreation.Sdk.Metadata\[\]&gt;  
       The metadata associated with this provisioning scheme.  
    ControllerAddress &lt;string\[\]&gt;  
       The DNS names of the controllers associated with this provisioning scheme for Quick Deploy purposes.
## Notes
In the case of failure, the following errors can result.  
    Error Codes  
    -----------  
    ProvisioningSchemeNotFound  
    The specified provisioning scheme could not be located.  
    PermissionDenied  
    The user does not have administrative rights to perform this operation.  
    ConfigurationLoggingError  
    The operation could not be performed because of a configuration logging error  
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
    ExceptionThrown  
    An unexpected error occurred.  To locate more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.
## Examples

### Example 1

```
C:\PS>Add-ProvSchemeControllerAddress -ProvisioningSchemeUid "01a4a008-8ce8-4165-ba9c-cdf15a6b0501" -ControllerAddress (ddcA.citrix.com,ddcB.citrix.com,ddcC.citrix2.com)  
  
ProvisioningSchemeUid  : 01a4a008-8ce8-4165-ba9c-cdf15a6b0501  
  
ProvisioningSchemeName : Scheme2  
  
CpuCount               : 1  
  
MemoryMB               : 1024  
  
MasterImageVM          : Base.vm/Base.snapshot  
  
MasterImageVMDate      : 17/05/2010 09:53:40  
  
IdentityPoolUid        : 03743136-e43b-4a87-af74-ab71686b3c16  
  
IdentityPoolName       : idPool1  
  
HostingUnitUid         : 01a4a008-8ce8-4165-ba9c-cdf15a6b0501  
  
HostingUnitName        : HostUnit1  
  
CleanOnBoot            : True  
  
TaskId                 : 00000000-0000-0000-0000-000000000000  
  
Metadata               : {}  
  
ControllerAddress      : {ddcA.citrix.com,ddcB.citrix.com,ddcC.citrix2.com}
```

#### Description
Add a set of controllers to the provisioning scheme with the identifier "01a4a008-8ce8-4165-ba9c-cdf15a6b0501".
### Example 2

```
C:\PS>Get-ProvScheme -ProvisioningSchemeName scheme1 | Add-ProvSchemeControllerAddress -ControllerAddress (ddcA.citrix.com,ddcB.citrix.com,ddcC.citrix2.com)  
  
ProvisioningSchemeUid  : 7585f0de-192e-4847-a6d8-22713c3a2f42  
  
ProvisioningSchemeName : Scheme1  
  
CpuCount               : 1  
  
MemoryMB               : 1024  
  
MasterImageVM          : Base.vm/Base.snapshot  
  
MasterImageVMDate      : 17/05/2010 09:53:40  
  
IdentityPoolUid        : 03743136-e43b-4a87-af74-ab71686b3c16  
  
IdentityPoolName       : idPool1  
  
HostingUnitUid         : 01a4a008-8ce8-4165-ba9c-cdf15a6b0501  
  
HostingUnitName        : HostUnit1  
  
CleanOnBoot            : True  
  
TaskId                 : 00000000-0000-0000-0000-000000000000  
  
Metadata               : {}  
  
ControllerAddress      : {ddcA.citrix.com,ddcB.citrix.com,ddcC.citrix2.com}
```

#### Description
Add controller addresses  to a provisioning scheme using a ProvisioningScheme object.
