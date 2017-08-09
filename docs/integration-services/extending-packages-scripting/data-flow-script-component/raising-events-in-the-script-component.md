---
title: "스크립트 구성 요소에서 이벤트를 발생 시키는 | Microsoft Docs"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Script component [Integration Services], raising events
ms.assetid: bb389073-e1d0-4794-8d29-c8b293b6a5e3
caps.latest.revision: 16
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 505855e82b683fc15ca00073f58e1f9cb348f830
ms.contentlocale: ko-kr
ms.lasthandoff: 08/03/2017

---
# <a name="raising-events-in-the-script-component"></a>스크립트 구성 요소에서 이벤트 발생
  이벤트를 사용하면 포함하는 패키지에 오류 및 경고와 태스크 진행률 또는 상태 같은 기타 정보를 보고할 수 있습니다. 패키지에서는 이벤트 알림을 관리하기 위한 이벤트 처리기를 제공합니다. 스크립트 구성 요소에서 메서드를 호출 하 여 이벤트를 발생 시킬 수는 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A> 의 속성은 **ScriptMain** 클래스입니다. 방법에 대 한 자세한 내용은 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 이벤트를 처리 하는 패키지를 참조 [Integration services&#40; Ssis&#41; 이벤트 처리기](../../../integration-services/integration-services-ssis-event-handlers.md)합니다.  
  
 이벤트는 패키지에서 사용할 수 있도록 설정된 모든 로그 공급자에 로깅될 수 있습니다. 로그 공급자는 이벤트에 대한 정보를 데이터 원본에 저장합니다. 스크립트 구성 요소에서는 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> 메서드를 사용하여 이벤트를 발생시키지 않고 로그 공급자에 정보를 로깅할 수도 있습니다. <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> 메서드의 사용 방법은 다음 섹션을 참조하십시오.  
  
 이벤트를 발생시키기 위해 스크립트 태스크에서는 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> 속성에 의해 제공된 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A> 인터페이스의 다음 메서드 중 하나를 호출합니다.  
  
|이벤트|Description|  
|-----------|-----------------|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireCustomEvent%2A>|패키지에서 사용자가 정의한 사용자 지정 이벤트를 발생시킵니다.|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireError%2A>|패키지에 오류 조건을 알립니다.|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireInformation%2A>|사용자에게 정보를 제공합니다.|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireProgress%2A>|패키지에 구성 요소 진행률을 알립니다.|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireWarning%2A>|구성 요소가 사용자 알림이 발생할 수 있지만 오류 조건은 아닌 상태에 있음을 패키지에 알립니다.|  
  
 다음은 Error 이벤트를 발생시키는 간단한 예입니다.  
  
 `Dim myMetadata as IDTSComponentMetaData100`  
  
 `myMetaData = Me.ComponentMetaData`  
  
 `myMetaData.FireError(...)`  
  
## <a name="see-also"></a>관련 항목:  
 [Integration Services &#40; Ssis&#41; 이벤트 처리기](../../../integration-services/integration-services-ssis-event-handlers.md)   
 [패키지에 이벤트 처리기를 추가 합니다.](http://msdn.microsoft.com/library/5e56885d-8658-480a-bed9-3f2f8003fd78)  
  
  