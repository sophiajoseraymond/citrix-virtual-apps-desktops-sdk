
# Get-Brokertelemetrydata
Generates list of registered instances of Public cloud workloads
## Syntax
```
Get-BrokerTelemetryData [-RegistrationTime <DateTime>] [-Uid <Int64>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Returns list of Public cloud workloads and their telemetry usage metadata


### Brokertelemetrydata Object
Data objects for filtering


  * Instance (System.String) InstanceMetadata Object

  * InstanceType (System.String) Instance type of the machine provided in a AWS instance

  * Location (System.String) Location of the hosted machine

  * MachineType (System.String) Machine type of the instance in a GCP machine

  * ProjectId (System.String) Project Id of the account in GCP project

  * RegistrationTime (System.DateTime?) Actual Registration Time of the VDA

  * ResourceGroupName (System.String) Resource Group name of the resource in an Azure environment

  * ResourceId (System.String) Resource ID of the resource in Azure environment

  * SubscriptionId (System.String) Subscription record for Azure

  * Timestamp (System.DateTime?) Metadata timestamp received from the VDA

  * Uid (System.Int64) Uid of the instance metadata

  * VmId (System.String) VmId of the instance

  * VmSize (System.String) VM size of the Azure instance


## Related Commands

* [Get-BrokerTelemetryData](./Get-BrokerTelemetryData/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| RegistrationTime | VDA Registration time of the service instance | false | false |  |
| Uid | Id of the registered VDA instance | false | false |  |
| ReturnTotalRecordCount | When specified, this causes the cmdlet to output an error record containing the number of records available. This error record is additional information and does not affect the objects written to the output pipeline. See about\_Broker\_Filtering for details. | false | false | False |
| MaxRecordCount | Specifies the maximum number of records to return. | false | false | 250 |
| Skip | Skips the specified number of records before returning results. Also reduces the count returned by -ReturnTotalRecordCount. | false | false | 0 |
| SortBy | Sorts the results by the specified list of properties. The list is a set of property names separated by commas, semi-colons, or spaces. Optionally, prefix each name with a + or - to indicate ascending or descending order. Ascending order is assumed if no prefix is present. | false | false | The default sort order is by name or unique identifier. |
| Filter | Gets records that match a PowerShell style filter expression. See about\_Broker\_Filtering for details. | false | false |  |
| Property | Specifies the properties to be returned. This is similar to piping the output of the command through Select-Object, but the properties are filtered more efficiently at the server. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### None
Input cannot be piped to this cmdlet
## Return Values

### Citrix.Broker.Admin.Sdk.Telemetrydata

## Notes
None<br>    None
## Examples

### Example 1
```
Get-BrokerTelemetryData
```
#### Description
Generates list of all registered VDA for public cloud workloads
