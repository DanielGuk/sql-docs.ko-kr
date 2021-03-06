---
title: Microsoft 신경망 알고리즘 기술 참조 | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 76e71ae9c0ceb236c49df8e7fc8ec67713ef3e76
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/10/2018
ms.locfileid: "34018250"
---
# <a name="microsoft-neural-network-algorithm-technical-reference"></a>Microsoft 신경망 알고리즘 기술 참조
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] 신경망은 최대 3 계층의 뉴런 또는 *퍼셉트론*으로 구성된 *다중 계층 퍼셉트론* 신경망(*역전파 델타 규칙 네트워크*)을 사용합니다. 이러한 3개의 계층은 입력 계층, 출력 계층 및 숨겨진 계층(옵션)입니다.  
  
 다중 계층 퍼셉트론 신경망에 대한 자세한 내용은 이 설명서에서 다루지 않습니다. 이 항목에서는 입력 및 출력 값을 정규화하는 데 사용되는 방법과 특성 카디널리티를 줄이는 데 사용되는 기능 선택 방법을 포함하여 알고리즘의 기본 구현에 대해 설명합니다. 또한 이 항목에서는 알고리즘의 동작을 사용자 지정하는 데 사용할 수 있는 매개 변수 및 기타 설정을 설명하고 모델 쿼리에 대한 추가 정보로 연결되는 링크를 제공합니다.  
  
## <a name="implementation-of-the-microsoft-neural-network-algorithm"></a>Microsoft 신경망 알고리즘 구현  
 다중 계층 퍼셉트론 신경망에서 각 뉴런은 하나 이상의 입력을 받아 하나 이상의 동일한 출력을 생성합니다. 각 출력은 뉴런에 대한 입력 합계의 간단한 비선형 함수입니다. 입력은 입력 계층의 노드에서 숨겨진 계층의 노드로 전달된 후 숨겨진 계층에서 출력 계층으로 전달됩니다. 계층 내 뉴런 사이에는 연결이 없습니다. 로지스틱 회귀 모델에서와 같이 숨겨진 계층이 포함되지 않은 경우에는 입력이 입력 계층의 노드에서 출력 계층의 노드로 직접 전달됩니다.  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 신경망 알고리즘을 사용하여 생성된 신경망에는 다음과 같은 3가지 유형의 뉴런이 있습니다.  
  
**입력 뉴런**  
  
 입력 뉴런은 데이터 마이닝 모델의 입력 특성 값을 제공합니다. 불연속 입력 특성의 경우 입력 뉴런은 일반적으로 입력 특성의 단일 상태를 나타냅니다. 학습 데이터에 해당 특성에 대한 Null이 들어 있는 경우 누락 값도 여기에 포함됩니다. 3개 이상의 상태가 있는 불연속 입력 특성은 각 상태에 대해 하나씩의 입력 뉴런과 누락된 상태에 대한 입력 뉴런 하나(학습 데이터에 Null이 있는 경우)를 생성합니다. 연속 입력 특성은 두 개의 입력 뉴런, 즉 누락된 상태에 대한 뉴런 하나와 연속 특성 자체의 값에 대한 뉴런 하나를 생성합니다. 입력 뉴런은 하나 이상의 숨겨진 뉴런에 입력을 제공합니다.  
  
**Hidden neurons**  
  
 숨겨진 뉴런은 입력 뉴런에서 입력을 받아 출력 뉴런에 출력을 제공합니다.  
  
**출력 뉴런**  
  
 출력 뉴런은 데이터 마이닝 모델의 예측 가능한 특성 값을 나타냅니다. 불연속 입력 특성의 경우 출력 뉴런은 일반적으로 누락된 값을 포함한 예측 가능한 특성의 단일 예측 상태를 나타냅니다. 예를 들어 예측 가능한 이진 특성은 해당 특성의 값이 있는지 여부를 나타내기 위해 누락된 상태 또는 기존 상태를 설명하는 출력 노드 하나를 생성합니다. 예측 가능한 특성으로 사용되는 부울 열은 3개의 출력 뉴런, 즉 true 값에 대해 뉴런 하나, false 값에 대해 뉴런 하나, 그리고 누락된 상태나 기존 상태에 대해 뉴런 하나를 생성합니다. 3개 이상의 상태가 있는 예측 가능한 불연속 특성은 각 상태에 대해 출력 뉴런 하나와 누락된 상태 또는 기존 상태에 대해 출력 뉴런 하나를 생성합니다. 예측 가능한 연속 열은 두 개의 출력 뉴런, 즉 누락된 상태 또는 기존 상태에 대해 뉴런 하나와 연속 열 자체 값에 대해 뉴런 하나를 생성합니다. 예측 가능한 열 집합을 검토하여 500개가 넘는 출력 뉴런이 생성되는 경우 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 에서는 마이닝 모델에 새 네트워크를 생성하여 추가 출력 뉴런을 나타냅니다.  
  
 뉴런은 해당 뉴런이 있는 신경망의 계층에 따라 다른 뉴런이나 다른 데이터에서 입력을 받습니다. 입력 뉴런은 원래 데이터에서 입력을 받습니다. 숨겨진 뉴런과 출력 뉴런은 신경망에 있는 다른 뉴런의 출력에서 입력을 받습니다. 입력은 뉴런 간에 관계를 설정하며 이러한 관계는 특정 사례 집합에 대한 분석 경로 역할을 합니다.  
  
 각 입력에는 *가중치*라는 값이 할당되어 있으며 이 값은 숨겨진 뉴런 또는 출력 뉴런에 대한 특정 입력의 관련성 또는 중요도를 설명합니다. 입력에 할당된 가중치가 클수록 해당 입력 값의 관련성 또는 중요도도 큽니다. 가중치는 음수가 될 수 있으며 이 경우 입력이 특정 뉴런을 활성화하는 것이 아니라 차단할 수 있음을 의미합니다. 특정 뉴런에 대한 입력의 중요도를 강조하기 위해 각 입력 값에 가중치를 곱합니다. 음수 가중치의 경우 값에 가중치를 곱하면 중요도가 낮아집니다.  
  
 각 뉴런에는 *활성화 함수*라는 간단한 비선형 함수가 할당되어 있으며 이 함수는 신경망 계층에 대한 특정 뉴런의 관련성 또는 중요도를 설명합니다. 숨겨진 뉴런은 활성화 함수로 *쌍곡 탄젠트* 함수(tanh)를 사용하는 반면 출력 뉴런은 활성화 함수로 *시그모이드* 함수를 사용합니다. 두 함수는 모두 신경망이 입력 뉴런과 출력 뉴런 간의 비선형 관계를 모델링할 수 있도록 하는 비선형 연속 함수입니다.  
  
### <a name="training-neural-networks"></a>신경망 학습  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 신경망 알고리즘을 사용하는 데이터 마이닝 모델의 학습에는 여러 단계가 필요합니다. 이러한 단계는 알고리즘 매개 변수에 지정한 값에 따라 큰 영향을 받습니다.  
  
 알고리즘은 먼저 데이터 원본에서 학습 데이터를 평가 및 추출합니다. *홀드아웃 데이터*라는 학습 데이터의 비율은 네트워크의 정확도를 평가하는 데 사용하기 위해 예약됩니다. 학습 프로세스 중 네트워크는 학습 데이터에 대한 각 반복 후에 즉시 평가됩니다. 정확도가 더 이상 높아지지 않으면 학습 프로세스가 중지됩니다.  
  
 *SAMPLE_SIZE* 및 *HOLDOUT_PERCENTAGE* 매개 변수의 값은 학습 데이터에서 샘플링할 사례 수와 홀드아웃 데이터로 예약할 사례 수를 결정하는 데 사용됩니다. *HOLDOUT_SEED* 매개 변수 값은 홀드아웃 데이터로 예약할 개별 사례를 임의로 결정하는 데 사용됩니다.  
  
> [!NOTE]  
>  이러한 알고리즘 매개 변수는 마이닝 구조에 적용되어 테스트 데이터 집합을 정의하는 HOLDOUT_SIZE 및 HOLDOUT_SEED 속성과는 다릅니다.  
  
 그런 다음 알고리즘은 마이닝 모델이 지원하는 네트워크의 수 및 복잡도를 확인합니다. 마이닝 모델이 예측에만 사용되는 특성을 하나 이상 포함하면 이러한 모든 특성을 나타내는 단일 네트워크가 생성됩니다. 마이닝 모델이 입력 및 예측에 모두 사용되는 특성을 하나 이상 포함하면 알고리즘 공급자는 각 특성에 대해 네트워크를 하나씩 생성합니다.  
  
 불연속 값이 포함된 입력 및 예측 가능한 특성의 경우 각 입력 또는 출력 뉴런이 각각 단일 상태를 나타냅니다. 연속 값이 포함된 입력 및 예측 가능한 특성의 경우에는 각 입력 또는 출력 뉴런이 각각 특성 값의 범위 및 분포를 나타냅니다. 두 경우 모두에서 지원되는 최대 상태 수는 *MAXIMUM_STATES* 알고리즘 매개 변수 값에 따라 달라집니다. 특정 특성의 상태 수가 *MAXIMUM_STATES* 알고리즘 매개 변수 값을 초과하면 해당 특성에 대해 가장 많이 사용되거나 해당 특성과 관련성이 가장 높은 상태가 최대값을 초과하지 않는 한도 내에서 선택되고 나머지 상태는 분석을 위해 누락된 값으로 그룹화됩니다.  
  
 그런 다음 알고리즘은 *HIDDEN_NODE_RATIO* 매개 변수 값을 사용하여 숨겨진 계층에 대해 만들 초기 뉴런 수를 결정합니다. *HIDDEN_NODE_RATIO* 를 0으로 설정하여 알고리즘이 마이닝 모델에 대해 생성하는 네트워크에서 숨겨진 계층의 생성을 방지하고 신경망을 로지스틱 회귀 분석으로 처리할 수 있습니다.  
  
 알고리즘 공급자는 이전에 예약된 학습 데이터 집합을 사용하고 *일괄 학습*이라는 프로세스를 통해 홀드아웃 데이터에 있는 각 사례의 실제 알려진 값을 네트워크의 예측과 비교하여 네트워크 전반의 모든 입력 가중치를 반복하여 동시에 평가합니다. 알고리즘은 전체 학습 데이터 집합을 평가한 후 각 뉴런의 예측 값 및 실제 값을 검토합니다. 이때 오류 정도(있는 경우)를 계산하고 *역전파*라는 프로세스를 통해 출력 뉴런에서 입력 뉴런으로 반대 방향으로 작업하여 해당 뉴런에 대한 입력과 연결된 가중치를 조정합니다. 그런 다음 전체 학습 데이터 집합에 대해 이 프로세스를 반복합니다. 알고리즘에 다양한 가중치 및 출력 뉴런을 사용할 수 있으므로 입력에 대한 가중치 할당 및 평가를 위해 켤레 경사도 알고리즘을 사용하여 학습 프로세스를 진행할 수 있습니다. 켤레 경사도 알고리즘에 대한 자세한 내용은 이 설명서에서 다루지 않습니다.  
  
### <a name="feature-selection"></a>기능 선택  
 입력 특성의 수가 *MAXIMUM_INPUT_ATTRIBUTES* 매개 변수 값보다 크고 예측 가능한 특성의 수가 *MAXIMUM_OUTPUT_ATTRIBUTES* 매개 변수 값보다 크면 마이닝 모델에 포함된 네트워크의 복잡도를 낮추기 위해 기능 선택 알고리즘이 사용됩니다. 기능 선택은 통계상 모델과 가장 관련성이 높은 특성만 남겨 입력 또는 예측 가능한 특성 수를 줄입니다.  
  
 모든 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터 마이닝 알고리즘에서는 자동으로 기능 선택을 사용하여 분석을 향상시키고 처리 로드를 줄입니다. 신경망 모델의 기능 선택에 사용되는 방법은 특성의 데이터 형식에 따라 달라집니다. 다음 표에서는 참조를 위해 신경망 모델에 사용되는 기능 선택 방법과 신경망 알고리즘을 기반으로 하는 로지스틱 회귀 알고리즘에 사용되는 기능 선택 방법을 보여 줍니다.  
  
|알고리즘|분석 방법|설명|  
|---------------|------------------------|--------------|  
|신경망|흥미도 점수<br /><br /> Shannon Entropy<br /><br /> Bayesian with K2 Prior<br /><br /> Bayesian Dirichlet with uniform prior(기본값)|데이터에 연속 열이 포함된 경우 신경망 알고리즘에서는 Entropy 기반 및 Bayesian 점수 매기기 방법을 모두 사용할 수 있습니다.<br /><br /> 기본.|  
|로지스틱 회귀|흥미도 점수<br /><br /> Shannon Entropy<br /><br /> Bayesian with K2 Prior<br /><br /> Bayesian Dirichlet with uniform prior(기본값)|이 알고리즘에 매개 변수를 전달하여 기능 선택 동작을 제어할 수 없기 때문에 기본값이 사용됩니다. 그러므로 모든 특성이 불연속 또는 분할된 특성일 경우 기본값은 BDEU입니다.|  
  
 신경망 모델의 기능 선택을 제어하는 알고리즘 매개 변수는 MAXIMUM_INPUT_ATTRIBUTES, MAXIMUM_OUTPUT_ATTRIBUTES 및 MAXIMUM_STATES입니다. HIDDEN_NODE_RATIO 매개 변수를 설정하여 숨겨진 계층 수를 제어할 수도 있습니다.  
  
### <a name="scoring-methods"></a>점수 매기기 방법  
 *점수 매기기* 는 정규화의 한 종류로서, 신경망 모델 학습 컨텍스트에서는 불연속 텍스트 레이블과 같은 값을 네트워크에서 다른 유형의 입력과 비교하고 가중치를 적용할 수 있는 값으로 변환하는 프로세스를 의미합니다. 예를 들어 한 입력 특성이 Gender이고 가능한 값은 Male 및 Female이며 다른 입력 특성은 Income이고 값 범위가 가변적인 경우, 각 특성의 값은 직접 비교할 수 없으므로 가중치를 계산할 수 있도록 공통적인 배율로 인코딩되어야 합니다. 점수 매기기는 이러한 입력을 숫자 값, 특히 확률 범위로 정규화하는 프로세스입니다. 정규화에 사용되는 함수는 극단적인 값으로 인해 분석 결과가 왜곡되지 않도록 입력 값을 동일한 배율로 보다 균일하게 분산시키는 데도 유용합니다.  
  
 신경망의 출력도 인코딩됩니다. 출력(즉, 예측)에 대한 단일 대상이 있거나 예측에만 사용되고 입력에는 사용되지 않는 여러 대상이 있는 경우에는 모델에서 단일 네트워크를 만들기 때문에 값을 정규화할 필요가 없을 수 있습니다. 그러나 입력 및 예측에 여러 개의 특성이 사용된 경우에는 모델에서 여러 네트워크를 만들어야 하므로 모든 값을 정규화해야 하며 네트워크에서 출력이 나갈 때 출력도 인코딩해야 합니다.  
  
 입력에 대한 인코딩은 학습 사례에 있는 각 불연속 값을 더하고 그 합에 가중치를 곱한 값을 기반으로 합니다. 이를 *가중치 합*이라고 하며 이 값은 숨겨진 계층의 활성화 함수에 전달됩니다. 인코딩에는 다음과 같이 z 점수가 사용됩니다.  
  
 **불연속 값**  
  
 `μ = p` – 상태의 사전 확률  
  
 `StdDev  = sqrt(p(1-p))`  
  
 **연속 값**  
  
 현재 값= `1 - μ/σ`  
  
 기존 값 없음= `-μ/σ`  
  
 값이 인코딩된 후 입력은 네트워크 가장자리를 가중치로 하여 가중치 합을 구하는 과정을 거칩니다.  
  
 출력에 대한 인코딩에는 예측에 매우 유용한 속성이 있는 시그모이드 함수가 사용됩니다. 이러한 속성 중 하나는 원래 값의 배율 조정 방식과 값이 양수인지 음수인지에 관계없이 이 함수의 출력이 항상 확률을 0에서 1 사이의 값이므로 확률을 예상하는 데 적합하다는 것입니다. 또 다른 유용한 속성은 시그모이드 함수에 다듬기 효과가 있으므로 값이 굴곡 지점에서 멀리 벗어날수록 값의 확률은 천천히 0 또는 1에 가까워진다는 것입니다.  
  
## <a name="customizing-the-neural-network-algorithm"></a>신경망 알고리즘 사용자 지정  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 신경망 알고리즘은 결과 마이닝 모델의 동작, 성능 및 정확도에 영향을 주는 여러 매개 변수를 지원합니다. 열에 모델링 플래그를 설정하여 모델의 데이터 처리 방식을 수정하거나 분산 플래그를 설정하여 열 내의 값이 처리되는 방식을 지정할 수도 있습니다.  
  
### <a name="setting-algorithm-parameters"></a>알고리즘 매개 변수 설정  
 다음 표에서는 Microsoft 신경망 알고리즘에서 사용할 수 있는 매개 변수에 대해 설명합니다.  
  
 HIDDEN_NODE_RATIO  
 입력 및 출력 뉴런에 대한 숨겨진 뉴런의 비율을 지정합니다. 다음 수식에서는 숨겨진 계층의 초기 뉴런 수를 결정합니다.  
  
 HIDDEN_NODE_RATIO * SQRT(총 입력 뉴런 \* 총 출력 뉴런)  
  
 기본값은 4.0입니다.  
  
 HOLDOUT_PERCENTAGE  
 홀드아웃 오류를 계산하는 데 사용되는 학습 데이터 내의 사례 비율을 지정합니다. 이 비율은 마이닝 모델 학습 중 중지 조건의 일부로 사용됩니다.  
  
 기본값은 30입니다.  
  
 HOLDOUT_SEED  
 알고리즘이 홀드아웃 데이터를 임의로 결정할 때 난수 생성기의 초기값으로 사용할 숫자를 지정합니다. 이 매개 변수를 0으로 설정하면 알고리즘은 마이닝 모델의 이름을 기반으로 초기값을 생성하여 다시 처리하는 동안 모델 콘텐츠가 동일하게 유지되도록 합니다.  
  
 기본값은 0입니다.  
  
 MAXIMUM_INPUT_ATTRIBUTES  
 기능 선택을 사용하기 전에 알고리즘에 제공할 수 있는 최대 입력 특성 수를 결정합니다. 이 값을 0으로 설정하면 입력 특성에 대해 기능 선택을 사용할 수 없습니다.  
  
 기본값은 255입니다.  
  
 MAXIMUM_OUTPUT_ATTRIBUTES  
 기능 선택을 사용하기 전에 알고리즘에 제공할 수 있는 최대 출력 특성 수를 결정합니다. 이 값을 0으로 설정하면 출력 특성에 대해 기능 선택을 사용할 수 없습니다.  
  
 기본값은 255입니다.  
  
 MAXIMUM_STATES  
 알고리즘이 지원하는 특성당 최대 불연속 상태 수를 지정합니다. 특정 특성의 상태 수가 이 매개 변수에 지정한 수보다 크면 알고리즘은 해당 특성에 대해 가장 많이 사용되는 상태를 사용하고 나머지 상태를 누락된 것으로 처리합니다.  
  
 기본값은 100입니다.  
  
 SAMPLE_SIZE  
 모델의 학습에 사용되는 사례 수를 지정합니다. 이 알고리즘은 HOLDOUT_PERCENTAGE 매개 변수에 의해 지정된 홀드아웃 데이터에 포함되지 않은 총 사례 수의 비율이나 이 숫자 중 더 작은 값을 사용합니다.  
  
 즉, HOLDOUT_PERCENTAGE를 30으로 설정하면 알고리즘은 이 매개 변수 값이나 총 사례 수의 70%에 해당하는 값 중 더 작은 값을 사용합니다.  
  
 기본값은 10000입니다.  
  
### <a name="modeling-flags"></a>모델링 플래그  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 신경망 알고리즘에서 지원되는 모델링 플래그는 다음과 같습니다.  
  
 NOT  NULL  
 열에 null이 포함될 수 없음을 나타냅니다. 따라서 Analysis Services가 모델 학습 중 Null을 발견할 경우 오류가 발생합니다.  
  
 마이닝 구조 열에 적용됩니다.  
  
 MODEL_EXISTENCE_ONLY  
 모델에서 특성 값이 존재하는지 누락되었는지만 고려해야 함을 나타냅니다. 정확한 값은 고려하지 않습니다.  
  
 마이닝 모델 열에 적용됩니다.  
  
### <a name="distribution-flags"></a>분산 플래그  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 신경망 알고리즘에서 지원되는 분산 플래그는 다음과 같습니다. 이 플래그는 모델에 대해서만 힌트로 사용됩니다. 알고리즘에서는 다른 분산을 발견할 경우 힌트에 제공된 분산이 아니라 발견된 분산을 사용합니다.  
  
 보통  
 열 내의 값이 정규 가우스 분포를 나타내는 것처럼 처리되어야 함을 나타냅니다.  
  
 Uniform  
 열 내의 값이 일정하게 분산된 것처럼 처리되어야 함을 나타냅니다. 즉, 값의 확률은 거의 같으며 값의 총 수에 대한 함수여야 함을 나타냅니다.  
  
 Log Normal  
 열 내의 값이 *log normal* 곡선에 따라 분산된 것처럼 처리되어야 함을 나타냅니다. 즉, 값의 로그가 일정하게 분산되어야 함을 나타냅니다.  
  
## <a name="requirements"></a>요구 사항  
 신경망 모델은 하나 이상의 입력 열과 하나의 출력 열을 포함해야 합니다.  
  
### <a name="input-and-predictable-columns"></a>입력 열과 예측 가능한 열  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 신경망 알고리즘은 다음 표에 나열된 특정 입력 열과 예측 가능한 열을 지원합니다.  
  
|열|내용 유형|  
|------------|-------------------|  
|입력 특성|Continuous, Cyclical, Discrete, Discretized, Key, Table 및 Ordered|  
|예측 가능한 특성|Continuous, Cyclical, Discrete, Discretized 및 Ordered|  
  
> [!NOTE]  
>  Cyclical  및 Ordered  내용 유형이 지원되기는 하지만 알고리즘은 해당 유형을 불연속 값으로 처리하고 특수한 처리를 수행하지 않습니다.  
  
## <a name="see-also"></a>관련 항목:  
 [Microsoft 신경망 알고리즘](../../analysis-services/data-mining/microsoft-neural-network-algorithm.md)   
 [신경망 모델에 대한 마이닝 모델 콘텐츠&#40;Analysis Services - 데이터 마이닝&#41;](../../analysis-services/data-mining/mining-model-content-for-neural-network-models-analysis-services-data-mining.md)   
 [신경망 모델 쿼리 예제](../../analysis-services/data-mining/neural-network-model-query-examples.md)  
  
  
