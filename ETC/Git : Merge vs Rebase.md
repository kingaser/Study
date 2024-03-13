### Merge
- Merge는 main과 sub 브랜치가 있을 때 main 브랜치에서 sub 브랜치를 Merge하면 main 브랜치의 헤드에 새롭게 커밋 이력이 생성됩니다.
- Merge는 실행한 브랜치로 병합을 실행하고 새로운 커밋 이력을 생성합니다.
![image](https://github.com/kingaser/Study/assets/104209781/7ee45e0d-4f81-435a-a694-a8955c4f3b73)
![image](https://github.com/kingaser/Study/assets/104209781/9c5afd84-ddb9-4bbd-b96d-839c4d4a3081)

### Rebase
- Rebase는 main과 sub 브랜치가 있을 때 sub 브랜치를 Rebase하면 sub 브랜치를 베이스로 커밋 이력이 정렬됩니다.
- 반대로 하게 되면 main 브랜치를 기준으로 커밋 이력이 정렬됩니다.
- Rebase는 어떤 특정 브랜치를 베이스로 커밋 이력을 재정렬 하겠다는 명령어입니다.
- 커밋 이력이 재정렬됙 때문에 이전과는 다른 새로운 해쉬 ID가 부여됩니다.
- 리베이스는 커밋 이력을 깔끔하게 관리하는 경우에 사용할 수 있습니다.
![image](https://github.com/kingaser/Study/assets/104209781/1aa03307-4e6d-45de-8c44-35b774be1536)
![image](https://github.com/kingaser/Study/assets/104209781/0a63b6d6-49ab-426c-8dec-79d846784dcf)

### cherry-pick
- 다른 브랜치에서 특정 커밋을 현재 작업 중인 브랜치로 가져오는 명령어입니다.
- 특정 커밋의 변경 내용을 선택적으로 현재 브랜치에 적용하고자 할 때 사용되고, 주로 특정 기능이나 수정이 다른 브랜치에서 이미 이루어진 경우,
그 변경 내용을 현재 브랜치에 적용하고자 할 때 활용됩니다.
