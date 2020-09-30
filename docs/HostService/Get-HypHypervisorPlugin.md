
# Get-Hyphypervisorplugin
Gets the available hypervisor types.
## Syntax
```
Get-HypHypervisorPlugin [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Use this command to retrieve a list of all the available hypervisor types, and their localized names.


## Related Commands

* [New-Item](../New-Item/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller to which the PowerShell snap-in connects.  You can provide this as a host name or an IP address. | false | false | LocalHost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Citrix.Host.Sdk.Hypervisorplugin<br>   Get-Hyphypervisorplugin Returns A List Of Objects Containing The Definition Of The Hypervisor Plug-Ins.<br>    Connectiontype &lt;Citrix.Xdinterservicetypes.Connectiontype&gt;<br>        The Hypervisor Connection Type.  This Can Be One Of The Following:<br>            Xenserver - Xenserver Hypervisor<br>            Scvmm - Microsoft Scvmm/Hyper-V<br>            Vcenter - Vmware Vsphere/Esx<br>            Custom - A Third-Party Hypervisor<br>    Displayname &lt;String&gt;<br>        The Localized Display Name (Localized Using The Locale Of The Powershell Snap-In Session)<br>    Pluginfactoryname &lt;String&gt;<br>        The Name Of The Hypervisor Plug-In Factory Used To Manage The Hypervisor Connections.

## Notes
To use third-party plug-ins, the plug-in assemblies must be installed into the appropriate location on each controller machine that forms part of the Citrix controller site.  Failure to do this can result in unpredictable behavior, especially during service failover conditions.<br>    In the case of failure the following errors can result.<br>    Error Codes<br>    -----------<br>    DatabaseError<br>    An error occurred in the service while attempting a database operation.<br>    CommunicationError<br>    An error occurred while communicating with the service.<br>    InvalidFilter<br>    A filtering expression was supplied that could not be interpreted for this cmdlet.<br>    ExceptionThrown<br>    An unexpected error occurred.  To locate more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.
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
