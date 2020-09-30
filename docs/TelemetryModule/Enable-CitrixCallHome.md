
# Enable-Citrixcallhome
Enables scheduled Call Home uploads and creates a Citrix identity for the machine.
## Syntax
```
Enable-CitrixCallHome [-Credential] <PSCredential> [-Collect] <String> [-MasterImage <SwitchParameter>] [<CommonParameters>]
```
## Detailed Description
This cmdlet enables recurring Call Home uploads to Citrix Insight Services. These uploads are analyzed by Citrix to identify known problems and provide other helpful information. Valid Citrix credentials are required to enable the recurring Call Home uploads. These credentials are not persisted.

The optional Collect parameter accepts a json-formatted string, which specify the parameters passed to collectors. This configuration will be used for scheduled uploads. Current collectors consist of 'sfb', 'wmi', 'process', 'registry', 'crashreport', 'trace', 'localdata' and 'sitedata'. Each of the collectors accepts at least a parameter 'enabled', used to disable the collector. By default, all collectors are enabled except for the 'sfb' collector, because 'sfb' collector is used for users to diagnose the skype failure and designed to be on-demand. The collector 'sfb' supports three parameters 'account', 'accounts' and 'enabled', first two of which specify the target user(s) 'sfb' collector will collect skype logs for, and can not coexist. If 'sfb' parameter is not null in -Collect json string, the 'sfb' collector will be enabled unless the 'enabled' is false.


## Related Commands

* [Get-Credential](../Get-Credential/)
* [Disable-CitrixCallHome](../Disable-CitrixCallHome/)
* [Get-CitrixCallHome](../Get-CitrixCallHome/)
* [Set-CitrixCallHomeSchedule](../Set-CitrixCallHomeSchedule/)
* [Get-CitrixCallHomeSchedule](../Get-CitrixCallHomeSchedule/)
* [Start-TelemetryUpload](../Start-TelemetryUpload/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Credential | Represents the Citrix user account of an authorized administrator.  The machine identity within Citrix Insight Services is derived from this user. | true | false |  |
| MasterImage | A switch to indicate that this machine is a master image that will be replicated by a provisioning system. | false | false | Not a master image |
| Collect | Specify the parameters passed to collectors. Json-formatted. | false | false |  |

## Input Type

### 

## Return Values

### 

## Examples

### Example 1: Enable Citrix Call Home
```
C:\PS>$cisCredential = Get-Credential

C:\PS>Enable-CitrixCallHome –Credential $cisCredential
```Enables Citrix Call Home with the default settings (weekly upload at 3AM Sunday)
### Example 2: Enable Citrix Call Home For A Master Image
```
C:\PS>$cisCredential = Get-Credential

C:\PS>Enable-CitrixCallHome –Credential $cisCredential -MasterImage
```Enable Citrix Call Home for a Master Image used in provisioning (weekly upload at 3AM Sunday)
### Example 3: Configure Citrix Call Home Collect For Scheduled Uploads
```
C:\PS>Enable-CitrixCallHome –Collect  '{"trace": {"enabled": false},"registry": {"enabled": false}}'
```Sets default collect configuration for scheduled call home uploads. If enabled is false, no data is collected for configured collector.
