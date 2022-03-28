![error](https://user-images.githubusercontent.com/76784643/160409536-9c9adc01-543b-477f-a109-5b6deefcf9dc.JPG)

추적되지 않은 working tree의 파일들이 git pull 명령이 수행되면 병합에 의해 덮어쓰이기 때문에 병합 전에 파일들을 이동시키거나 제거하라는 메시지가 출력됐다.

## 원인
1. 깃헙 저장소에 README.md만 존재하는 develop 브랜치를 로컬의 devleop 브랜치에서 당겨왔다.
2. 로컬의 devleop 브랜치에서 새로운 브랜치를 생성했다.
3. 새로운 브랜치에서 작업한 내용을 원격 저장소의 develop 브랜치에 푸시했다.
4. (그리고 로컬의 develop 브랜치로 이동해서 원격 저장소의 develop 브랜치를 당겨오려고 했다.)
5. 로컬의 develop 브랜치로 이동했다. 이 상태에서 IntelliJ로 화면을 전환했는데 IntelliJ에서도 develop 브랜치로 이동되면서 IntelliJ로 열린 프로젝트의 파일들이 자동으로 develop 브랜치에 생성됐다.
6. 원격 저장소의 develop 브랜치를 당겨오려고 했는데 병합에 의해 덮어쓰일 수 있다는 오류가 발생했다.

## 해결
추적되지 않은 working tree의 파일들을 staging area로 옮기고 staging area의 파일들을 임시 저장 공간으로 옮긴 후 병합을 수행한다.
임시 저장 공간으로 옮긴 파일들은 사용하지 않을 것이기 때문에 저장 공간 안에서 제거했다.  
`git add .`  
`git stash`  
`git pull`  
`git stash clear`
