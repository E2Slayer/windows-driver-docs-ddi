---
UID: NS:nbl._NET_BUFFER_LIST_CONTEXT
title: NET_BUFFER_LIST_CONTEXT
ms.date: 11/30/2020
targetos: Windows
description: The NET_BUFFER_LIST_CONTEXT structure stores context information for a NET_BUFFER_LIST structure.
tech.root: netvista
req.construct-type: structure
req.ddi-compliance: 
req.dll: 
req.header: ndis/nbl.h
req.include-header: ndis.h
req.kmdf-ver: 
req.lib: 
req.max-support: 
req.redist: 
req.target-min-winverclnt: Supported in NDIS 6.0 and later.
req.target-min-winversvr: 
req.target-type: Windows
req.typenames: NET_BUFFER_LIST_CONTEXT, *PNET_BUFFER_LIST_CONTEXT
req.umdf-ver: 
req.unicode-ansi: 
topic_type:
 - apiref
api_type:
 - HeaderDef
api_location:
 - nbl.h
api_name:
 - _NET_BUFFER_LIST_CONTEXT
 - PNET_BUFFER_LIST_CONTEXT
 - NET_BUFFER_LIST_CONTEXT
f1_keywords:
 - _NET_BUFFER_LIST_CONTEXT
 - nbl/_NET_BUFFER_LIST_CONTEXT
 - PNET_BUFFER_LIST_CONTEXT
 - nbl/PNET_BUFFER_LIST_CONTEXT
 - NET_BUFFER_LIST_CONTEXT
 - nbl/NET_BUFFER_LIST_CONTEXT
dev_langs:
 - c++
---

# _NET_BUFFER_LIST_CONTEXT structure


## -description

The NET_BUFFER_LIST_CONTEXT structure stores context information for a 
  <a href="/windows-hardware/drivers/ddi/nbl/ns-nbl-net_buffer_list">NET_BUFFER_LIST</a> structure.

## -struct-fields

### -field Next

A pointer to the next NET_BUFFER_LIST_CONTEXT structure in a linked list of
     NET_BUFFER_LIST_CONTEXT structures.

### -field Size

The size, in bytes, of the entire context space in the NET_BUFFER_LIST_CONTEXT structure,
     including the used and unused context space.

### -field Offset

The offset, in bytes, from the beginning of the context data buffer to the start of the context
     data in the NET_BUFFER_LIST_CONTEXT structure. The 
     <b>Offset</b> member also specifies the size in bytes of the unused context space in the
     NET_BUFFER_LIST_CONTEXT structure.

### -field ContextData

The context data buffer. The context data can include any information that a driver
     requires.

## -remarks

Every 
    <a href="/windows-hardware/drivers/ddi/nbl/ns-nbl-net_buffer_list">NET_BUFFER_LIST</a> structure can include a
    preallocated NET_BUFFER_LIST_CONTEXT structure. As a NET_BUFFER_LIST structure travels through the driver
    stack, the linked list of NET_BUFFER_LIST_CONTEXT structures can expand to accommodate additional data
    space for each driver.

Drivers should use the following NDIS macros and functions to access and manipulate members in a
    NET_BUFFER_LIST_CONTEXT structure:

<ul>
<li>

<a href="/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisallocatenetbufferlistcontext">
       NdisAllocateNetBufferListContext</a>


</li>
<li>

<a href="/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisfreenetbufferlistcontext">
       NdisFreeNetBufferListContext</a>


</li>
<li>

<a href="/windows-hardware/drivers/network/net-buffer-list-context-data-start">
       NET_BUFFER_LIST_CONTEXT_DATA_START</a>


</li>
<li>

<a href="/windows-hardware/drivers/network/net-buffer-list-context-data-size">
       NET_BUFFER_LIST_CONTEXT_DATA_SIZE</a>


</li>
</ul>
The 
    <b>ContextData</b> member of the NET_BUFFER_LIST_CONTEXT structure specifies the data portion of the
    NET_BUFFER_LIST_CONTEXT structure. To improve system performance, a driver should preallocate any
    required context data space when the driver allocates a NET_BUFFER_LIST structure pool. To preallocate
    this data space, a driver calls the 
    <a href="/windows-hardware/drivers/ddi/nblapi/nf-nblapi-ndisallocatenetbufferlistpool">
    NdisAllocateNetBufferListPool</a> function and then specifies the amount of data space required in the 
    <i>ContextSize</i> parameter. Preallocation of this data space saves NDIS from allocating memory in the
    receive and send paths.

<div class="alert"><b>Note</b>  NDIS estimates the required context data space and, if necessary, adjusts the
    allocated data space to meet the requirements for the entire driver stack.</div>
<div> </div>
The 
    <b>Offset</b> member specifies the amount of unused context space in the NET_BUFFER_LIST_CONTEXT
    structure. The 
    <b>Offset</b> member also indicates the offset from the beginning of the 
    <b>ContextData</b> member to the start of the used context data space.

NDIS drivers call the 
    <a href="/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisallocatenetbufferlistcontext">
    NdisAllocateNetBufferListContext</a> function to allocate contiguous buffer space in the
    NET_BUFFER_LIST_CONTEXT structure. If necessary, NDIS allocates a new NET_BUFFER_LIST_CONTEXT structure
    with additional space to honor the request. NDIS drivers call the 
    <a href="/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisfreenetbufferlistcontext">
    NdisFreeNetBufferListContext</a> function to free the buffer space.

Use the 
    <a href="/windows-hardware/drivers/network/net-buffer-list-context-data-size">
    NET_BUFFER_LIST_CONTEXT_DATA_SIZE</a> macro to obtain the size of the used context space. Use the 
    <a href="/windows-hardware/drivers/network/net-buffer-list-context-data-start">
    NET_BUFFER_LIST_CONTEXT_DATA_START</a> macro to get the starting address of the used context space.

For more information on how to use net buffers, see 
    <a href="/windows-hardware/drivers/network/net-buffer-architecture">NET_BUFFER Architecture</a>.

## -see-also

<a href="/windows-hardware/drivers/ddi/nbl/ns-nbl-net_buffer">NET_BUFFER</a>



<a href="/windows-hardware/drivers/ddi/nbl/ns-nbl-net_buffer_list">NET_BUFFER_LIST</a>



<a href="/windows-hardware/drivers/network/net-buffer-list-context-data-size">
   NET_BUFFER_LIST_CONTEXT_DATA_SIZE</a>



<a href="/windows-hardware/drivers/network/net-buffer-list-context-data-start">
   NET_BUFFER_LIST_CONTEXT_DATA_START</a>



<a href="/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisallocatenetbufferlistcontext">
   NdisAllocateNetBufferListContext</a>



<a href="/windows-hardware/drivers/ddi/nblapi/nf-nblapi-ndisallocatenetbufferlistpool">
   NdisAllocateNetBufferListPool</a>



<a href="/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisfreenetbufferlistcontext">NdisFreeNetBufferListContext</a>

