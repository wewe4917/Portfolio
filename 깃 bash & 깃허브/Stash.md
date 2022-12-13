## 1) 파일 내용 출력
```
$ cat [파일명.확장자명]
```
## 2) 디렉토리를 만드는 동시에 지역저장소 생성
```
$ cd init [디렉토리명]
```
## 3) 현재 커밋을 다른 브랜치에 있는 [커밋메시지] 커밋으로 되돌림
```
$ git reset [커밋메시지] [커밋해시]
```
## 4) 병합이 끝난 [브랜치명]을 삭제
```
$ git branch [브랜치명] -d
```
## 5) 작업 트리의 수정 내용 stash에 따로 보관하기
```
$ git stash
$ git stash save
```
## 6) 보관한 내용을 목록을 출력
```
$ git stash list
```
## 7) 보관한 내용을 적용
```
$ git stash apply
$ git stash apply stash@{1}
```
## 8) 보관한 내용 중 가장 최근 항목을 삭제
```
$ git stash drop
$ git stash drop stash@{1}
```
## 9) stash를 apply하고 제거(drop) 하기
```
$ git stash pop
```
