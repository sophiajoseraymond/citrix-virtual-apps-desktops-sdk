
# Update-Trustservicekey
Update\\\\Rotate the public key of a service
## Syntax
```
Update-TrustServiceKey -ServiceName <String> -PublicKey <String> [-InstanceId <String>] [-InstanceName <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Updates primary public key for a given service and (optional) instance id, rotating keys accordingly.

Use Get-TrustServiceKey and look at the "LastUpdated" and "RotationNeeded" fields to determine when it was last rotated and if the Service Key needs to be rotated.


## Related Commands

* [Register-TrustServiceKey](../Register-TrustServiceKey/)
* [Get-TrustServiceKey](../Get-TrustServiceKey/)
* [Unregister-TrustServiceKey](../Unregister-TrustServiceKey/)
* [Revoke-TrustPreviousServiceKey](../Revoke-TrustPreviousServiceKey/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ServiceName | The Name of the Service being updated. | true | false |  |
| PublicKey | A new Service key. | true | false |  |
| InstanceId | The instance ID of the service. | false | false | \$null |
| InstanceName | The name of the instance for this service. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### None Or Citrix.Trust.Sdk.Servicekey
This cmdlet returns a ServiceKey object.
## Examples

### Example 1
```
Update-TrustServiceKey -ServiceName ConnectorProxy -InstanceId DCCHN-Proxy.xd.local -PublicKey "newKey" -InstanceName "Instance1"
```
#### Description
Rotate the Service Key for the DCCHN-Proxy.xd.local ConnectorProxy.
