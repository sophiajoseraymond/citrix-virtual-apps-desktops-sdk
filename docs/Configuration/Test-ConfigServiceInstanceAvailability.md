
# Test-Configserviceinstanceavailability
Tests whether the supplied service instances are responding to requests.
## Syntax

```
Test-ConfigServiceInstanceAvailability [-ServiceInstance] <ServiceInstance[]> [-MaxDelaySeconds <Int32>] [-ForceWaitForOneOfEachType] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description



## Related Commands

* [Register-ConfigServiceInstance](../Register-ConfigServiceInstance/)
* [Unregister-ConfigRegisteredServiceInstance](../Unregister-ConfigRegisteredServiceInstance/)
* [Get-ConfigRegisteredServiceInstance](../Get-ConfigRegisteredServiceInstance/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ServiceInstance | The service instances to test. | true | true (ByValue) |  |
| MaxDelaySeconds | The timeout period to wait before concluding that services are unresponsive. | false | false | Infinite |
| ForceWaitForOneOfEachType | If at least one of each type of service responds, finish immediately. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| TraceParent | Specifies the trace parent assigned for internal diagnostic tracing use | false | false |  |
| TraceState | Specifies the trace state assigned for internal diagnostic tracing use | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the host name or IP address of the controller to which the PowerShell snap-in connects. | false | false | 'LocalHost'.  Once a value is specified by any command, this value becomes the new default. |

## Input Type

### 

## Return Values

### System.Management.Automation.Psobject
This represents a service instance and has the following parameters;  
    ServiceGroupUid &lt;Guid&gt;  
        The unique identifer for the service group to which the service instance belongs.  
    ServiceGroupName &lt;string&gt;  
        The name of the service group that the service instance is part of.  
    ServiceInstanceUid &lt;Guid&gt;  
        The unique identifier for the service instance.  
    ServiceType &lt;string&gt;  
        The type of the service group.  
    Address &lt;string&gt;  
        The contact address for the service instance.  
    Binding &lt;string&gt;  
        The binding to use for connections to the service instance.  
    Version &lt;int&gt;  
        The version of the service instance.  
    ServiceAccount &lt;string&gt;  
        The AD computer account for the computer that is providing the service instance.  
    ServiceAccountSid &lt;string&gt;  
        The AD computer account SID for the computer that is providing the service instance.  
    InterfaceType &lt;string&gt;  
        The interface type for the service instance.  
    Metadata &lt;Citrix.Configuration.Sdk.Metadata\[\]&gt;  
        The metadata for the service instance.  
    Status &lt;Citrix.Configuration.Sdk.Commands.Availability&gt;  
        An enumeration value indicating whether the service is Responding, NotResponding, Unknown, or BadBindingType.  
    ResponseTime &lt;System.TineSpan&gt;  
        The interval elapsed between hailing the service and getting a definite response
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
