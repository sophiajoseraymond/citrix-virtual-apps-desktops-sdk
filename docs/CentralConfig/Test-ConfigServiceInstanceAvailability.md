
# Test-Configserviceinstanceavailability
Tests whether the supplied service instances are responding to requests.
## Syntax
```
Test-ConfigServiceInstanceAvailability [-ServiceInstance] <ServiceInstance[]> [-MaxDelaySeconds <Int32>] [-ForceWaitForOneOfEachType] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description



## Related Commands

* [Register-ConfigServiceInstance](./Register-ConfigServiceInstance/)
* [Unregister-ConfigRegisteredServiceInstance](./Unregister-ConfigRegisteredServiceInstance/)
* [Get-ConfigRegisteredServiceInstance](./Get-ConfigRegisteredServiceInstance/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ServiceInstance | The service instances to test. | true | true (ByValue) |  |
| MaxDelaySeconds | The timeout period to wait before concluding that services are unresponsive. | false | false | Infinite |
| ForceWaitForOneOfEachType | If at least one of each type of service responds, finish immediately. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| AdminAddress | Specifies the host name or IP address of the controller to which the PowerShell snap-in connects. | false | false | 'LocalHost'.  Once a value is specified by any command, this value becomes the new default. |

## Input Type

### 

## Return Values

### System.Management.Automation.Psobject<br>    This Represents A Service Instance And Has The Following Parameters;<br>    Servicegroupuid &lt;Guid&gt;<br>        The Unique Identifer For The Service Group To Which The Service Instance Belongs.<br>    Servicegroupname &lt;String&gt;<br>        The Name Of The Service Group That The Service Instance Is Part Of.<br>    Serviceinstanceuid &lt;Guid&gt;<br>        The Unique Identifier For The Service Instance.<br>    Servicetype &lt;String&gt;<br>        The Type Of The Service Group.<br>    Address &lt;String&gt;<br>        The Contact Address For The Service Instance.<br>    Binding &lt;String&gt;<br>        The Binding To Use For Connections To The Service Instance.<br>    Version &lt;Int&gt;<br>        The Version Of The Service Instance.<br>    Serviceaccount &lt;String&gt;<br>        The Ad Computer Account For The Computer That Is Providing The Service Instance.<br>    Serviceaccountsid &lt;String&gt;<br>        The Ad Computer Account Sid For The Computer That Is Providing The Service Instance.<br>    Interfacetype &lt;String&gt;<br>        The Interface Type For The Service Instance.<br>    Metadata &lt;Citrix.Configuration.Sdk.Metadata\[\]&gt;<br>        The Metadata For The Service Instance.<br>    Status &lt;Citrix.Configuration.Sdk.Commands.Availability&gt;<br>        An Enumeration Value Indicating Whether The Service Is Responding, Notresponding, Unknown, Or Badbindingtype.<br>    Responsetime &lt;System.Tinespan&gt;<br>        The Interval Elapsed Between Hailing The Service And Getting A Definite Response

## Notes
The Availability Status Codes are o Responding: Got a positive response o NotResponding: Got a response, but it was negative or the connection was refused o Unknown: Did not respond in time / timed-out o BadBindingType: Binding parameter in ServiceInstance is not wcf\_HTTP\_kerb
## Examples

### Example 1
```
C:\>Get-ConfigRegisteredServiceInstance | Test-ConfigServiceInstanceAvailability -ForceWaitForOneOfEachType
```
#### Description
Test all the service instances that are registered in the Configuration Service, returning when one of each type is responding.
### Example 2
```
C:\>Test-ConfigServiceInstanceAvailability -ServiceInstance $services -MaxDelaySeconds 5
```
#### Description
Test each of the given services, allowing a 5 second time-out.
