---
title: 'Ibcpsession:: Bcpcolfmt (OLE DB) | Microsoft Docs'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- IBCPSession::BCPColFmt (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- BCPColFmt method
ms.assetid: 2852f4ba-f1c6-4c4c-86b2-b77e4abe70de
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e896f3e04d24becf136b7abefcff9dbe97fa0970
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48058683"
---
# <a name="ibcpsessionbcpcolfmt-ole-db"></a>IBCPSession::BCPColFmt(OLE DB)
  프로그램 변수와 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 열 간의 바인딩을 만듭니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
HRESULT BCPColFmt(   
DBORDINALidxUserDataCol,  
inteUserDataType,  
intcbIndicator,  
intcbUserData,  
BYTE *pbUserDataTerm,  
intcbUserDataTerm,  
DBORDINALidxServerCol);  
```  
  
## <a name="remarks"></a>Remarks  
 **BCPColFmt** 메서드는 BCP 데이터 파일 필드와 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 열 간의 바인딩을 만드는 데 사용됩니다. 열의 길이, 유형, 종결자 및 접두사 길이를 매개 변수로 사용하고 개별 필드에 대해 이러한 각 속성을 설정합니다.  
  
 사용자가 대화형 모드를 선택하면 이 메서드가 두 번 호출됩니다. 서버 열의 유형을 기반으로 하는 기본값에 따라 열 형식을 설정하기 위해 한 번 호출되고, 대화형 모드에서 각 열에 대해 선택된 클라이언트의 열 유형에 따라 형식을 설정하기 위해 한 번 호출됩니다.  
  
 비대화형 모드에서는 열당 한 번만 호출되어 각 열의 유형을 문자 또는 네이티브 유형으로 설정하고 열과 행 종결자를 설정합니다.  
  
 **BCPColFmt** 메서드를 사용하여 대량 복사에 사용할 사용자 파일 형식을 지정할 수 있습니다. 대량 복사의 경우 형식에는 다음과 같은 부분이 포함됩니다.  
  
-   사용자 파일 필드에서 데이터베이스 열로의 매핑  
  
-   각 사용자 파일 필드의 데이터 형식  
  
-   각 필드에 대한 표시기(옵션)의 길이  
  
-   사용자 파일 필드당 최대 데이터 길이  
  
-   각 필드에 대한 종결 바이트 시퀀스(옵션)  
  
-   선택 사항인 종결 바이트 시퀀스의 길이  
  
 **BCPColFmt** 에 대한 각 호출에서는 사용자 파일의 한 필드에 대한 서식을 지정합니다. 예를 들어 다섯 개의 필드로 구성된 사용자 데이터 파일에서 세 필드의 기본 설정을 변경하려면 먼저 `BCPColumns(5)`를 호출한 다음 **BCPColFmt** 를 다섯 번 호출합니다. 이 중 세 번의 호출에서 사용자 지정 형식을 설정합니다. 나머지 두 번의 호출에서는 *eUserDataType* 을 BCP_TYPE_DEFAULT로 설정하고 *cbIndicator*, *cbUserData*및 *cbUserDataTerm* 을 각각 0, BCP_VARIABLE_LENGTH 및 0으로 설정합니다. 이 프로시저는 다섯 개의 열을 모두 복사하는데 이 중 세 개는 사용자 지정된 형식으로, 두 개는 기본 형식으로 복사합니다.  
  
> [!NOTE]  
>  [BCPColFmt](ibcpsession-bcpcolumns-ole-db.md)가 호출되기 전에 **IBCPSession::BCPColumns** 메서드를 호출해야 합니다. 사용자 파일에 있는 각 열에 대해 **BCPColFmt** 를 한 번씩 호출해야 합니다. 사용자 파일의 열에 대해 **BCPColFmt** 를 두 번 이상 호출하면 오류가 발생합니다.  
  
 사용자 파일의 모든 데이터를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 테이블로 복사할 필요는 없습니다. 열을 건너뛰려면 idxServerCol 매개 변수를 0으로 설정하여 해당 열의 데이터 형식을 지정합니다. 필드를 건너뛰려는 경우에도 메서드가 제대로 작동하려면 모든 정보가 필요합니다.  
  
 **참고** [IBCPSession::BCPWriteFmt](ibcpsession-bcpwritefmt-ole-db.md) 함수를 사용하여 **BCPColFmt**를 통해 제공된 형식 지정을 저장할 수 있습니다.  
  
## <a name="arguments"></a>인수  
 *idxUserDataCol*[in]  
 사용자 데이터 파일에 포함된 필드의 인덱스입니다.  
  
 *eUserDataType*[in]  
 사용자 데이터 파일에 포함된 필드의 데이터 형식입니다. 사용 가능한 데이터 형식은 같거나는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 헤더 파일 (sqlncli.h) bcp_type_xxx 형식으로 예를 들어 BCP_TYPE_SQLINT4 합니다. BCP_TYPE_DEFAULT 값을 지정하면 공급자는 테이블 또는 뷰 열 유형과 동일한 유형을 사용합니다. 대량 복사 작업에 대 한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 파일로 때는 `eUserDataType` 인수는 인수가 BCP_TYPE_SQLDECIMAL 또는 BCP_TYPE_SQLNUMERIC:  
  
-   원본 열이 decimal 또는 numeric이 아니면 기본 전체 자릿수 및 소수 자릿수가 사용됩니다.  
  
-   원본 열이 decimal 또는 numeric이면 원본 열의 전체 자릿수 및 소수 자릿수가 사용됩니다.  
  
 *cbIndicator*[in]  
 필드의 접두사 길이입니다. 기본값은 BCP_PREFIX_DEFAULT입니다. 유효한 접두사 길이는 0, 1, 2, 4 및 8입니다. 접두사 크기 8은 주로 필드가 청크되었음을 나타내는 데 사용됩니다. 이 값은 큰 값 형식 열을 효율적으로 대량 복사하는 데 사용됩니다.  
  
 *cbUserData*[in]  
 길이 표시기나 종결자의 길이를 제외한 사용자 파일에 있는 이 필드 데이터의 최대 길이(바이트)입니다.  
  
 설정 `cbUserData` 를 bcp_length_null로 파일 필드에 있는 데이터의 모든 값을 나타내는 이거나 NULL로 설정 해야 합니다. 설정 `cbUserData` 를 bcp_length_variable로 시스템이 각 필드에 대 한 데이터의 길이 확인 함을 나타냅니다. 일부 필드의 경우 이 설정은 길이 또는 Null 표시기가 생성되어 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 복사되는 복사본의 데이터 앞에 추가됨을 의미하거나 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]로 복사되는 데이터에 표시기가 필요함을 나타냅니다.  
  
 에 대 한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 문자 및 이진 데이터 형식의 경우 `cbUserData` BCP_LENGTH_VARIABLE, BCP_LENGTH_NULL, 0 또는 양수 값일 수 있습니다. 경우 `cbUserData` 가 BCP_LENGTH_VARIABLE 이면 시스템 있으면 길이 표시기 나 종결자 시퀀스 중 하나를 사용 하 여 데이터의 길이를 결정 합니다. 길이 표시기와 종결자 시퀀스를 모두 지정하는 경우 대량 복사에는 복사되는 데이터 크기가 가장 작은 방법이 사용됩니다. 하는 경우 `cbUserData` 가 BCP_LENGTH_VARIABLE 이면 데이터 형식은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 문자 또는 이진 형식이 길이 표시기 나 종결자 시퀀스를 지정 하는 시스템 오류 메시지를 반환 합니다.  
  
 하는 경우 `cbUserData` 가 0 이거나 양수 값 이면 시스템은 `cbUserData` 최대 데이터 길이로 합니다. 그러나 양수 이면 `cbUserData`최소한의 데이터를 복사 하는 메서드를 사용 하 여 데이터 길이 확인 하는 시스템, 길이 표시기 나 종결자 시퀀스를 제공 합니다.  
  
 `cbUserData` 값 데이터의 바이트 수를 나타냅니다. 문자 데이터가 유니코드 와이드 문자로 다음 양수 표현 되는 경우 `cbUserData` 매개 변수 값의 각 문자를 바이트 단위로 크기를 곱한 문자의 수를 나타냅니다.  
  
 *pbUserDataTerm*[size_is][in]  
 이 필드에 사용할 종결자 시퀀스입니다. 이 매개 변수는 주로 문자 데이터 형식에 유용한데 그 이유는 다른 모든 형식은 길이가 고정되어 있거나 이진 데이터의 경우 현재 바이트 수를 정확하게 기록하기 위해 길이 표시기가 필요하기 때문입니다.  
  
 추출한 데이터가 종결되지 않도록 하거나 사용자 파일의 데이터가 종결되지 않았음을 나타내려면 이 매개 변수를 NULL로 설정하십시오.  
  
 종결자와 길이 표시기를 사용하거나 종결자와 최대 열 길이를 사용하는 등 두 가지 이상의 방법을 사용하여 사용자 파일 열 길이를 지정하는 경우 대량 복사에는 복사되는 데이터 크기가 가장 작은 방법이 선택됩니다.  
  
 대량 복사 API는 필요한 경우 유니코드에서 MBCS로의 문자 변환을 수행합니다. 종결자 바이트 문자열 및 바이트 문자열 길이가 모두 올바르게 설정되도록 주의해야 합니다.  
  
 *cbUserDataTerm*[in]  
 이 열에 사용할 종결자 시퀀스의 길이(바이트)입니다. 종결자가 없거나 데이터에 필요하지 않은 경우 이 값을 0으로 설정합니다.  
  
 *idxServerCol*[in]  
 데이터베이스 테이블에서 열의 서수 위치입니다. 첫 번째 열 번호는 1입니다. 열의 서수 위치는 **IColumnsInfo::GetColumnInfo** 또는 이와 유사한 메서드를 사용하여 확인할 수 있습니다. 이 값이 0이면 대량 복사에서 데이터 파일의 필드를 무시합니다.  
  
## <a name="return-code-values"></a>반환 코드 값  
 S_OK  
 메서드가 성공했습니다.  
  
 E_FAIL  
 공급자 관련 오류가 발생했습니다. 자세한 내용을 보려면 [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) 인터페이스를 사용하세요.  
  
 E_UNEXPECTED  
 예기치 않은 메서드가 호출되었습니다. 예를 들어 이 메서드를 호출하기 전에 [IBCPSession::BCPInit](ibcpsession-bcpinit-ole-db.md) 메서드를 호출하지 않았습니다.  
  
 E_INVALIDARG  
 잘못된 인수입니다.  
  
 E_OUTOFMEMORY  
 메모리 부족 오류가 발생했습니다.  
  
## <a name="see-also"></a>관련 항목  
 [IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md)   
 [대량 복사 작업 수행](../native-client/features/performing-bulk-copy-operations.md)  
  
  
