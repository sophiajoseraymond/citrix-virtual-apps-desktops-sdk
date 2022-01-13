
# Enable-Citrixcallhome
Enables recurring Call Home uploads to Citrix Insight Services. These uploads are analyzed by Citrix to identify known problems and provide other helpful information. Valid Citrix credentials are required to enable the recurring Call Home uploads. These credentials are not persisted.
## Syntax

```
Enable-CitrixCallHome [-Credential] <PSCredential> [-UploadGrantToken] <String> [-UploadToken] <String> [-Collect] <String> [-MasterImage <SwitchParameter>] [<CommonParameters>]
```

## Detailed Description
This cmdlet enables recurring Call Home uploads to Citrix Insight Services. These uploads are analyzed by Citrix to identify known problems and provide other helpful information. Valid Citrix credentials are required to enable the recurring Call Home uploads. These credentials are not persisted.

The optional Collect parameter accepts a json-formatted string, which specify the parameters passed to collectors. This configuration will be used for scheduled uploads. Current collectors consist of 'sfb', 'wmi', 'process', 'registry', 'crashreport', 'trace', 'file', 'msi', 'localdata' and 'sitedata'. Each of the collectors accepts at least a parameter 'enabled', used to disable the collector. By default, all collectors are enabled except for the 'sfb' collector, because 'sfb' collector is used for users to diagnose the skype failure and designed to be on-demand. The collector 'sfb' supports three parameters 'account', 'accounts' and 'enabled', first two of which specify the target user(s) 'sfb' collector will collect skype logs for, and can not coexist. If 'sfb' parameter is not null in -Collect json string, the 'sfb' collector will be enabled unless the 'enabled' is false.

Only one of the following parameters needs to be specified in order to upload to Citrix Insight Services (CIS). Credential - Citrix credentials. UploadGrantToken - Can be obtained by using New-CitrixCallHomeUploadGrantToken cmdlet. UploadToken - Can be obtained by using New-CitrixCallHomeUploadToken cmdlet.


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
| Credential | Represents the Citrix user account of an authorized administrator. The machine identity within Citrix Insight Services is derived from this user. | true | false |  |
| UploadGrantToken | The Upload Grant Token is associated with the company/organization rather than the individual creating the grant and is used to create an Upload Token. Citrix Call Home Upload Grant Token can be generated from New-CitrixCallHomeUploadGrantToken cmdlet. | true | false |  |
| UploadToken | The Upload Token is included in HTTP headers of Citrix Insight Services payload to identify the upload is authenticated/identifiable. Citrix Call Home Upload Token can be generated from New-CitrixCallHomeUploadToken cmdlet. | true | false |  |
| MasterImage | A switch to indicate that this machine is a master image that will be replicated by a provisioning system. | false | false | Not a master image |
| Collect | Specify the parameters passed to collectors. Json-formatted. | false | false |  |

## Input Type

### 

## Return Values

### 

## Examples

### Example 1: Enable Citrix Call Home

```
C:\PS>$citrixCredential = Get-Credential  
  
C:\PS>Enable-CitrixCallHome –Credential $citrixCredential
```
Enables Citrix Call Home with the default settings (weekly upload at 3AM Sunday)
### Example 2: Enable Citrix Call Home Using Uploadgranttoken

```
C:\PS>$uploadGrantToken = New-CitrixCallHomeUploadGrantToken -Credential (Get-Credential)  
  
C:\PS>Enable-CitrixCallHome -UploadGrantToken $uploadGrantToken
```
Enables Citrix Call Home with the default settings (weekly upload at 3AM Sunday)
### Example 3: Enable Citrix Call Home Using Uploadtoken

```
C:\PS>$uploadToken = New-CitrixCallHomeUploadToken -UploadGrantToken (New-CitrixCallHomeUploadGrantToken -Credential (Get-Credential))  
  
C:\PS>Enable-CitrixCallHome –UploadToken $uploadToken
```
Enables Citrix Call Home with the default settings (weekly upload at 3AM Sunday)
### Example 4: Enable Citrix Call Home For A Master Image

```
C:\PS>$citrixCredential = Get-Credential  
  
C:\PS>Enable-CitrixCallHome –Credential $citrixCredential -MasterImage
```
Enable Citrix Call Home for a Master Image used in provisioning (weekly upload at 3AM Sunday)
### Example 5: Configure Citrix Call Home Collect For Scheduled Uploads

```
C:\PS>$citrixCredential = Get-Credential  
  
C:\PS>Enable-CitrixCallHome –Credential $citrixCredential –Collect  '{"trace": {"enabled": false},"registry": {"enabled": false}}'
```
Sets default collect configuration for scheduled call home uploads. If enabled is false, no data is collected for configured collector.
