
# Get-Brokerhypervisorconnectionstatus
Gets connection status and power management stats for the hypervisor.
## Syntax

```
Get-BrokerHypervisorConnectionStatus [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-FilterScope <Guid>] [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```

## Detailed Description
The GetBrokerHypervisorConnectionStatus cmdlet retrieves the power management statistics and connection status for all hypervisors on the DDC


### Brokerhypervisorconnectionstatus Object
FIXME


  * CredentialsValid (System.Boolean?) FIXME

  * HclCurrentlyConnected (System.Boolean?) FIXME

  * HypervisorConnectionGuid (System.Guid?) FIXME

  * HypervisorConnectionUid (System.Int32) FIXME

  * HypervisorType (System.String) FIXME

  * HypervisorZone (System.Guid?) FIXME

  * InMaintenanceMode (System.Boolean?) FIXME

  * InProgressActions (System.Int32?) FIXME

  * LastActionCompletedTime (System.DateTime?) FIXME

  * LastActionFailedTime (System.DateTime?) FIXME

  * LastActionStartTime (System.DateTime?) FIXME

  * LastMachineManagerCreationTime (System.DateTime?) FIXME

  * LastPowerStateUpdateEventTime (System.DateTime?) FIXME

  * LastPowerStateUpdateTime (System.DateTime?) FIXME

  * LastSiteServiceStartTime (System.DateTime?) FIXME

  * LastToolStateUpdateEventTime (System.DateTime?) FIXME

  * LastToolStateUpdateTime (System.DateTime?) FIXME

  * NextPendingAction (System.Int64?) FIXME

  * PendingActions (System.Int32?) FIXME

  * TotalMachineManagersCreated (System.Int32?) FIXME

  * TotalMachineManagersFailed (System.Int32?) FIXME

  * TotalMachines (System.Int32?) FIXME


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Property | Specifies the properties to be returned. This is similar to piping the output of the command through Select-Object, but the properties are filtered more efficiently at the server. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| TraceParent | Specifies the trace parent assigned for internal diagnostic tracing use | false | false |  |
| TraceState | Specifies the trace state assigned for internal diagnostic tracing use | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| ReturnTotalRecordCount | When specified, this causes the cmdlet to output an error record containing the number of records available. This error record is additional information and does not affect the objects written to the output pipeline. See [about\_Broker\_Filtering](../about_Broker_Filtering/) for details. | false | false | False |
| MaxRecordCount | Specifies the maximum number of records to return. | false | false | 250 |
| Skip | Skips the specified number of records before returning results. Also reduces the count returned by -ReturnTotalRecordCount. | false | false | 0 |
| SortBy | Sorts the results by the specified list of properties. The list is a set of property names separated by commas, semi-colons, or spaces. Optionally, prefix each name with a + or - to indicate ascending or descending order. Ascending order is assumed if no prefix is present. | false | false | The default sort order is by name or unique identifier. |
| Filter | Gets records that match a PowerShell style filter expression. See [about\_Broker\_Filtering](../about_Broker_Filtering/) for details. | false | false |  |
| FilterScope | Gets only results allowed by the specified scope id. | false | false |  |

## Input Type

### None

## Return Values

### Citrix.Broker.Admin.Sdk.Getbrokerhypervisorconnectionstatus
Get-BrokerHypervisorConnectionStatus returns an object for each hypervisor connection present in the DDC.
