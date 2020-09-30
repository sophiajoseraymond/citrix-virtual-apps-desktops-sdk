
# Set-Configregisteredserviceinstance
Updates a service instance.
## Syntax
```
Set-ConfigRegisteredServiceInstance -ServiceInstanceUid <Guid> -Address <String> [-PassThru] [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Use this cmdlet to change the address property of an existing service instance that is registered in the Configuration Service.


## Related Commands

* [Get-ConfigRegisteredServiceInstance](../Get-ConfigRegisteredServiceInstance/)
* [Register-ConfigServiceInstance](../Register-ConfigServiceInstance/)
* [Unregister-ConfigRegisteredServiceInstance](../Unregister-ConfigRegisteredServiceInstance/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ServiceInstanceUid | The unique identifier for the service instance to be updated. | true | true (ByPropertyName) |  |
| Address | The new address for the service instance. | true | false |  |
| PassThru | Defines whether or not the command returns a result showing the new state of the updated service instance. | false | false | true |
| LoggingId | Specifies the logging id of the high-level operation this cmdlet invocation is part of. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snap-in connects to.  You can provide this as a host name or an IP address. | false | false | LocalHost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Citrix.Configuration.Sdk.Serviceinstance<br>    This Represents A Service Instance And Has The Following Parameters:<br>    Servicegroupuid &lt;Guid&gt;<br>        The Unique Identifier For The Service Group To Which The Service Instance Belongs.<br>    Servicegroupname &lt;String&gt;<br>        The Name Of The Service Group To Which The Service Instance Belongs.<br>    Serviceinstanceuid &lt;Guid&gt;<br>        The Unique Identifier For The Service Instance.<br>    Servicetype &lt;String&gt;<br>        The Type Of The Service Group.<br>    Address &lt;String&gt;<br>        The Contact Address For The Service Instance.<br>    Binding &lt;String&gt;<br>        The Binding To Use For Connections To The Service Instance.<br>    Version &lt;Int&gt;<br>        The Version Of The Service Instance.<br>    Serviceaccount &lt;String&gt;<br>        The Ad Computer Account For The Computer That Is Providing The Service Instance.<br>    Serviceaccountsid &lt;String&gt;<br>        The Ad Computer Account Sid For The Computer That Is Providing The Service Instance.<br>    Interfacetype &lt;String&gt;<br>        The Interface Type For The Service Instance.<br>    Metadata &lt;Citrix.Configuration.Sdk.Metadata\[\]&gt;<br>        The Metadata For The Service Instance.

## Notes
In the case of failure, the following errors can result.<br>    Error Codes ----------- ObjectToUpdateDoesNotExist The service instance specified could not be located. DatabaseError An error occurred in the service while attempting a database operation. DatabaseNotConfigured The operation could not be completed because the database for the service is not configured. DataStoreException An error occurred in the service while attempting a database operation - communication with the database failed for various reasons. CommunicationError An error occurred while communicating with the service. ExceptionThrown An unexpected error occurred.  For more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.
## Examples

### Example 1
```
C:\PS>Set-ConfigRegisteredServiceInstance -ServiceInstanceUid "9805f39d-99eb-44f0-8f63-9d8e3f1228e0" -Address "http://myServer.com/Citrix/sdkHostingUnitService"
```
#### Description
Update the service instance with the unique identifier of '9805f39d-99eb-44f0-8f63-9d8e3f1228e0' to use the new address.
