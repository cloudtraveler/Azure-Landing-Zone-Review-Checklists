[![GitHub Super-Linter](https://github.com/Azure/review-checklists/workflows/Lint%20Code%20Base/badge.svg)](https://github.com/marketplace/actions/super-linter)

# Azure Review Checklists


많은 조직에서 공통적으로 요구하는 사항 중 하나는 퍼블릭 클라우드를 시작으로 설계가 모범 사례를 따르고 있는지 재검토하는 것입니다. 이 작업의 범위는 일반적인 Azure 랜딩 존부터 워크로드별 배포에 이르기까지 다양할 수 있습니다.

Azure 설계 검토(또는 그 어떤 검토 작업이든)를 수행할 때 Microsoft 직원과 파트너사는 종종 발견 사항을 문서화하고 설계 개선 사항 및 권장 사항을 추적하기 위한 수단으로 Excel 스프레드시트를 활용합니다. Excel 스프레드시트의 문제점은 버전 관리가 쉽지 않다는 점입니다. 또한 분기, 이슈, 풀 리퀘스트, 검토 등 팀 협업은 최선의 경우에도 어렵고 대부분의 경우 불가능합니다.

![](./pictures/overview.png)

이 체크리스트를 사용하는 방법은 세 가지입니다.

1) Via [Excel](./spreadsheet/README.md)
2) [Azure Resource Graph Queries](./scripts/README.md)

## Reporting errors and contributing

체크리스트에서 오류나 누락된 정보를 발견하신 경우, [기여 가이드라인](./CONTRIBUTING.md)을 따라 
[이슈 생성](https://github.com/Azure/review-checklists/issues/new/choose)하거나 PR을 생성해 주시기 바랍니다.
## Checklists

지원되는 체크리스트 및 해당 책임자 요약:

| Checklist | Status | CodeOwners |
| --- | --- | --- |
| Azure Landing Zone  | GA | FTA-ALZ-vTeam, ALZ-checklist-contributors  |
| AI Landing Zone  | Preview | [@mbilalamjad](https://github.com/mbilalamjad) [@prwani](https://github.com/prwani)  |
| WAF | GA | Dynamically generated |
| AKS | GA | [@msftnadavbh](https://github.com/msftnadavbh) [@seenu433](https://github.com/seenu433) [@erjosito](https://github.com/erjosito) |
| ARO | Preview | [@msftnadavbh](https://github.com/msftnadavbh) [@naioja](https://github.com/naioja) [@erjosito](https://github.com/erjosito) |
| AVD | GA | [@igorpag](https://github.com/igorpag) [@mikewarr](https://github.com/mikewarr) [@bagwyth](https://github.com/bagwyth) |
| Cost | GA | [@brmoreir](https://github.com/brmoreir) [@pea-ms](https://github.com/pea-ms) |
| Multitenancy | GA | [@arsenvlad](https://github.com/arsenvlad) [@cherchyk](https://github.com/cherchyk) |
| Application Delivery Networking | GA | [@erjosito](https://github.com/erjosito) [@andredewes](https://github.com/andredewes) |
| AVS design | Preview | [@fskelly](https://github.com/fskelly) [@mgodfrey50](https://github.com/mgodfrey50) [@robinher](https://github.com/robinher) |
| AVS implementation | Preview | [@fskelly](https://github.com/fskelly) [@mgodfrey50](https://github.com/mgodfrey50) [@robinher](https://github.com/robinher) |
| SAP | GA | [@NaokiIgarashi](https://github.com/NaokiIgarashi) [@AlastairMorrison](https://github.com/AlastairMorrison) [@mottach](https://github.com/mottach) |
| API Management | Preview | [@andredewes](https://github.com/andredewes) [@seenu433](https://github.com/seenu433) |
| Stack HCI | Preview | [@mbrat2005](https://github.com/mbrat2005) [@steveswalwell](https://github.com/steveswalwell) [@igomaa](https://github.com/igomaa) |
| Spring Apps | Preview | [@bappadityams](https://github.com/) [@vermegi](https://github.com/vermegi) [@fmustaf](https://github.com/fmustaf) |
| Azure DevOps | Preview | [@roshair](https://github.com/roshair) |
| SQL Migration | Preview | [@karthikyella](https://github.com/karthikyella) [@dbabulldog-repo](https://github.com/dbabulldog-repo) |
| Security | Deprecated | [@mgodfrey50](https://github.com/mgodfrey50) [@rudneir2](https://github.com/rudneir2) |

## 면책 조항

- 본 내용은 공식 Microsoft 문서 또는 소프트웨어가 아닙니다.
- 본 내용은 아키텍처 또는 설계에 대한 승인 또는 보증을 의미하지 않습니다.
- 본 코드 샘플은 "있는 그대로" 제공되며, 상품성 및/또는 특정 목적에의 적합성에 대한 묵시적 보증을 포함하되 이에 국한되지 않는 어떠한 명시적 또는 묵시적 보증도 제공되지 않습니다.
- 본 샘플은 어떠한 Microsoft 표준 지원 프로그램이나 서비스에서도 지원되지 않습니다.
- Microsoft는 상품성 또는 특정 목적에의 적합성에 대한 묵시적 보증을 포함하되 이에 국한되지 않는 모든 묵시적 보증을 추가로 부인합니다.
- 샘플 및 문서의 사용 또는 성능으로 인해 발생하는 모든 위험은 귀하에게 있습니다.
- 어떠한 경우에도 Microsoft, 해당 스크립트의 작성자 또는 제작, 생산, 제공에 관여한 기타 누구도 샘플 또는 문서의 사용 또는 사용 불능으로 인해 발생하는 어떠한 손해(사업 이익 손실, 사업 중단, 사업 정보 손실 또는 기타 금전적 손해를 포함하되 이에 국한되지 않음)에 대해 책임을 지지 않습니다. Microsoft가 그러한 손해의 가능성에 대해 통지받은 경우에도 마찬가지입니다.
용어집


