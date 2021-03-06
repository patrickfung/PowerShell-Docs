﻿---
author: jpjofre
description: 
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell, cmdlet
manager: carolz
ms.date: 2016-09-30
ms.prod: powershell
ms.technology: powershell
ms.topic: reference
online version: http://go.microsoft.com/fwlink/?LinkID=517140
schema: 2.0.0
title: Save-Package
---

# Save-Package

## SYNOPSIS
Saves packages to the local computer without installing them.

## SYNTAX

### PackageBySearch
```
Save-Package [[-Name] <String[]>] [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-Source <String[]>] [-Path <String>] [-LiteralPath <String>]
 [-Credential <PSCredential>] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ProviderName <String[]>]
 [<CommonParameters>]
```

### PackageByInputObject
```
Save-Package [-Path <String>] [-LiteralPath <String>] -InputObject <SoftwareIdentity>
 [-Credential <PSCredential>] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### PSModule:PackageByInputObject
```
Save-Package [-Path <String>] [-LiteralPath <String>] [-Credential <PSCredential>] [-Force] [-ForceBootstrap]
 [-WhatIf] [-Confirm] [-PackageManagementProvider <String>] [-Scope <String>] [-PublishLocation <String>]
 [-AllVersions] [-Filter <String>] [-Tag <String[]>] [-Includes <String[]>] [-DscResource <String[]>]
 [-Command <String[]>] [<CommonParameters>]
```

### PSModule
```
Save-Package [-Path <String>] [-LiteralPath <String>] [-Credential <PSCredential>] [-Force] [-ForceBootstrap]
 [-WhatIf] [-Confirm] [-PackageManagementProvider <String>] [-Scope <String>] [-PublishLocation <String>]
 [-AllVersions] [-Filter <String>] [-Tag <String[]>] [-Includes <String[]>] [-DscResource <String[]>]
 [-Command <String[]>] [<CommonParameters>]
```

## DESCRIPTION
The **Save-Package** cmdlet saves packages to the local computer without installing them.
This cmdlet saves the newest version of a package unless you specify the *AllVersions* parameter.
The *DestinationPath* and *LiteralPath* parameters are mutually exclusive, and cannot be added to the same command.

## EXAMPLES

### Example 1: Save a package to the local computer
```
PS C:\>Save-Package -Name "DSCAccelerator" -DestinationPath "C:\Users\TestUser\Downloads"
```

This example saves the newest version of a package, DSCAccelerator, to the C:\Users\TestUser\Downloads folder.

### Example 2: Save an exact version of a package
```
PS C:\>Save-Package -Name "DSCAccelerator" -RequiredVersion "2.1.2" -DestinationPath "C:\Users\TestUser\Downloads"
```

This example saves only version 2.1.2 of a package, DSCAccelerator, to the C:\Users\TestUser\Downloads folder.

### Example 3: Save a package by piping results of Find-Package
```
PS C:\>Find-Package -Name "DSCAccelerator" -RequiredVersion "2.1.2" | Save-Package -DestinationPath "C:\Users\TestUser\Downloads"
```

This command saves a package named DSCAccelerator by first locating the exact package with the **Find-Package** cmdlet, then piping the results of **Find-Package** to the **Save-Package** cmdlet.

### Example 4: Save a package to a local folder, then install the package
```
PS C:\>Save-Package "notepad2" -DestinationPath "C:\temp"
PS C:\>Install-Package "C:\temp\notepad2.4.2.25.3.nupkg"
```

The first command saves a package to C:\temp, a folder on the local computer.
The second command installs the saved package from the C:\temp folder, instead of installing from the web.

## PARAMETERS

### -AllVersions
Indicates that this cmdlet saves all available versions of the package.
By default, **Save-Package** only returns the newest available version.

```yaml
Type: SwitchParameter
Parameter Sets: PSModule:PackageByInputObject, PSModule
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Command
Specifies one or more commands included in the package.

```yaml
Type: String[]
Parameter Sets: PSModule:PackageByInputObject, PSModule
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm
Prompts you for confirmation before running the cmdlet.Prompts you for confirmation before running the cmdlet.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential
Specifies a user account that has rights to save a package from a specified package provider or source.

```yaml
Type: PSCredential
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DscResource
Specifies one or more Desired State Configuration (DSC) resources for the package.

```yaml
Type: String[]
Parameter Sets: PSModule:PackageByInputObject, PSModule
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Filter
Specifies a filter for the package.

```yaml
Type: String
Parameter Sets: PSModule:PackageByInputObject, PSModule
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force
Indicates that this cmdlet overrides restrictions that prevent the command from succeeding, as long as running the command does not compromise security.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ForceBootstrap
Indicates that this cmdlet forces Package Management to automatically install the package provider for the specified package.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Includes
Indicates the resources that the package includes.

```yaml
Type: String[]
Parameter Sets: PSModule:PackageByInputObject, PSModule
Aliases: 
Accepted values: DscResource, Cmdlet, Function

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject
A software ID object that represents the package that you want to save.
Software IDs are part of the results of the Find-Package cmdlet.

```yaml
Type: SoftwareIdentity
Parameter Sets: PackageByInputObject
Aliases: 

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -LiteralPath
Specifies the literal path to which you want to save the package.
You cannot add both this parameter and the *DestinationPath* parameter to the same command.

```yaml
Type: String
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaximumVersion
Specifies the maximum allowed version of the package that you want to save.
If you do not add this parameter, **Save-Package** saves the highest available version of the package.

```yaml
Type: String
Parameter Sets: PackageBySearch
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MinimumVersion
Specifies the minimum allowed version of the package that you want to find.
If you do not add this parameter, **Find-Package** finds the highest available version of the package that also satisfies any maximum specified version specified by the *MaximumVersion* parameter.

```yaml
Type: String
Parameter Sets: PackageBySearch
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name
Specifies one or more package names.

```yaml
Type: String[]
Parameter Sets: PackageBySearch
Aliases: 

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PackageManagementProvider
Specifies the Package Management provider.

```yaml
Type: String
Parameter Sets: PSModule:PackageByInputObject, PSModule
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path
Specifies the path at which to save the package.

```yaml
Type: String
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProviderName
Specifies one or more provider names.

```yaml
Type: String[]
Parameter Sets: PackageBySearch
Aliases: Provider
Accepted values: msi, Programs, msu, Bootstrap, PSModule, nuget, chocolatey

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PublishLocation
Specifies the publish location.

```yaml
Type: String
Parameter Sets: PSModule:PackageByInputObject, PSModule
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RequiredVersion
Specifies the exact version of the package to save.
If you do not add this parameter, **Save-Package** finds the highest available version of the provider that also satisfies any maximum version specified by the *MaximumVersion* parameter.

```yaml
Type: String
Parameter Sets: PackageBySearch
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Scope
{{Fill Scope Description}}

```yaml
Type: String
Parameter Sets: PSModule:PackageByInputObject, PSModule
Aliases: 
Accepted values: CurrentUser, AllUsers

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Source
Specifies one or more package sources.

```yaml
Type: String[]
Parameter Sets: PackageBySearch
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Tag
Specifies a tag to search for within the package metadata.

```yaml
Type: String[]
Parameter Sets: PSModule:PackageByInputObject, PSModule
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf
Shows what would happen if the cmdlet runs.
The cmdlet is not run.Shows what would happen if the cmdlet runs.
The cmdlet is not run.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### You cannot pipe input to this cmdlet.

## OUTPUTS

### This cmdlet does not generate any output.

## NOTES

## RELATED LINKS

[about_PackageManagement](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[Get-Package](Get-Package.md)

[Install-Package](Install-Package.md)

[Save-Package](Save-Package.md)

[Uninstall-Package](Uninstall-Package.md)

