---
title: 유효성 검사 없이 암호화 사용 | Microsoft Docs
description: 유효성 검사 없이 암호화 사용
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- data access [OLE DB Driver for SQL Server], encryption
- cryptography [OLE DB Driver for SQL Server]
- MSOLEDBSQL, encryption
- encryption [OLE DB Driver for SQL Server]
- OLE DB Driver for SQL Server, encryption
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 41aa355de39aabc266e798b6870a8f43ceca4110
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47814731"
---
# <a name="using-encryption-without-validation"></a>유효성 검사 없이 암호화 사용
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서는 로그인과 관련한 네트워크 패킷이 항상 암호화됩니다. 서버를 시작할 때 제공된 인증서가 없으면 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]가 로그인 패킷을 암호화하는 데 사용할 자체 서명된 인증서를 생성합니다.  

자체 서명 된 인증서는 보안을 보장 하지 않습니다. 암호화 핸드셰이크는 NT LAN Manager (NTLM)에 기반 합니다. 보안 연결에 대 한 SQL Server에서 확인할 수 있는 인증서를 프로 비전 하는 것이 좋습니다. 인증서 유효성 검사에만 보안 보안 TLS (전송 계층)를 만들 수 있습니다.

응용 프로그램에 따라 연결 문자열 키워드나 연결 속성을 사용하여 모든 네트워크 트래픽을 암호화해야 할 수도 있습니다. **IDbInitialize::Initialize**에 공급자 문자열을 사용하는 경우 OLE DB에 대한 키워드는 "Encrypt"이고, **IDataInitialize**에 초기화 문자열을 사용하는 경우 ADO 및 OLE DB에 대한 키워드는 "Use Encryption for Data"입니다. 여도 구성할 수 있습니다이 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Configuration Manager를 사용 하는 **프로토콜 암호화 강제** 옵션을 선택한에서 암호화 된 연결을 요청 하도록 클라이언트를 구성 합니다. 기본적으로 연결의 모든 네트워크 트래픽을 암호화하려면 서버에 인증서를 제공해야 합니다. 서버에서 인증서를 신뢰 하도록 클라이언트를 설정 하 여 중간자 개입 공격에 취약 해질 수 있습니다. 서버에서 확인할 수 있는 인증서를 배포 하는 경우 인증서를 신뢰 하는 방법에 대 한 클라이언트 설정을 FALSE로 변경 하는 확인 합니다.

연결 문자열 키워드에 대한 내용은 [SQL Server용 OLE DB 드라이버에서 연결 문자열 키워드 사용](../../oledb/applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md )을 참조하세요.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Configuration Manager에서 **프로토콜 암호화 강제 사용** 및 **서버 인증서 신뢰** 옵션을 모두 설정하면 서버에 인증서가 제공되지 않은 경우에도 암호화를 사용할 수 있습니다. 이 경우 확인할 수 있는 인증서가 서버에 제공되지 않으면 유효성 검사 없이 자체 서명된 서버 인증서가 암호화에 사용됩니다.  
  
 응용 프로그램에서 "TrustServerCertificate" 키워드 또는 이 키워드의 관련 연결 특성을 사용하여 암호화를 보장할 수도 있습니다. 응용 프로그램 설정으로 인해 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 클라이언트 구성 관리자에서 설정한 보안 수준이 낮아지지는 않지만 더 강화될 수는 있습니다. 예를 들어 클라이언트에 대해 **프로토콜 암호화 강제 사용** 옵션을 설정하지 않았지만 애플리케이션 자체에서 암호화를 요청할 수 있습니다. 또한 서버 인증서가 제공되지 않은 경우에도 암호화를 보장할 수 있도록 응용 프로그램에서 암호화 및 "TrustServerCertificate"를 요청할 수도 있습니다. 그러나 클라이언트 구성에 "TrustServerCertificate"가 설정되어 있지 않은 경우에는 제공된 서버 인증서가 필요합니다. 다음 표에서는 이러한 모든 경우에 대해 설명합니다.  
  
|프로토콜 암호화 강제 사용 클라이언트 설정|서버 인증서 신뢰 클라이언트 설정|연결 문자열/연결 특성 Encrypt/Use Encryption for Data|연결 문자열/연결 특성 서버 인증서 신뢰|결과|  
|----------------------------------------------|---------------------------------------------|------------------------------------------------------------------------------|----------------------------------------------------------------------|------------|  
|아니오|해당 사항 없음|아니요(기본값)|무시됨|암호화가 수행되지 않습니다.|  
|아니오|해당 사항 없음|사용자 계정 컨트롤|아니요(기본값)|확인할 수 있는 서버 인증서가 있는 경우에만 암호화가 수행되고 그렇지 않으면 연결 시도가 실패합니다.|  
|아니오|해당 사항 없음|사용자 계정 컨트롤|사용자 계정 컨트롤|항상 암호화가 수행되지만 자체 서명된 서버 인증서가 사용될 수 있습니다.|  
|사용자 계정 컨트롤|아니오|무시됨|무시됨|확인할 수 있는 서버 인증서가 있는 경우에만 암호화가 수행되고 그렇지 않으면 연결 시도가 실패합니다.|  
|사용자 계정 컨트롤|사용자 계정 컨트롤|아니요(기본값)|무시됨|항상 암호화가 수행되지만 자체 서명된 서버 인증서가 사용될 수 있습니다.|  
|사용자 계정 컨트롤|예|사용자 계정 컨트롤|아니요(기본값)|확인할 수 있는 서버 인증서가 있는 경우에만 암호화가 수행되고 그렇지 않으면 연결 시도가 실패합니다.|  
|사용자 계정 컨트롤|예|예|사용자 계정 컨트롤|항상 암호화가 수행되지만 자체 서명된 서버 인증서가 사용될 수 있습니다.|  
||||||

> [!CAUTION]
> 앞의 표에서 다양 한 구성에서 시스템 동작에 지침을 제공합니다. 보안 연결에 대 한 암호화는 클라이언트와 서버 모두에 필요를 확인 합니다. 또한 인증서를 확인할 수 있고 서버에 있는지를 확인 합니다 **TrustServerCertificate** 클라이언트 설정을 FALSE로 설정 된 합니다.

## <a name="ole-db-driver-for-sql-server"></a>SQL Server용 OLE DB 드라이버 
 SQL Server용 OLE DB 드라이버는 DBPROPSET_SQLSERVERDBINIT 속성 집합에 구현된 SSPROP_INIT_TRUST_SERVER_CERTIFICATE 데이터 원본 초기화 속성이 추가되면서 유효성 검사 없이 암호화를 지원합니다. 또한 "TrustServerCertificate"라는 새로운 연결 문자열 키워드가 추가되었습니다. 이 문자열 키워드는 예 또는 아니요 값을 받으며, 기본값은 아니요입니다. 서비스 구성 요소를 사용하는 경우에는 True 또는 False 값을 받으며, 기본값은 False입니다.  
  
 DBPROPSET_SQLSERVERDBINIT 속성 집합에 대 한 향상 된 기능에 대 한 자세한 내용은 참조 하세요. [초기화 및 권한 부여 속성](../../oledb/ole-db-data-source-objects/initialization-and-authorization-properties.md)합니다.  

  
## <a name="see-also"></a>참고 항목  
 [SQL Server 기능용 OLE DB 드라이버](../../oledb/features/oledb-driver-for-sql-server-features.md)  
  
  
