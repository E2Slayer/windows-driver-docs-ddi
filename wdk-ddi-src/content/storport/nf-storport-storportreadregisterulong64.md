---
UID: NF:storport.StorPortReadRegisterUlong64
title: StorPortReadRegisterUlong64 macro (storport.h)
description: The StorPortReadRegisterUlong64 routine reads a 64-bit value from a specified 64-bit register address.
old-location: storage\storportreadregisterulong64.htm
tech.root: storage
ms.date: 03/29/2018
keywords: ["StorPortReadRegisterUlong64 macro"]
ms.keywords: StorPortReadRegisterUlong64, StorPortReadRegisterUlong64 routine [Storage Devices], storage.storportreadregisterulong64, storport/StorPortReadRegisterUlong64
req.header: storport.h
req.include-header: Storport.h
req.target-type: Universal
req.target-min-winverclnt: Available starting with Windows 8.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: 
targetos: Windows
req.typenames: 
f1_keywords:
 - StorPortReadRegisterUlong64
 - storport/StorPortReadRegisterUlong64
topic_type:
 - APIRef
 - kbSyntax
api_type:
 - HeaderDef
api_location:
 - storport.h
api_name:
 - StorPortReadRegisterUlong64
---

# StorPortReadRegisterUlong64 macro


## -description

The <b>StorPortReadRegisterUlong64</b> routine reads a 64-bit value from a specified 64-bit register address.

## -parameters

### -param h [in]


A pointer to the hardware device extension.

### -param r [in]


A pointer to the register where the data is to be read.

## -remarks

The <b>StorPortReadRegisterUlong64</b> routine is only available on the 64-bit version of Windows.

## -see-also

<a href="/windows-hardware/drivers/ddi/storport/nf-storport-storportwriteregisterulong64">StorPortWriteRegisterUlong64</a>
