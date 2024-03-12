## Git, GitHub, GitLab Flow
### Git Flow
- 가장 최초로 제안된 Workflow 방식이며, 대규모 프로젝트 관리에 적합한 방식으로 평가받습니다.
- 기본 브랜치는 5가지 입니다. feature > develop > release > hotfix > master
![image](https://github.com/kingaser/Study/assets/104209781/6ac120cb-9ef2-4d13-85e5-ca06413b0bc8)

  - Master(Main) : 릴리즈 시 사용하는 최종 단계 메인 브랜치입니다. Tag를 통해 버전 관리를 합니다.
  - Develop : 다음 릴리즈 버전 개발을 진행하는 브랜치입니다. 추가 기능 구현이 필요해지면, 해당 브랜치에서 다시 브랜치(Feature)를 내어 개발을 진행하고, 완료된 기능은 다시 Develop 브랜치로 Merge합니다.
  - Feature : Develop 브랜치에서 기능 구현을 할 때 만드는 브랜치입니다. 한 기능 단위마다 Feature 브랜치를 생성하는게 원칙입니다.
  - Release : Develop에서 파생된 브랜치입니다. Master 브랜치로 현재 코드가 Merge 될 수 있는지 테스트하고, 이 과정에서 발생한 버그를 고치는 공간입니다. 확인 결과 이상이 없다면, 해당 브랜치는 Master와 Merge 합니다.
  - Hotfix : Master 브랜치의 버그를 수정하는 브랜치입니다. 검수를 해도 릴리즈된 Master 브랜치에서 버그가 발견되는 경우가 존재하빈다. 이 때 Hotfix 브랜치를 내어 버그 수정을 진행합니다.
디버그가 완료되면 Master, Develop 브랜치에 Merge 해주고 브랜치를 닫습니다.

- git-flow에서 가장 중심이 되는 브랜치는 Master와 develop입니다.(무조건 필요합니다)
이름을 변경할 수는 있지만, 통상적으로 사용하는 이름이므로 그대로 사용하는게 좋습니다.
- 진행 과정 중에 Merge된 feature, release, hotfix 브랜치는 닫아서 삭제하도록 합니다.
- 이처럼 계획적인 릴리즈를 가지고 스케쥴이 짜여진 대규모 프로젝트에는 git-flow가 적합합니다.
하지만 대부분 일반적인 프로젝트에서는 불필요한 절차들이 많아 생산성을 떨어뜨린다는 의견도 많은 방식입니다.

### GitHub Flow
- git-flow를 개선하기 위해 나온 하나의 방식입니다.
- 흐름이 단순한 만큼 역할도 단순합니다. git flow의 hotfix나 feature 브랜치를 구분하지 안혹, pull request를 권장합니다.
![image](https://github.com/kingaser/Study/assets/104209781/942e136a-3147-4831-b98b-938419325dbd)
- Master 브랜치가 릴리즈에 있어 절대적인 역할을 합니다.
- Master 브랜치는 항상 최신으로 유지하며, Stable한 상태로 product에 배포되는 브랜치입니다.
따라서 Merge 전에 충분한 테스트 과정을 거쳐야 합니다. (브랜치를 push하고 Jenkins로 테스트)
- 새로운 브랜치는 항상 Master 브랜치에서 만들며, 새로운 기능 추가나 버그 해결을 위한 브랜치는 해당 역할에 대한 이름을 명확하게 지어주고,
커밋 메시지 또한 알기 쉽도록 작성해야 합니다.
- 그리고 Merge 전에는 pull request를 통해 공유하여 코드 리뷰를 진행합니다. 이를 통해 피드백을 받고, Merge 준비가 완료되면 Master 브랜치로 요청하게 됩니다.
- 이 Merge는 바로 product에 반영되므로 충분한 노의가 필요하며 CI도 필수적입니다.
- Merge가 완료되면, push를 진행하고 자동으로 배포가 완료됩니다.(GitHub-flow의 핵심적인 부분)

### CI(Continous Integration)
- 형상관리 항목에 대한 선정과 형상관리 구성 방식을 결정합니다.
- 빌드/배포 자동화 방식입니다.
- 단위테스트/통합테스트 방식입니다.
- 이 세가지를 모두 고려한 자동화된 프로세스를 구성하는 것입니다.

### GitLab Flow
- github flow의 간단한 배포 이슈를 보완하기 위해 관련 내용을 추가로 덧붙인 flow 방식입니다.
![image](https://github.com/kingaser/Study/assets/104209781/9e1bead3-8efb-41d3-b8dd-cc620c36e07c)

- Production 브랜치가 존재하여 커밋 내용을 일방적으로 Deploy하는 형태를 갖추고 있습니다.
- Master 브랜치와 Production 브랜치 사이에 Pre-Production 브랜치를 두어 개발 내용을 바로 반영하지 않고, 시간을 두고 반영합니다.
이를 통한 이점은, Production 브랜치에서 릴리즈된 코드가 항상 프로젝트의 최신 버전 상태를 유지할 필요가 없습니다.
- 즉, GitHub-Flow의 단점인 안정성과 배포 시기 조절에 대한 부분을 production이라는 추가 브랜치를 두어 보강하는 전략이라고 볼 수 있습니다.

---
3가지 방법 중 무엇이 가장 좋은 방식이라고 선택할 수 없습니다. 프로젝트, 개발자, 릴리즈 계획 등 상황에 따라 적합한 방법을 택해야 합니다.
배달의 민족인 '우아한 형제들'이 github-flow에서 git-flow로 워크플로우를 변경한 것 처럼 브랜칭과 배포에 관한 전략 상황에 따라 변경이 가능한 부분입니다.
따라서 각자 팀의 상황에 맞게 적절한 워크플로우를 선택하여 생산성을 높이는 것이 중요할 것입니다.
