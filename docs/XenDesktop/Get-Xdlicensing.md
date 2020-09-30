# Get-Xdlicensing

Get the licensing attributes for a site.

## Syntax

```
Get-XDLicensing [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description

Get the licensing attributes for the site which has a Controller identified by AdminAddress.

## Related Commands

* [Get-ConfigLicensingModel](../Get-ConfigLicensingModel/)
* [Get-ConfigProductEdition](../Get-ConfigProductEdition/)
* [Get-XDSite](../Get-XDSite/)
* [Set-XDLicensing](../Set-XDLicensing/)

## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| AdminAddress | Specifies the address of the Delivery Controller to which the PowerShell module will connect. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## Input Type

### None

You cannot pipe input to this cmdlet.
## Return Values


### Citrix.Xendesktoppowershellsdk.Serviceinterfaces.Configuration.Licenseinformation

A Citrix.XenDesktopPowerShellSdk.ServiceInterfaces.Configuration.LicenseInformation object containing the relevant attributes.

## Examples

### Example 1
```
C:\PS> Get-XDLicensing -AdminAddress MyController
```
#### Description

Get the licensing attributes of the Site which has a Controller identified by MyController.
