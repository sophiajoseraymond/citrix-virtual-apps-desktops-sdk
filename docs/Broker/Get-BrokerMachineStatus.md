
# Get-Brokermachinestatus
Gets detailed machine brokering and power management status
## Syntax

```
Get-BrokerMachineStatus [-Uid] <Int32> [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [<CommonParameters>]  
  
Get-BrokerMachineStatus [[-MachineName] <String>] [-CatalogUid <Int32>] [-DesktopGroupUid <Int32>] [-LaunchReadiness <String>] [-Sid <String>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-FilterScope <Guid>] [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```

## Detailed Description
The Get-BrokerMachineStatus cmdlet retrieves detailed internal status of machines relating to their readiness to accept new sessions or undertake power management operations. This information is for diagnostic purposes only.


### Brokermachinestatus Object
Each machine status object returned represents the detailed status of a physical or virtual machine configured in the site with respect to its readiness for brokering or power management.


  * CatalogUid (System.Int32) The UID of the catalog containing the machine.

  * CurrentSessions (System.Int32) The number of currently established sessions on the machine.

  * DesktopGroupUid (System.Int32?) The UID of the desktop group containing the machine.

  * DrainingUntilReboot (System.Boolean) Whether no new sessions can be started on the machine as it is drained of sessions pending a reboot as part of a reboot cycle.

  * DrainingUntilShutdown (System.Boolean) Whether no new sessions can be started on the machine as it is drained of sessions pending a shutdown.

  * EffectiveLoadIndex (System.Int32?) The machine's effective load index (0 - 10000, RDS only).

  * FreeSessions (System.Int32) The number of additional sessions the machine can accept before it reaches its configured session limit (always 0 or 1 for VDI machines).

  * HasPendingPowerActions (System.Boolean) Whether the machine currently has outstanding, not yet started or completed, power actions.

  * HypervisorInMaintenanceMode (System.Boolean) Whether the machine's hypervisor connection (if any) is in maintenance mode.

  * IdleTimeBeforeUsageSecs (System.Int32?) Number of seconds for which the machine should ideally be left idle before it is selected for a new session (for example, after registration).

  * ImageOutOfDate (System.Boolean) Whether the MCS master disk image currently being used by the machine is out of date.

  * InMaintenanceMode (System.Boolean) Whether the machine is currently in maintenance mode.

  * LastIdlePeriodStartTime (System.DateTime) Start time of the last idle period (see IdleTimeBeforeUsageSecs).

  * LaunchReadiness (System.String) Summary state of the machine's readiness to accept a new session.

  * LogonsInProgress (System.Int32?) The number of session logons currently in progress on the machine (RDS only).

  * MachineFaultState (System.String) Indicates any diagnostic fault state of the machine, or None otherwise.

  * MachineName (System.String) The name of the machine (domaine ame).

  * NeedsStart (System.Boolean) Whether the machine will be restarted when next convenient (a 'natural' reboot).

  * PendingSessions (System.Int32) Number of outstanding sessions brokered to the machine that have not yet been established (client has not connected to the machine).

  * PowerState (System.String) The last reported power state of the machine.

  * SessionSupport (System.String) Whether the machine is a VDI (single session) or RDS (multi-session) machine.

  * Sid (System.String) The Windows SID of the machine.

  * SinBinReleaseTime (System.DateTime?) When set, indicates that the machine can not be selected for new sessions until the indicated time due to an earlier power management problem.

  * TagUid (System.String\[\]) List of tags associated with the machine (if any).

  * TenantId (System.Guid?) Tenant ID associated with the machine (if any).

  * Uid (System.Int32) The UID of the machine.

  * Usage (System.String) The CVAD allocation type applicable to the machine.

  * UserForcedLogOffGracePeriodExpiryTime (System.DateTime?) If set, time at which Autoscale will forcibly logoff remaining sessions on machine if users have not already logged off.

  * WillShutdownAfterUse (System.Boolean) Whether the machine must be shutdown after current session ends.

  * WindowsConnectionSetting (System.String) The Windows ConnectionSetting value reported on the machine (RDS only).

  * WorkerState (System.String) Internal machine state.

  * ZoneHealthy (System.Boolean) Whether the machine's zone is currently considered healthy.

  * ZoneUid (System.Guid) The zone in which the machine resides.


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Uid | Get status details of the machine with the specified UID. | true | false |  |
| MachineName | Gets status details of machines having a name matching that specified. | false | false |  |
| CatalogUid | Gets status details of machines in the specified catalog. | false | false |  |
| DesktopGroupUid | Gets status details of machines in the specified desktop group. | false | false |  |
| LaunchReadiness | Gets status detais of machines with the specified launch readiness. | false | false |  |
| Sid | Gets status details of the machine with the specified SID. | false | false |  |
| ReturnTotalRecordCount | When specified, this causes the cmdlet to output an error record containing the number of records available. This error record is additional information and does not affect the objects written to the output pipeline. See [about\_Broker\_Filtering](../about_Broker_Filtering/) for details. | false | false | False |
| MaxRecordCount | Specifies the maximum number of records to return. | false | false | 250 |
| Skip | Skips the specified number of records before returning results. Also reduces the count returned by -ReturnTotalRecordCount. | false | false | 0 |
| SortBy | Sorts the results by the specified list of properties. The list is a set of property names separated by commas, semi-colons, or spaces. Optionally, prefix each name with a + or - to indicate ascending or descending order. Ascending order is assumed if no prefix is present. | false | false | The default sort order is by name or unique identifier. |
| Filter | Gets records that match a PowerShell style filter expression. See [about\_Broker\_Filtering](../about_Broker_Filtering/) for details. | false | false |  |
| FilterScope | Gets only results allowed by the specified scope id. | false | false |  |
| Property | Specifies the properties to be returned. This is similar to piping the output of the command through Select-Object, but the properties are filtered more efficiently at the server. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| TraceParent | Specifies the trace parent assigned for internal diagnostic tracing use | false | false |  |
| TraceState | Specifies the trace state assigned for internal diagnostic tracing use | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### None

## Return Values

### Citrix.Broker.Admin.Sdk.Getbrokermachinestatus
Get-BrokerMachineStatus returns an object for each selected machine.
