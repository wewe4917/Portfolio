## 1) 원격 저장소에 연결
```
$ git remote add origin [github 레포지 주소]
$ git remote add origin [branch 이름]   #없으면 생성됨
```
## 2) 원격 저장소에 연결됐는지 확인
```
$ git remote -v
```
## 3) 지역 저장소의 커밋을 맨 처음 원격 저장소에 올리는 경우
```
$ git push -u origin master
```
## 4) 3번을 한 후에 지역 저장소의 커밋을 원격 저장소에 올리는 경우(업로드)
```
$ git push
$ git push origin master
```
## 5) 원격 저장소의 커밋을 지역 저장소로 가져옴
```
$ git pull
$ git pull origin master
```
## 6) SSH 키를 생성함
```
$ ssh-keygen
```
## 7) 원격 저장소 복제하기
* 첫번째 커밋이 아니라면 풀 먼저하기
```
$ git remote remove origin
```
* 원격 저장소를 [지역저장소명]에 복제하기
```
$ git clone [원격 저장소 주소]
```
## 8) 원격 저장소의 커밋을 가져오기만 하고 merge하지 않는다
* 가져온 branch 내용은 origin/[브랜치] 로 저장됨
```
$ git fetch
```
* 이후엔 diff 로 비교
```
$ git diff test origin/test # 브랜치 이름이 test일 경우 예시
```
## 9) 패치로 가져온 정보가 있는 브랜치\[FETCH\_HEAD\]로 이동
```
$ git checkout FETCH_HEAD
```
## 10) 패치로 가져온 정보가 있는 브랜치[FETCH_HEAD]를 master 브랜치에 병합한다
```
$ git merge FETCH_HEAD
```
## 11) [브랜치명]을 만드는 것과 동시에 체크아웃한다
```
$ git checkout -b [브랜치명]
```
## 12) 원격 저장소에 [브랜치명]의 브랜치의 커밋을 올린다
```
$ git push origin [브랜치명]
```
## 13) 원격저장소 삭제
```
$ git remote remove origin
```
