---
title: "데이터 결합(Excel용 MDS 추가 기능) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a867dc15-5a0d-457c-8304-ac323bcf9377
caps.latest.revision: 6
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 6
---
# 데이터 결합(Excel용 MDS 추가 기능)
  에 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], 를 게시 하기 전에 데이터를 비교 하려는 경우 두 워크시트의 데이터를 결합 합니다. 이 절차에서는 두 워크시트의 데이터를 한 워크시트에 결합합니다. 그런 다음 추가 비교를 수행하여 MDS 저장소에 게시할 데이터를 결정할 수 있습니다.  
  
## 필수 구성 요소  
  
-   MDS 관리 데이터가 포함된 워크시트가 있어야 합니다. 자세한 내용은 참조 [Master Data Services에서 Excel로 데이터 내보내기](../../master-data-services/microsoft-excel-add-in/export-data-to-excel-from-master-data-services.md)합니다.  
  
-   MDS 관리 데이터와 결합할 데이터가 포함된 워크시트가 있어야 합니다. 이 시트에는 머리글 행이 있어야 합니다.  
  
### 관리되지 않는 데이터를 MDS 관리 시트에 결합하려면  
  
1.  MDS 관리 데이터가 포함 된 시트는 **게시 및 유효성 검사** 그룹에서 **데이터 결합**합니다.  
  
2.  **데이터 결합** 대화 상자에서 **MDS 데이터와 결합할 범위** 입력란 옆에 있는 아이콘을 클릭합니다. 대화 상자가 축소됩니다.  
  
3.  결합할 데이터가 포함된 시트를 클릭합니다.  
  
4.  머리글 행을 포함하여 결합할 시트에 있는 모든 셀을 강조 표시합니다.  
  
5.  **데이터 결합** 대화 상자에서 아이콘을 클릭합니다. 대화 상자가 확장됩니다.  
  
6.  MDS 엔터티에 대해 나열된 열에 대해 **해당 열**아래의 열을 선택합니다. 모든 MDS 열에 해당 열이 필요하지는 않습니다.  
  
7.  **결합**을 클릭합니다. 데이터가 MDS의 데이터인지 외부 원본에서 가져온 데이터인지를 나타내는 **원본** 열이 표시됩니다.  
  
## 다음 단계  
  
-   MDS 관리 및 외부 데이터 간의 유사성을 찾으려면 참조 [유사한 데이터 일치 & #40; MDS 추가 기능에서 Excel 및 #41;에 대 한](../../master-data-services/microsoft-excel-add-in/match-similar-data-mds-add-in-for-excel.md)합니다.  
  
## 참고 항목  
 [개요: Excel & #40; 데이터 내보내기 MDS 추가 기능에서 Excel 및 #41;에 대 한](../../master-data-services/microsoft-excel-add-in/overview-exporting-data-to-excel-mds-add-in-for-excel.md)   
 [Excel용 MDS 추가 기능의 데이터 품질 일치](../../master-data-services/microsoft-excel-add-in/data-quality-matching-in-the-mds-add-in-for-excel.md)  
  
  