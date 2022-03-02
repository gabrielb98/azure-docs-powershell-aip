---
external help file: AipService.dll-Help.xml
Module Name: AIPService
ms.assetid: B81D7053-016A-44C2-896A-040F6510C7ED
online version: https://go.microsoft.com/fwlink/?linkid=2045300
schema: 2.0.0
---

# Get-AipServiceTrackingLog

## SYNOPSIS
Gets tracking information for documents protected by Azure Information Protection.

This cmdlet is supported by both the Azure Information Protection classic and unified labeling clients, with different usage, as described below.

## SYNTAX
```
Get-AipServiceTrackingLog -ContentId <Guid> [-FromTime <DateTime>] [-ToTime <DateTime>] [-WhatIf] [-Confirm]
 [<CommonParameters>]

```

## DESCRIPTION
The **Get-AipServiceTrackingLog** cmdlet runs a query to return protection information about tracked documents.

Information returned includes:

- The document content ID, with the document name if available.
- The Rights Management issuer.
- The users who accessed the document, when, and from what location. 
- What protection template ID or specific usage rights were used to protect the document and whether access was granted or denied.
- The _IsHiddenInfo_ property, which will always be **false**. This property is used to hide events for users where tracking is disabled. 

You can specify a start time and stop time of entries to include. The output is returned as a list of PowerShell objects in the PowerShell console.

The **Get-AipServiceTracking** cmdlet returns tracking information about a protected document with a specified contentID. 

To retrieve the contentID for a specific document, use the [Get-AipServiceDocumentLog](Get-AipServiceDocumentLog.md) cmdlet.

## EXAMPLES

### Example 1: Get tracking data for a specific document, using its contentId
```
PS C:\>Get-AipServiceDocumentLog -ContentId c03bf90c-6e40-4f3f-9ba0-2bcd77524b87
```

This command runs a query to return tracking information for a specific document, with a contentID value of **c03bf90c-6e40-4f3f-9ba0-2bcd77524b87** 


## PARAMETERS

### -Confirm
Prompts you for confirmation before running the cmdlet.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ContentId
Specifies the contentID value for the document you want to return tracking data for.

To retrieve the contentID for a specific document, use the [Get-AipServiceDocumentLog](Get-AipServiceDocumentLog.md) cmdlet.
 
```yaml
Type: String
Parameter Sets: (All)
Aliases: cf

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FromTime
Specifies the start time (inclusive) for the log file as a **DateTime** object. To obtain a **DateTime** object, use the [Get-Date](/powershell/module/Microsoft.PowerShell.Utility/Get-Date?viewFallbackFrom=powershell-4.0) cmdlet. Specify the date and time according to your system locale settings. For more information, type `Get-Help Get-Date`.

```yaml
Type: DateTime
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ToTime
Specifies the stop time (inclusive) for the log file as a **DateTime** object. To obtain a **DateTime** object, use the [Get-Date](/powershell/module/Microsoft.PowerShell.Utility/Get-Date?viewFallbackFrom=powershell-4.0) cmdlet. Specify the date and time according to your system locale settings. For more information, type `Get-Help Get-Date`.

```yaml
Type: DateTime
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UserEmail
Specifies the email address of the user. The cmdlet gets the tracking information for documents that were protected by, or accessed by the user who has this email address. 

```yaml
Type: String
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -WhatIf
Shows what would happen if the cmdlet runs. The cmdlet is not run.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. 

For more information, see [about_CommonParameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Get-AipServiceDocumentLog](./Get-AipServiceDocumentLog.md)
