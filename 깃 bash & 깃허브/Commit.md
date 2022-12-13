## 1) [파일명.확장자명]을 스테이지에 올림
```
$ git add [파일명.확장자명]
```
## 2) 커밋 메시지 [메시지명]을 붙여 커밋
```
$ git commit -m "[메시지명]"
```
## 3) 메시지 [메시지명]을 붙여서 스테이징과 커밋을 동시에 진행
```
$ git commit -a -m "[메시지명]"
```
## 4) 커밋 내역 확인
```
$ git log
$ git log --pretty=oneline   # 한줄로 표기하기
```
* 특정 커밋 내역 확인
```
$ git show [커밋 id]
```
## 5) 최근 버전과 작업 폴더의 수정 파일 사이의 차이를 출력
```
$ git diff
$ git diff [이전커밋 id] [이후커밋 id]
```
## 6) 지정한 커밋 해시로 이동
```
$ git checkout [커밋 해시]
```
## 7) 가장 최근 커밋을 취소
```
$ git reset HEAD^ # 현재 HEAD의 이전 커밋으로 되돌리기
$ git reset HEAD~n # 현재로 부터 n 번째 이전 커밋으로 되돌리기
```
## 8) 지정한 커밋 해시로 이동하고 커밋을 취소
```
$ git reset [커밋 해시]
```
reset의 3가지 옵션
```
$ git reset --soft [커밋ID]  # head 만 바뀜
$ git reset --mixed [커밋ID] # staging 도 그 때로 바뀜
$ git reset --hard [커밋ID] # working디렉토리/staging 모두 그 때로 바꿈 
```
## 9) 지정한 커밋 해시의 변경 이력을 취소
```
$ git revert [커밋 해시]
```
## 10) 커밋 수정하는 법
```
파일 수정 한 뒤
$ git add .
$ git commit --amend  : 최신 커밋 수정
```
