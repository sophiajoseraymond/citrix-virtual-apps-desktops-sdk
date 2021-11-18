
# Get-Monitorserviceinstance
Gets the service instance entries for the Monitor Service.
## Syntax

```
Get-MonitorServiceInstance [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
Returns service interfaces published by instances of the Monitor Service. Each instance of a service publishes multiple interfaces with distinct interface types, and each of these interfaces is represented as a ServiceInstance object. Service instances can be used to register the service with a central configuration service so that other services can use the functionality.

You do not need to configure a database connection to use this command.


## Related Commands

* [Get-MonitorServiceStatus](../Get-MonitorServiceStatus/)
* [Reset-MonitorServiceGroupMembership](../Reset-MonitorServiceGroupMembership/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| TraceParent | Specifies the trace parent assigned for internal diagnostic tracing use | false | false |  |
| TraceState | Specifies the trace state assigned for internal diagnostic tracing use | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a Citrix Virtual Apps and Desktops 7 controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Citrix.Monitor.Sdk.Serviceinstance
The Get-MonitorServiceInstance command returns an object containing the following properties.  
ServiceGroupUid &lt;Guid&gt;  
    Specifies the unique identifier for the service group of which the service is a member.  
ServiceGroupName &lt;String&gt;  
    Specifies the name of the service group of which the service is a member.  
ServiceInstanceUID &lt;Guid&gt;  
    Specifies the unique identifier for registered service instances, which are service instances held by and obtained from a central configuration service.  Unregistered service instances do not have unique identifiers.  
ServiceType &lt;String&gt;  
    Specifies the service instance type.  For this service, the service instance type is always Monitor.  
Address  
    Specifies the address of the service instance.  The address can be used to access the service and, when registered in the central configuration service, can be used by other services to access the service.  
Binding  
    Specifies the binding type that must be used to communicate with the service instance.  In this release of Citrix Virtual Apps and Desktops 7, the binding type is always 'wcf\_HTTP\_kerb'. This indicates that the service provides a Windows Communication Foundation endpoint that uses HTTP binding with integrated authentication.  
Version  
    Specifies the version of the service instance.  The version number is used to ensure that the correct versions of the services are used for communications.  
ServiceAccount &lt;String&gt;  
    Specifies the Active Directory account name for the machine on which the service instance is running.  The account name is used to provide information about the permissions required for interservice communications.  
ServiceAccountSid &lt;String&gt;  
    Specifies the Active Directory account security identifier for the machine on which the service instance is running.  
InterfaceType &lt;String&gt;  
    Specifies the interface type.  Each service can provide multiple service instances, each for a different purpose, and the interface defines the purpose.  Available interfaces are:  
        SDK - for PowerShell operations  
        InterService - for operations between different services  
        Peer - for communications between services of the same type  
Metadata &lt;Citrix.Monitor.Sdk.Metadata\[\]&gt;  
     The collection of metadata associated with registered service instances, which are service instances held by and obtained from a central configuration service.  Metadata is not stored for unregistered service instances.
## Notes
If the command fails, the following errors can be returned.  
    Error Codes  
    -----------  
    DatabaseError  
        An error occurred in the service while attempting a database operation.  
    DatabaseNotConfigured  
        The operation could not be completed because the database for the service is not configured.  
    DataStoreException  
        An error occurred in the service while attempting a database operation - communication with the database failed for various reasons.  
    PermissionDenied  
        You do not have permission to execute this command.  
    AuthorizationError  
        There was a problem communicating with the Citrix Delegated Administration Service.  
    CommunicationError  
        There was a problem communicating with the remote service.  
    ExceptionThrown  
        An unexpected error occurred.  For more details, see the Windows event logs on the controller or the Citrix Virtual Apps and Desktops 7 logs.
## Examples

### Example 1

```
c:\PS>Get-MonitorServiceInstance  
  
Address            : http://MyServer.com:80/Citrix/Monitor/Monitor  
  
Binding            : wcf_HTTP_kerb  
  
InterfaceType      : SDK  
  
Metadata           :  
  
MetadataMap        :  
  
ServiceAccount     : ENG\MyAccount$  
  
ServiceAccountSid  : S-1-5-21-2406005612-3133289213-1653143164  
  
ServiceGroupName   : MyServiceGroup  
  
ServiceGroupUid    : a88d2f6b-c00a-4f76-9c38-e8330093b54d  
  
ServiceInstanceUid : 00000000-0000-0000-0000-000000000000  
  
ServiceType        : Monitor  
  
Version            : 1  
  
Address            : http://MyServer.com:80/Citrix/Monitor/MonitorApi  
  
Binding            : wcf_HTTP_kerb  
  
InterfaceType      : InterService  
  
Metadata           :  
  
MetadataMap        :  
  
ServiceAccount     : ENG\MyAccount  
  
ServiceAccountSid  : S-1-5-21-2406005612-3133289213-1653143164  
  
ServiceGroupName   : MyServiceGroup  
  
ServiceGroupUid    : a88d2f6b-c00a-4f76-9c38-e8330093b54d  
  
ServiceInstanceUid : 00000000-0000-0000-0000-000000000000  
  
ServiceType        : Monitor  
  
Version            : 1
```

#### Description
Get all instances of the Monitor Service running on the specified machine.  For remote services, use the AdminAddress parameter to define the service for which the interfaces are required.  If the AdminAddress parameter has not been specified for the runspace, service instances running on the local machine are returned.
