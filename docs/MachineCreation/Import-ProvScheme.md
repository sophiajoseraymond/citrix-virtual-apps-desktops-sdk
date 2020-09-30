
# Import-Provscheme
Import a provisioning scheme into the site
## Syntax
```
Import-ProvScheme [-ProvisioningSchemeData <String>] [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
This cmdlet imports a provisioning scheme into the site, the data passed to this cmdlet should be obtained via the Export-ProvScheme cmdlet generally obtained form a different site


## Related Commands

* [Export-ProvScheme](../Export-ProvScheme/)
* [Export-AcctIdentityPool](../Export-AcctIdentityPool/)
* [Import-AcctIdentityPool](../Import-AcctIdentityPool/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ProvisioningSchemeData | Json encoded string of a provisioning scheme | false | true (ByPropertyName) |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Citrix.Machinecreation.Sdk.Provisioningscheme<br>    This Object Provides Details Of The Provisioning Scheme And Contains The Following Information:<br>    Provisioningschemeuid &lt;Guid&gt;<br>        The Unique Identifier For The Provisioning Scheme.<br>    Provisioningschemename &lt;String&gt;<br>        The Name Of The Provisioning Scheme.<br>    Cpucount &lt;Int&gt;<br>        The Number Of Processors That Vms Will Be Created With When Using This Scheme.<br>    Memorymb &lt;Int&gt;<br>        The Maximum Amount Of Memory That Vms Will Be Created With When Using This Scheme.<br>    Masterimagevm &lt;String&gt;<br>        The Path Within The Hosting Unit Provider To The Copy Of The Vm Snapshot That The Scheme Uses.<br>    Masterimagevmdate &lt;Datetime&gt;<br>        The Date And Time That The Copy Was Made Of The Vm Snapshot Used By The Scheme.<br>    Identitypooluid &lt;Guid&gt;<br>        The Unique Identifier Of The Identity Pool (From The Adidentity Powershell Snap-In) That The Scheme Uses.<br>    Identitypoolname &lt;String&gt;<br>        The Name Of The Identity Pool (From The Adidentity Powershell Snap-In) That The Scheme Uses.<br>    Hostingunituid &lt;Guid&gt;<br>       The Unique Identifier Of The Hosting Unit (From The Hosting Unit Powershell Snap-In) That The Scheme Uses.<br>    Hostingunitname &lt;String&gt;<br>       The Name Of The Hosting Unit (From The Hosting Unit Powershell Snap-In) That The Scheme Uses.<br>    Cleanonboot &lt;Boolean&gt;<br>       Indicates Whether The Vms That Are Created Will Be Reset To A Clean State On Each Boot.<br>    Taskid &lt;Guid&gt;<br>       The Identifier Of Any Current Task That Is Running For The Provisioning Scheme.<br>    Metadata &lt;Citrix.Machinecreation.Sdk.Metadata\[\]&gt;<br>       The Metadata Associated With This Provisioning Scheme.<br>    Controlleraddress &lt;String\[\]&gt;<br>       The Dns Names Of The Controllers Associated With This Provisioning Scheme For Quick Deploy Purposes.<br>    Vmmetadata &lt;Char\[\]&gt;<br>        The Opaque Vm Metadata Block<br>    Usepersonalvdiskstorage &lt;Bool&gt;<br>        True If The Scheme Will Use Personal Vdisk Storage.<br>    Personalvdiskdriveletter &lt;Char&gt;<br>        The Drive Letter For The Personal Vdisk<br>    Personalvdiskdrivesize &lt;Int&gt;<br>        The Size Of The Personal Vdisk In Gb<br>    Profileusagepercentage &lt;Double&gt;<br>        The Percentage Of The Personal Vdisk To Be Used For Profile Data<br>    Dedicatedtenancy &lt;Bool&gt;<br>        Whether To Use Dedicated Tenancy When Creating Machines In Cloud Hypervisors.<br>    Currentmasterimageuid &lt;Guid&gt;<br>        The Unique Identifier Of The Current Master Image Used By The Provisioning Scheme. (See Get-Provschememastervmimagehistory.)<br>    Usewritebackcache &lt;Bool&gt;<br>        True If The Scheme Will Use The Wrote Back Cache Feature.<br>    Writebackcachedisksize &lt;Int&gt;<br>          The Size Of The Write Back Cache Disk If Specified In Gb.<br>    Writebackcachememorysize &lt;Int&gt;<br>          The Size Of The Write Back Memory Cache If Specified In Mb.<br>    Usefulldiskcloneprovisioning &lt;Bool&gt;<br>          Indicates Whether The Machines Are Provisioned Using The Dedicated Full Disk Clone Feature.

## Notes
In the case of failure, the following errors can result.<br>    Error Codes<br>    CouldNotQueryDatabase<br>    The query required to get the database was not defined.<br>    PermissionDenied<br>    The user does not have administrative rights to perform this operation.<br>    ConfigurationLoggingError<br>    The operation could not be performed because of a configuration logging error<br>    CommunicationError<br>    An error occurred while communicating with the service.<br>    DatabaseNotConfigured<br>    The operation could not be completed because the database for the service is not configured.
## Examples

### Example 1
```
Import-ProvScheme -ProvisioningSchemeData $provisioningSchemeData
```
#### Description
Import the json encoded data that is in \$provisioningSchemeData
