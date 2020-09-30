
# Get-Configregisteredserviceinstance
Gets the service instances that are registered in the directory.
## Syntax
```
Get-ConfigRegisteredServiceInstance [-ServiceInstanceUid <Guid>] [-ServiceGroupUid <Guid>] [-ServiceGroupName <String>] [-ServiceType <String>] [-Address <String>] [-Binding <String>] [-Version <Int32>] [-ServiceAccountSid <String>] [-InterfaceType <String>] [-Metadata <String>] [-Property <String[]>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Use this cmdlet to retrieve the service instances currently registered with the Configuration Service that match the parameters supplied.  If no parameters are supplied, all the service instances are returned.


## Related Commands

* [Register-ConfigServiceInstance](../Register-ConfigServiceInstance/)
* [Unregister-ConfigRegisteredServiceInstance](../Unregister-ConfigRegisteredServiceInstance/)
* [Set-ConfigRegisteredServiceInstance](../Set-ConfigRegisteredServiceInstance/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ServiceInstanceUid | The unique identifier for the service instance. | false | false |  |
| ServiceGroupUid | The unique identifier for the service group to which the service instance belongs. | false | false |  |
| ServiceGroupName | The name for the service group to which the service instance belongs. | false | false |  |
| ServiceType | The service type for the service instance. | false | false |  |
| Address | The connection address for the service instance. | false | false |  |
| Binding | The binding for the service instance. | false | false |  |
| Version | The service instance version. | false | false |  |
| ServiceAccountSid | The AD account SID for the computer account that the computer hosting the service instance is running as. | false | false |  |
| InterfaceType | The interface type for the service instance. | false | false |  |
| Metadata | Gets records with matching metadata entries.<br>The value being compared with is a concatenation of the key name, a colon, and the value. For example: -Metadata "abc:x\*" matches records with a metadata entry having a key name of "abc" and a value starting with the letter "x". | false | false |  |
| Property | Specifies the properties to be returned. This is similar to piping the output of the command through Select-Object, but the properties are filtered more efficiently at the server. | false | false |  |
| ReturnTotalRecordCount | See about\_Config\_Filtering for details. | false | false | false |
| MaxRecordCount | See about\_Config\_Filtering for details. | false | false | 250 |
| Skip | See about\_Config\_Filtering for details. | false | false | 0 |
| SortBy | See about\_Config\_Filtering for details. | false | false |  |
| Filter | See about\_Config\_Filtering for details. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snap-in connects to.  You can provide this as a host name or an IP address. | false | false | LocalHost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Citrix.Configuration.Sdk.Serviceinstance<br>    This Represents A Service Instance And Has The Following Parameters;<br>    Servicegroupuid &lt;Guid&gt;<br>        The Unique Identifier For The Service Group To Which The Service Instance Belongs.<br>    Servicegroupname &lt;String&gt;<br>        The Name Of The Service Group To Which The Service Instance Belongs.<br>    Serviceinstanceuid &lt;Guid&gt;<br>        The Unique Identifier For The Service Instance.<br>    Servicetype &lt;String&gt;<br>        The Type Of The Service Group.<br>    Address &lt;String&gt;<br>        The Contact Address For The Service Instance.<br>    Binding &lt;String&gt;<br>        The Binding To Use For Connections To The Service Instance.<br>    Version &lt;Int&gt;<br>        The Version Of The Service Instance.<br>    Serviceaccount &lt;String&gt;<br>        The Ad Computer Account For The Computer That Is Providing The Service Instance.<br>    Serviceaccountsid &lt;String&gt;<br>        The Ad Computer Account Sid For The Computer That Is Providing The Service Instance.<br>    Interfacetype &lt;String&gt;<br>        The Interface Type For The Service Instance.<br>    Metadata &lt;Citrix.Configuration.Sdk.Metadata\[\]&gt;<br>        The Metadata For The Service Instance.

## Notes
In the case of failure, the following errors can result.<br>    Error Codes ----------- PartialData Only a subset of the available data was returned. CouldNotQuueryDatabase The query required to get the database was not defined. CommunicationError An error occurred while communicating with the service. DatabaseNotConfigured The operation could not be completed because the database for the service is not configured. InvalidFilter A filtering expression was supplied that could not be interpreted for this cmdlet. ExceptionThrown An unexpected error occurred.  To locate more details see the Windows event logs on the controller being used, or examine the XenDesktop logs.
## Examples

### Example 1
```
C:\>Get-ConfigRegisteredServiceInstance

Address            : http://MyServer.com:80/Citrix/MyContract/v1

Binding            : wcf_HTTP_kerb

InterfaceType      : SDK

Metadata           : {}

MetadataMap        : {}

ServiceAccount     : ENG\MyAccount$

ServiceAccountSid  : S-1-5-21-1155438255-2213498043-2452000591-1104

ServiceGroupName   : MyService

ServiceGroupUid    : 2b990d5a-bba9-413b-aa08-e104e67f89bc

ServiceInstanceUid : 8dc38b5a-3fbb-457c-b326-6c41c94c18d5

ServiceType        : MySnapIn

Version            : 1

Address            : http://MyServer.com:80/Citrix/MyContract/PeerAPI/v1

Binding            : wcf_HTTP_kerb

InterfaceType      : Peer

Metadata           : {}

MetadataMap        : {}

ServiceAccount     : ENG\MyAccount$

ServiceAccountSid  : S-1-5-21-1155438255-2213498043-2452000591-1104

ServiceGroupName   : MyService

ServiceGroupUid    : 2b990d5a-bba9-413b-aa08-e104e67f89bc

ServiceInstanceUid : 8f822ed6-42f3-4a26-911a-a4a6a87c0ef2

ServiceType        : MySnapIn

Version            : 1

Address            : http://MyServer.com:80/Citrix/MyContract/MyServiceEnvTestAPI/v1

Binding            : wcf_HTTP_kerb

InterfaceType      : EnvironmentTest

Metadata           : {}

MetadataMap        : {}

ServiceAccount     : ENG\MyAccount$

ServiceAccountSid  : S-1-5-21-1155438255-2213498043-2452000591-1104

ServiceGroupName   : MyService

ServiceGroupUid    : 2b990d5a-bba9-413b-aa08-e104e67f89bc

ServiceInstanceUid : d2d40d9b-2a5d-4c5a-b9ca-a7f73cffe4f2

ServiceType        : MySnapIn

Version            : 1

Address            : http://MyServer.com:80/Citrix/MyContract/MyServiceAPI/v1

Binding            : wcf_HTTP_kerb

InterfaceType      : InterService

Metadata           : {}

MetadataMap        : {}

ServiceAccount     : ENG\MyAccount$

ServiceAccountSid  : S-1-5-21-1155438255-2213498043-2452000591-1104

ServiceGroupName   : MyService

ServiceGroupUid    : 2b990d5a-bba9-413b-aa08-e104e67f89bc

ServiceInstanceUid : 5d428970-2ba1-4336-b8d0-f3aa961b8983

ServiceType        : MySnapIn

Version            : 1
```
#### Description
Return all the service instances that are registered in the Configuration Service.
### Example 2
```
C:\>Get-ConfigRegisteredServiceInstance -InterfaceType "SDK"

Address            : http://MyServer.com:80/Citrix/MyContract/v1

Binding            : wcf_HTTP_kerb

InterfaceType      : SDK

Metadata           : {}

MetadataMap        : {}

ServiceAccount     : ENG\MyAccount$

ServiceAccountSid  : S-1-5-21-1155438255-2213498043-2452000591-1104

ServiceGroupName   : MyService

ServiceGroupUid    : 2b990d5a-bba9-413b-aa08-e104e67f89bc

ServiceInstanceUid : 8dc38b5a-3fbb-457c-b326-6c41c94c18d5

ServiceType        : MySnapIn

Version            : 1
```
#### Description
Return all the service instances that are registered in the Configuration Service and are of type 'SDK'.
