## 1. 업로드할 폴더의 상위 폴더로 이동
## 2. 깃을 사용할 수 있도록 폴더를 초기화
```
git init
```
## 3. 상태 변경이 필요한 파일이 있는지 확인
```
git status
```
## 4. add 명령어를 실행하여 tracked 파일로 변경
```
git add 폴더명
```
## 5. commit 명령어를 실행하여 폴더를 커밋
```
git commit -m "Commit Message"
```
## 6. 로컬 저장소를 원격 저장소와 연결
```
git remote add origin "원격 저장소 주소"
```
## 7. remote -v 명령어를 실행하여 로컬 저장소와 원격 저장소가 연결되었는지 확인
```
git remote -v
```
## 8. push 명령어를 실행하여 폴더를 업로드
```
git push origin master
```
