---
UID: NF:prdrvcom.ConvertDevModeToPrintTicket
title: ConvertDevModeToPrintTicket function (prdrvcom.h)
description: The IPrintOemPrintTicketProvider::ConvertDevModeToPrintTicket method converts a DEVMODEW structure into a print ticket.
old-location: print\iprintoemprintticketprovider_convertdevmodetoprintticket.htm
tech.root: print
ms.date: 02/26/2018
keywords: ["ConvertDevModeToPrintTicket function"]
ms.keywords: ConvertDevModeToPrintTicket, ConvertDevModeToPrintTicket method [Print Devices], ConvertDevModeToPrintTicket method [Print Devices], IPrintOemPrintTicketProvider interface, IPrintOemPrintTicketProvider interface [Print Devices], ConvertDevModeToPrintTicket method, IPrintOemPrintTicketProvider::ConvertDevModeToPrintTicket, prdrvcom/IPrintOemPrintTicketProvider::ConvertDevModeToPrintTicket, print.iprintoemprintticketprovider_convertdevmodetoprintticket, print_ticket-package_4605321f-640a-438b-a4cc-6e34ef5521b1.xml
f1_keywords:
 - "prdrvcom/IPrintOemPrintTicketProvider.ConvertDevModeToPrintTicket"
 - "IPrintOemPrintTicketProvider.ConvertDevModeToPrintTicket"
req.header: prdrvcom.h
req.include-header: Prdrvcom.h
req.target-type: Desktop
req.target-min-winverclnt:
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
topic_type:
- APIRef
- kbSyntax
api_type:
- COM
api_location:
- prdrvcom.h
api_name:
- IPrintOemPrintTicketProvider.ConvertDevModeToPrintTicket
targetos: Windows
req.typenames: SHIMOPTS, *PSHIMOPTS
req.product: Windows 10 or later.
---

# ConvertDevModeToPrintTicket function


## -description


The <code>IPrintOemPrintTicketProvider::ConvertDevModeToPrintTicket</code> method converts a <a href="/windows/win32/api/wingdi/ns-wingdi-devmodew">DEVMODEW</a> structure into a print ticket.


## -parameters




### -param cbDevmode [in]

The size, in bytes, of the input <a href="/windows/win32/api/wingdi/ns-wingdi-devmodew">DEVMODEW</a> structure. The size includes both the public and private portions of this structure.


### -param pDevmode [in]

A pointer to the input DEVMODEW structure.


### -param pPrintTicket [in, out]

A pointer to the partially-completed print ticket. When <code>IPrintOemPrintTicketProvider::ConvertDevModeToPrintTicket</code> returns, all of the entries in the print ticket should be filled in.


### -param cbDrvPrivateSize [in]

The size, in bytes, of the plug-in's private DEVMODEW structure.


### -param pPrivateDevmode [in]

A pointer to the plug-in's private <a href="/windows/win32/api/wingdi/ns-wingdi-devmodew">DEVMODEW</a> structure.


## -returns



<code>IPrintOemPrintTicketProvider::ConvertDevModeToPrintTicket</code> should return S_OK if the operation succeeds. Otherwise, this method should return a standard COM error code.




## -remarks



The core driver calls the <code>IPrintTicketProvider::ConvertDevModeToPrintTicket</code> method with an input print ticket that is populated with public and Unidrv-private or Pscript5-private features. The plug-in is free to set <a href="/windows/win32/api/wingdi/ns-wingdi-devmodew">DEVMODEW</a> settings in the public part or in the plug-in's private part, based on settings in the input print ticket. In addition to setting new DEVMODEW items, the plug-in can modify existing settings in the public portion of the DEVMODEW structure.

The DEVMODEW structure fields that correlate with the part of the DEVMODEW structure of interest to the client will already have been populated before <code>IPrintOemPrintTicketProvider::ConvertDevModeToPrintTicket</code> is called, including the public portion of the DEVMODEW structure and excluding the privately-defined values in the public portion of the DEVMODEW structure.




## -see-also




<a href="/windows-hardware/drivers/ddi/prcomoem/nn-prcomoem-iprintoemprintticketprovider">IPrintOemPrintTicketProvider</a>



<a href="/windows-hardware/drivers/ddi/prcomoem/nf-prcomoem-iprintoemprintticketprovider-convertprinttickettodevmode">IPrintOemPrintTicketProvider::ConvertPrintTicketToDevMode</a>
 

 
