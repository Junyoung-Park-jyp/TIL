# *SSAFY Start Camp* 3일차

<br>
<br>

---

<br>
<br>

## 1. 원격 저장소

* 코드와 버전 관리 이력을 온라인 상의 특정 위치에 저장하여 <br>  여러 개발자가 협업하고 코드를 공유할 수 있는 저장 공간

* Github, Gitlab 등

<br>
<br>

---

<br>
<br>

## git remote add origin \<url>

* 로컬 저장소에 원격 저장소의 url 추가

* origin <- 별칭(암묵적 약속으로 origin 애용)

<br>
<br>

---

<br>
<br>

## push & pull

* push할때는 commit이 필수!
  * commit이 완료된 내용을 올리는 것이기 때문

* pull은 변경사항만을 받는다

* git clone
  * 원격 저장소 전체를 복제(git init은 되어 있다)

<br>
<br>

---

<br>
<br>

## gitignore

* Git에서 특정 파일, 디렉토리를 관리하지 않게 하는 텍스트 파일
* 이미 commit으로 관리 대상이 된다면, 이후에 gitignore에 등록해도 관리가 된다

## git file의 status

* untracked: 신규 파일(track X)
* modified: 변경된 파일
  * red=working directory, greem=staging area
