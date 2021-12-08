
# Remove-Provschemecontrolleraddress
Removes metadata from a provisioning scheme.
## Syntax

```
Remove-ProvSchemeControllerAddress [-ProvisioningSchemeName] <String> [-ControllerAddress] <String[]> [-LoggingId <Guid>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]  
  
Remove-ProvSchemeControllerAddress -ProvisioningSchemeUid <Guid> -ControllerAddress <String[]> [-LoggingId <Guid>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
Removes the specified controller addresses from the specified object. Attempting to remove an address not present writes an error record to the pipeline.


## Related Commands

* [Get-ProvScheme](../Get-ProvScheme/)
* [Add-ProvSchemeControllerAddress](../Add-ProvSchemeControllerAddress/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ProvisioningSchemeName | The name of the provisioning scheme from which metadata is to be removed. | true | true (ByPropertyName) |  |
| ProvisioningSchemeUid | The identifier of the provisioning scheme from which metadata is to be removed. | true | false |  |
| ControllerAddress | Specifies the array of DNS names to be removed from the provisioning scheme. | true | true (ByPropertyName) |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| TraceParent | Specifies the trace parent assigned for internal diagnostic tracing use | false | false |  |
| TraceState | Specifies the trace state assigned for internal diagnostic tracing user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snap-in connects to.  You can provide this as a host name or an IP address. | false | false | LocalHost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### Citrix.Machinecreation.Sdk.Provisioningscheme  
    You Can Pipe An Object Containing A Parameter Called 'Provisioningschemename' To Remove-Provschememetadata.

## Return Values

### 

## Notes
In the case of failure, the following errors can result.  
    Error Codes  
    -----------  
    ProvisioningSchemeNotFound  
    The specified provisioning scheme could not be located.  
    ControllerAddressNotFound  
    The specified address was not associated with the provisioning scheme.  
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
    ExceptionThrown  
    An unexpected error occurred.  To locate more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.
## Examples

### Example 1

```
C:\PS>Get-ProvScheme -ProvisioningSchemeName scheme1 | Remove-ProvSchemeControllerAddress  
  
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
  
ControllerAddress      : {}
```

#### Description
Remove all controller addresses from the provisioning scheme with the name "scheme1".
### Example 2

```
C:\PS>Remove-ProvSchemeControllerAddress -ProvisioningSchemeUid "01a4a008-8ce8-4165-ba9c-cdf15a6b0501" -ControllerAddress (ddcA.citrix.com,ddcC.citrix2.com)  
  
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
  
ControllerAddress      : {ddcB.citrix.com}
```

#### Description
Remove a subset of the controller address list from the provisioning scheme with the identifier "01a4a008-8ce8-4165-ba9c-cdf15a6b0501".
