
# Get-Userprofiledefinition
Gets the high level description of a configuration for profile management, based on a byte array (blob).
## Syntax

```
Get-UserProfileDefinition [-ByteArray] <Byte[]> [-ExcludeUnconfigured] [<CommonParameters>]
```

## Detailed Description
Use this command to convert a configuration byte array into a set of named property settings. The byte array will either have been retrieved from the Broker, or from the New-UserProfileConfiguration cmdlet.


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ByteArray | Specifies the low-level byte array (blob) to be interpreted. | true | true (ByValue) |  |
| ExcludeUnconfigured | When this switch is supplied, the returned object will only carry the properties whose values have been explicitly set. Properties whose values are unconfigured will be omitted. When this switch is not supplied, the full set of configuration properties will be returned, and any unconfigured settings will just appear to be set to their default value. | false | false |  |

## Input Type

### Byte\[\]
The cmdlet accepts the ByteArray parameter as pipeline input.
## Return Values

### System.Management.Automation.Psobject
This cmdlet outputs a single PSObject with multiple properties. Each property denotes one setting within the configuration set. The following is a summary of the properties and their data types:  
ServiceActive  (bool?)  
ProcessedGroups  (string\[\])  
ExcludedGroups  (string\[\])  
ProcessAdmins  (bool?)  
UserStorePath  (string)  
PSMidSessionWriteBack  (bool?)  
OfflineSupport  (bool?)  
DeleteCachedProfilesOnLogoff  (bool?)  
ProfileDeleteDelay  (int?)  
MigrateWindowsProfilesToUserStore  (MigrateWindowsProfilesToUserStoreEnum?)  
LocalProfileConflictHandling  (LocalProfileConflictHandlingEnum?)  
TemplateProfilePath  (string)  
TemplateProfileOverridesLocalProfile  (bool?)  
TemplateProfileOverridesRoamingProfile  (bool?)  
TemplateProfileIsMandatory  (bool?)  
LoadRetries  (int?)  
ProcessCookieFiles  (bool?)  
DisableDynamicConfig  (bool?)  
LogoffRatherThanTempProfile  (bool?)  
DebugMode  (bool?)  
LogLevel\_Warnings  (bool?)  
LogLevel\_Information  (bool?)  
LogLevel\_FileSystemNotification  (bool?)  
LogLevel\_FileSystemActions  (bool?)  
LogLevel\_RegistryActions  (bool?)  
LogLevel\_RegistryDifference  (bool?)  
LogLevel\_ActiveDirectoryActions  (bool?)  
LogLevel\_PolicyUserLogon  (bool?)  
LogLevel\_Logon  (bool?)  
LogLevel\_Logoff  (bool?)  
LogLevel\_UserName  (bool?)  
MaxLogSize  (int?)  
DebugFilePath  (string)  
ExclusionList  (string\[\])  
IncludeListRegistry  (string\[\])  
ExclusionListSyncFiles  (string\[\])  
ExclusionListSyncDir  (string\[\])  
SyncDirList  (string\[\])  
SyncFileList  (string\[\])  
MirrorFoldersList  (string\[\])  
PSEnabled  (bool?)  
PSAlwaysCache\_Enabled  (bool?)  
PSAlwaysCache  (int?)  
PSPendingLockTimeout  (int?)  
PSUserGroups  (string\[\])  
CPEnable  (bool?)  
CPUserGroups  (string\[\])  
CPSchemaPathData  (string)  
CPPathData  (string)  
CPMigrationFromBaseProfileToCPStore  (bool?)  
FRAdminAccess  (bool?)  
FRIncDomainName  (bool?)  
FRAppDataEnabled  (FRAppDataEnum?)  
FRAppDataPath  (string)  
FRDesktopEnabled  (FRDesktopEnum?)  
FRDesktopPath  (string)  
FRStartMenuEnabled  (FRStartMenuEnum?)  
FRStartMenuPath  (string)  
FRDocumentsEnabled  (FRDocumentsEnum?)  
FRDocumentsPath  (string)  
FRPicturesEnabled  (FRPicturesEnum?)  
FRPicturesPath  (string)  
FRMusicEnabled  (FRMusicEnum?)  
FRMusicPath  (string)  
FRVideosEnabled  (FRVideosEnum?)  
FRVideosPath  (string)  
FRFavoritesEnabled  (FRFavoritesEnum?)  
FRFavoritesPath  (string)  
FRContactsEnabled  (FRContactsEnum?)  
FRContactsPath  (string)  
FRDownloadsEnabled  (FRDownloadsEnum?)  
FRDownloadsPath  (string)  
FRLinksEnabled  (FRLinksEnum?)  
FRLinksPath  (string)  
FRSearchesEnabled  (FRSearchesEnum?)  
FRSearchesPath  (string)  
FRSavedGamesEnabled  (FRSavedGamesEnum?)  
FRSavedGamesPath  (string)
## Examples

### Example 1

```
C:\PS> $blob = New-UserProfileConfiguration  
  
C:\PS>Get-UserProfileDefinition -ByteArray $blob
```

#### Description
The first command creates a fresh configuration set in its default state, and stores it in a Windows PowerShell variable. The second command interprets the new blob, and would output the individual properties of the default configuration.
### Example 2

```
C:\PS> New-UserProfileConfiguration | Get-UserProfileDefinition
```

#### Description
This command creates a fresh configuration set in its default state, and pipes the resulting byte array through to Get-UserProfileDefinition, which will interpret it and output its individual properties.
