## 1) 새로운 브랜치 [브랜치명]을 생성
```
$ git branch [브랜치명]
```
* 브랜치 조회하기
```
$ git branch
```
## 2) [브랜치명]으로 체크아웃(이동)
```
$ git checkout [브랜치명]
$ git checkout -b [브랜치명]  # 브랜치만들고 바로 이동
```
* 브랜치 삭제
```
$ git branch -d 브랜치명
```
## 3) 커밋 로그에서 한 줄에 한 커밋씩 출력
```
$ git log --oneline
```
## 4) 수정한 전체 파일을 스페이지에 올린다.
```
$ git add .
```
## 5) 커밋 로그에 각 브랜치의 커밋을 그래프로 표시
```
$ git log --branches --graph
```
## 6) [브랜치명]을 master 브랜치와 병합 //
```
$ git merge [브랜치명]
$ git merge [브랜치명] --edit // 병합 후 바로 vi 편집기가 나오면서 커밋 메시지 수정 가능
$ git merge [브랜치명] --no-edit // 커밋 메시지 수정없이 바로 병합
```
## 7) merge 취소하기
```
$ git merge --abort
```
