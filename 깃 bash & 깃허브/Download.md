## 1. 폴더 생성 후 이동
```
mkdir sample-code1
cd sample-code1
```
## 2. git 초기화
```
git init
```
## 3. git checkout 설정 변경
```
git config core.sparseCheckout true
```
## 4. 원하는 git 저장소 추가
```
git remote add -f origin https://github.com/android/architecture-components-samples.git
```
## 5. 원하는 특정 폴더 저장소 선택(window)
```
echo NavigationAdvancedSample/* > .git/info/sparse-checkout
```
## 6. 원하는 특정 폴더 저장소 선택(ubuntu)
```
echo "NavigationAdvancedSample/*" > .git/info/sparse-checkout
```
## 7. git 당기기(특정 브렌치 정보)
```
git pull origin main
```
