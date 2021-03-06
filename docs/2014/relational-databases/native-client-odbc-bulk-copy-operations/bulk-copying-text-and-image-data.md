---
title: 텍스트 및 이미지 데이터 대량 복사 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- bulk copy [ODBC], text data
- SQL Server Native Client ODBC driver, bulk copy
- bulk copy [ODBC], image data
- ODBC, bulk copy operations
ms.assetid: 87155bfa-3a73-4158-9d4d-cb7435dac201
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c468ec3cf52526192893458055cde857aeaa864d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48103833"
---
# <a name="bulk-copying-text-and-image-data"></a>텍스트 및 이미지 데이터 대량 복사
  큰 **텍스트**를 **ntext**, 및 **이미지** 값은 대량 복사를 사용 하는 [bcp_moretext](../native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md) 함수입니다. 코드를 작성할 [bcp_bind](../native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md) 에 대 한 합니다 **텍스트**, **ntext**, 또는 **이미지** 열을 *pData* 포인터가으로 설정 NULL 나타내는 데이터가 제공 됩니다 **bcp_moretext**합니다. 각각에 대해 제공 하는 데이터의 정확한 길이 지정 하는 것이 반드시 **텍스트**를 **ntext**, 또는 **이미지** 각 대량 복사 행의 열입니다. 열에 대 한 데이터의 길이에 지정 된 열 길이와 다르면 [bcp_bind](../native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md)를 사용 하 여 [bcp_collen](../native-client-odbc-extensions-bulk-copy-functions/bcp-collen.md) 길이를 설정할 적절 한 값입니다. A [bcp_sendrow](../native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md) 보냅니다 모든 비**텍스트**아닌-**ntext**, 및 비-**이미지** 데이터; 호출 **bcp_moretext** 보내도록 합니다 **텍스트**를 **ntext**, 또는 **이미지** 별도 단위로 데이터입니다. 대량 복사 함수는 모든 데이터가 현재 전송 된 확인 **텍스트**하십시오 **ntext**, 또는 **이미지** 통해보낼데이터의길이합계열**bcp_moretext** 최신에 지정 된 길이 같으면 **bcp_collen** 하거나 **bcp_bind**합니다.  
  
 **bcp_moretext** 에 열을 식별 하 매개 변수가 없습니다. 여러 **텍스트**, **ntext**, 또는 **이미지** 행에 열 **bcp_moretext** 에서 작동 하는 **텍스트**, **ntext**, 또는 **이미지** 열 서 수 번호가 가장 낮은 및 서 수 번호가 가장 높은 열으로 진행 되 고 열으로 시작 합니다. **bcp_moretext** 라인이 한 열에서 다음에 전송 된 데이터의 길이 합계 최신에 지정 된 길이 같으면 **bcp_collen** 하거나 **bcp_bind** 현재 열에 대 한 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [대량 복사 작업 수행 &#40;ODBC&#41;](performing-bulk-copy-operations-odbc.md)  
  
  
