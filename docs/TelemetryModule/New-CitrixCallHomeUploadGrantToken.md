
# New-Citrixcallhomeuploadgranttoken
Creates a Citrix Call Home upload grant token that can then be used to create an upload token.
## Syntax

```
New-CitrixCallHomeUploadGrantToken [-Credential] <PSCredential> [-ValidUntil <String>] [<CommonParameters>]
```

## Detailed Description
This cmdlet creates a Citrix Call Home upload grant token that can then be used to create an upload token. Citrix credentials are required, these credentials are not persisted.


## Related Commands

* [Get-Credential](../Get-Credential/)
* [Start-CitrixCallHomeUpload](../Start-CitrixCallHomeUpload/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Credential | Represents the Citrix user account of an authorized administrator. The machine identity within Citrix Insight Services is derived from this user. | true | false |  |
| ValidUntil | The generated Citrix Call Home upload token will be valid until the specified time. | false | false | 0(Infinite) |

## Input Type

### System.Management.Automation.Pscredential
This cmdlet accepts a PSCredential object as input that populates the Credential parameter.
### System.String
This cmdlet accepts a String object as input that populates the ValidUtil parameter.
## Return Values

### Uploadgranttoken

## Examples

### Example 1: Obtain A Citrix Call Home Upload Grant Token That's Valid Until 2017/1/1 00:00:00

```
C:\PS>$citrixCredential = Get-Credential  
  
C:\PS>$uploadGrantToken = New-CitrixCallHomeUploadGrantToken –Credential $citrixCredential -ValidUntil "2017/1/1 00:00:00"
```
Obtains a Citrix Call Home upload grant token from Citrix Insight Services. This may then be passed to Start-CitrixCallHomeUpload to authenticate an upload.
