
# Send-Citrixcallhomebundle
This cmdlet sends the previously saved Call Home upload to Citrix Insight Services(CIS).
## Syntax

```
Send-CitrixCallHomeBundle -Credential <PSCredential> -Path <String> [<CommonParameters>]  
  
Send-CitrixCallHomeBundle -UploadGrantToken <String> -Path <String> [<CommonParameters>]  
  
Send-CitrixCallHomeBundle -UploadToken <String> -Path <String> [<CommonParameters>]
```

## Detailed Description
This cmdlet sends the previously saved Call Home upload to Citrix Insight Services(CIS). Only one of the following parameters needs to be specified in order to upload to Citrix Insight Services (CIS). Credential - Citrix credentials. UploadGrantToken - Can be obtained by using New-CitrixCallHomeUploadGrantToken cmdlet. UploadToken - Can be obtained by using New-CitrixCallHomeUploadToken cmdlet.


## Related Commands

* [Enable-CitrixCallHome](../Enable-CitrixCallHome/)
* [Get-CitrixCallHome](../Get-CitrixCallHome/)
* [Set-CitrixCallHomeSchedule](../Set-CitrixCallHomeSchedule/)
* [Get-CitrixCallHomeSchedule](../Get-CitrixCallHomeSchedule/)
* [Start-CitrixCallHomeUpload](../Start-CitrixCallHomeUpload/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Credential | Represents the Citrix user account of an authorized administrator. The machine identity within Citrix Insight Services is derived from this user. | true | true |  |
| UploadGrantToken | The Upload Grant Token is associated with the company/organization rather than the individual creating the grant and is used to create an Upload Token. Citrix Call Home Upload Grant Token can be generated from New-CitrixCallHomeUploadGrantToken cmdlet. | true | true |  |
| UploadToken | The Upload Token is included in HTTP headers of Citrix Insight Services payload to identify the upload is authenticated/identifiable. Citrix Call Home Upload Token can be generated from New-CitrixCallHomeUploadToken cmdlet. | true | true |  |
| Path | Path to previously saved bundle. | true | true |  |

## Input Type

### 

## Return Values

### 

## Examples

### Example 1: Send Previously Saved Bundle

```
PS C:\>Send-CitrixCallHomeBundle -Credential (Get-Credential) -Path C:\saved-bundle.zip
```
If you saved a bundle via Start-CitrixCallHomeUpload, you can send it to CIS(Citrix Insights Service) using this command.
