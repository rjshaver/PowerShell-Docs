---
external help file: PSITPro5_PSGet.xml
online version: fba585bf-f5ef-40b2-9c05-9deeee77e187
schema: 2.0.0
---

# Get-PSRepository
## SYNOPSIS
Gets PowerShell repositories.

## SYNTAX

```
Get-PSRepository [[-Name] <String[]>]
```

## DESCRIPTION
The Get-PSRepository cmdlet gets PowerShell module repositories that are registered for the current user.

## EXAMPLES

### Example 1: Get all module repositories
```
PS C:\>Get-PSRepository
Name                                     SourceLocation                                     OneGetProvider       InstallationPolicy
----                                     --------------                                     --------------       ------------------
PSGallery                                http://go.micro...                                 NuGet                Untrusted
myNuGetSource                            https://myget.c...                                 NuGet                Trusted
```

This command gets all module repositories registered for the current user.

### Example 2: Get module repositories by name
```
PS C:\>Get-PSRepository -Name "*NuGet*"
```

This command gets all module repositories that include NuGet in their names.

### Example 3: Get a module repository and format the output
```
PS C:\>Get-PSRepository -Name "Local01" | Format-List * -Force
Name                      : local01
SourceLocation            : http://manikb-dev:8765/api/v2/
Trusted                   : True
Registered                : True
InstallationPolicy        : Trusted
PackageManagementProvider : NuGet
PublishLocation           : http://pattif-dev:8765/api/v2/package/
ScriptSourceLocation      : http://pattif-dev:8765/api/v2/artifacts/psscript
ScriptPublishLocation     : http://pattif-dev:8765/api/v2/package/
ProviderOptions           : {}
```

This command gets the repository named Local01 and uses the pipeline operator to pass that object to the Format-List cmdlet.

## PARAMETERS

### -Name
Specifies the names of the repositories to get.

```yaml
Type: String[]
Parameter Sets: (All)
Aliases: 

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Register-PSRepository](fba585bf-f5ef-40b2-9c05-9deeee77e187)

[Set-PSRepository](a512c852-8b73-49bb-b339-74d5438c4aa7)

[Unregister-PSRepository](0566904d-fa61-41ff-87d4-6471fe449d9b)
