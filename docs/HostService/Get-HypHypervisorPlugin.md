
# Get-Hyphypervisorplugin
Gets the available hypervisor types.
## Syntax

```
Get-HypHypervisorPlugin [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
Use this command to retrieve a list of all the available hypervisor types, and their localized names.


## Related Commands

* [New-Item](../New-Item/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| TraceParent | Specifies the trace parent assigned for internal diagnostic tracing use | false | false |  |
| TraceState | Specifies the trace state assigned for internal diagnostic tracing use | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller to which the PowerShell snap-in connects.  You can provide this as a host name or an IP address. | false | false | LocalHost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Citrix.Host.Sdk.Hypervisorplugin
Get-HypHypervisorPlugin returns a list of objects containing the definition of the hypervisor plug-ins.  
    ConnectionType &lt;Citrix.XDInterServiceTypes.ConnectionType&gt;  
        The hypervisor connection type.  This can be one of the following:  
            XenServer - XenServer hypervisor  
            SCVMM - Microsoft SCVMM/Hyper-V  
            vCenter - VMWare vSphere/ESX  
            Custom - a third-party hypervisor  
    DisplayName &lt;string&gt;  
        The localized display name (localized using the locale of the Powershell snap-in session)  
    PluginFactoryName &lt;string&gt;  
        The name of the hypervisor plug-in factory used to manage the hypervisor connections.
## Notes
To use third-party plug-ins, the plug-in assemblies must be installed into the appropriate location on each controller machine that forms part of the Citrix controller site.  Failure to do this can result in unpredictable behavior, especially during service failover conditions.  
    In the case of failure the following errors can result.  
    Error Codes  
    -----------  
    DatabaseError  
    An error occurred in the service while attempting a database operation.  
    CommunicationError  
    An error occurred while communicating with the service.  
    InvalidFilter  
    A filtering expression was supplied that could not be interpreted for this cmdlet.  
    ExceptionThrown  
    An unexpected error occurred.  To locate more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.
## Examples

### Example 1

```
c:\PS> Get-HypHypervisorPlugin | Format-Table -AutoSize  
  
          ConnectionType DisplayName              PluginFactoryName  
  
          -------------- -----------              -----------------  
  
                   SCVMM Microsoft virtualization MicrosoftPSFactory  
  
                 VCenter VMware virtualization    VmwareFactory  
  
               XenServer Citrix Hypervisor        XenFactory
```

#### Description
Get the available hypervisor management plug-ins.
