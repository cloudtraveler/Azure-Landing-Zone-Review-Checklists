# 검토 체크리스트 스크립트 (미리 보기)


이 폴더에는 검토 프로세스를 지원하는 스크립트를 찾을 수 있습니다.


## Azure Resource Graph 검토


스크립트 [checklist_graph.sh](./checklist_graph.sh)는 [../checklists](../checklists) 폴더 내 체크리스트의 항목과 연관된 그래프 쿼리를 자동으로 수행합니다. 여러 작동 모드를 지원하며, 다음 섹션에서는 사용 예시를 보여줍니다.


### 설치


> :warning: ***`checklist_graph.sh` 스크립트는 반드시 Bash 환경 셸에서 실행해야 합니다. Azure Cloud Shell을 사용하는 경우 올바른 환경을 선택했는지 확인하십시오.***


> 참고: 사설 AKS 클러스터(API 서버가 사설인 경우) 컨텍스트에서는 Azure Cloud Shell을 사용하여 `checklist_graph.sh` 스크립트를 실행하는 데 제한이 없습니다.
> checklist_graph 스크립트 실행에 사용되는 ID(Azure Cloud Shell이 사용하는 ID)가 [쿼리하려는 리소스(이 경우 AKS 클러스터)에 대한 최소한 읽기 권한을 포함한 Azure RBAC에서 적절한 권한을 보유해야 합니다](https://learn.microsoft.com/azure/governance/resource-graph/overview#permissions-in-azure-resource-graph).
> Azure 개체 또는 개체 그룹에 대한 최소한의 읽기 권한이 없으면 결과가 반환되지 않습니다.
> 이 스크립트는 Azure Resource Graph API를 쿼리할 뿐, 클러스터의 API 서버와 통신하지 않습니다.

Azure CLI를 지원하는 모든 환경(예: [Azure Cloud Shell](https://shell.azure.com))에서 스크립트를 다운로드할 수 있습니다. 스크립트를 다운로드하고 실행 준비를 위해 다음 명령을 실행하세요:

```Shell
wget –quiet –output-document ./checklist_graph.sh https://raw.githubusercontent.com/Azure/review-checklists/main/scripts/checklist_graph.sh
chmod +xr ./checklist_graph.sh
```


### 기본 사용법


이 스크립트를 실행하면 문서화된 Azure Resource Graph 쿼리와 함께 모든 체크리스트 항목의 JSON 형식 출력을 생성할 수 있습니다. 예를 들어, AKS 체크리스트에 대한 Azure Resource Graph 쿼리를 실행하려면:


```Shell
./checklist_graph.sh --technology=aks --format=json > ./graph_results.json
```


위 명령어는 JSON 파일 `./graph_results.json`을 생성합니다. 이제 Excel 스프레드시트로 이동하세요. 해당 체크리스트(이 예시에서는 AKS)를 이미 불러왔는지 확인한 후, 고급 명령인 "그래프 결과 가져오기"를 사용하여 이 파일을 스프레드시트로 가져옵니다:


![고급 버튼](../pictures/advanced_buttons.png)


스프레드시트의 "Comments" 열에는 Azure Graph 쿼리 결과가 채워지며, 권장 사항을 준수하거나 미준수하는 리소스 ID가 표시됩니다. 다음 그림과 같습니다(이 경우 단일 AKS 클러스터가 있는 구독에 대한 Azure Resource Graph 검사 결과를 가져온 후):


![고급 ](../pictures/graph_import_result.png)


다음 섹션에서는 스크립트의 고급 사용법을 보여줍니다.


### 사용 가능한 체크리스트 목록 표시


스크립트를 실행하여 사용 가능한 체크리스트를 확인할 수 있습니다. 모든 체크리스트에 Azure Resource Graph 쿼리가 포함되는 것은 아닙니다:


```
./checklist_graph.sh --list-technologies
```


### 체크리스트 내 기존 카테고리 목록 표시


스크립트를 실행하여 사람이 읽기 쉬운 출력을 생성할 수도 있습니다. 예를 들어, 단일 카테고리로 범위를 제한한 분석을 실행하려면 다음 명령을 실행하세요. 명령:


```
./checklist_graph.sh --techonology=aks --list-categories
```


출력:


```
0: - ID 및 액세스 관리
1: - 네트워크 토폴로지 및 연결성
2: - 비즈니스 연속성 및 재해 복구
3: - 거버넌스 및 보안
4: - 비용 거버넌스
5: - 운영
6: - 애플리케이션 배포
```


### 콘솔 출력으로 모든 범주 검토 수행


이 예시는 단일 구독 내 모든 범주에 대한 분석을 실행하는 방법을 보여줍니다. 출력 결과는 Excel 스프레드시트에 (카테고리별로) 복사/붙여넣기할 수 있습니다. 명령어:


```
./checklist_graph.sh --technology=aks --format=text
```


출력 결과 (간결함을 위해 일부 생략). 리소스는 `<리소스 그룹>/<리소스 이름>` 구문으로 형식화됨:


```
체크리스트 항목: Azure 지역에서 지원되는 경우 가용 영역 사용:
/subscriptions/e7da9914-9b05-4891-893c-546cb7b0422e/resourceGroups/akstest/providers/Microsoft.ContainerService/managedClusters/checklist: 미준수
체크리스트 항목: SLA 지원 AKS 오퍼링 사용:
/subscriptions/e7da9914-9b05-4891-893c-546cb7b0422e/resourceGroups/akstest/providers/Microsoft.ContainerService/managedClusters/checklist: non-compliant
체크리스트 항목: 서비스 주체 대신 관리형 ID 사용:
/subscriptions/e7da9914-9b05-4891-893c-546cb7b0422e/resourceGroups/akstest/providers/Microsoft.ContainerService/managedClusters/checklist: 준수됨...

```


### 관리 그룹 범위로 그래프 쿼리 실행


모든 이전 명령어는 `--management-group` 플래그를 사용하여 단일 구독 대신 관리 그룹 범위로 지정할 수 있습니다. 관리 그룹 이름을 지정하세요(관리 그룹의 **표시 이름**이 아닌 **실제 이름**을 반드시 지정해야 함). 예시:


```
./checklist_graph.sh --technology=aks --category=1 --management-group=mymgmtgroup
```


사용된 플래그에 따라 출력은 이전 예제와 동일합니다.


### 문제 해결


`checklist_graph.sh` 스크립트 실행 시 발생하는 문제를 해결하려면 다음 명령을 실행하세요:


```
./checklist_graph.sh --technology=aks --format=json --debug
```


Azure Cloud Shell 콘솔에 기록되는 디버그 메시지를 확인하세요.
