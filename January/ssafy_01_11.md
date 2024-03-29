# 마크다운 이해해보기

<br>
<br>

---
<br>
<br>

# 제목
## 조금 약한 제목
### 조금 더 약한 제목

- #을 붙여서 제목/소제목을 작성한다
- #은 최대 6개까지

<br>
<br>

---

<br>
<br>

## 리스트

- (\1. 2. 3.)을 붙여 순서가 있는 리스트
  1. 첫번째
  2. 두번째
- *, -, +(bullet point)를 이용해 순서가 없는 리스트
  * 탭키로 indent를 삽입하면 리스트 내부 리스트
- "---"로 구분선을 추가할 수 있다
- 혼합 사용도 물론 가능
  1. 순서 있는 리스트 안의
    - 순서 없는 리스트
  - 순서 없는 리스트 안의
    1. 순서 있는 리스트

<br>
<br>

---

<br>
<br>

## Codeblock

- 여러줄의 코드를 삽입할 때

```
# 기본적으로 코드를 작성할때는 백틱(`) 3개 + 사용언어를 넣는다
\n
print(a)
```

```python
@app.route("/")
def ssafy_11():
    return "싸피 11기 베스트 일레븐"
```

- 한줄의 코드일 때

  - 백틱(`)을 앞뒤로 하나씩 넣는다 `print(SSAFY)` 예시

<br>
<br>

---

<br>
<br>

## 링크(link) & 이미지(image)

* 특정 주소를 사용해 다른 페이지 이동하는 링크 혹은 이미지
* 링크는 [텍스트] (주소) 형식
  * [구글](https://google.co.kr)
* 이미지는 ![텍스트] (주소) 형식
* 웹주소로 넣기  ![고양이](https://mblogthumb-phinf.pstatic.net/20160512_297/gatoblancokr_1463028030970omGoS_JPEG/Siamese-cat-on-couch.jpg?type=w420)
* 로컬주소로 넣기 ![고양이](SiamCat.jpg)

<br>
<br>

---

<br>
<br>

## 텍스트 관련 문법

* (\*\*텍스트\*\*)로 **볼드체**
* (\*텍스트\*, \_텍스트\_)로 *이탤릭체*
* (\~텍스트\~)로 ~취소선~  
>(\>텍스트)로 인용문 작성 가능
>> (\>>텍스트)로 인용문 내의 인용문

<br>
<br>

---

<br>
<br>

## 구분선 긋기

* (\---) -를 3개 이상 긋기

<br>
<br>

---

<br>
<br>

## 테이블 작성

* (\|)를 이용해서 만든다
* 구분선 앞뒤로 : 이용해서 정렬

| 조 | 번호 | 이름 |
| :--- | ---: | ---:|
| 5 | 21 | 임광영 |
| 5 | 9 | 남윤희 |
| 5 | 7 | 김준호 |
| 5 | 12 | 박수진 |
| 5 | 13 | 박준영 |

<br>

| 떠든 사람 | 횟수 |
| :--- | ---: |
| 유태람 | 正 |
| 박준영 | 正正正 |

<br>
<br>

---

<br>
<br>

# CLI(Command Line Interface)

* **명령어**를 통해 사용자와 컴퓨터가 상호 작용하는 방식

<br>
<br>

---

<br>
<br>

## GUI vs CLI

* 왜 CLI를 쓸까?
  * GUI는 상대적으로 쉽지만, 단계가 많고 성능을 더 소모한다
  * 수 많은 서버와 개발 시스템이 CLI를 통해 조작 환경 제공

<br>
<br>

---

<br>
<br>

## CLI에서 .의 역할

* . = 현재 디렉토리

* .. = 상위 디렉토리

* ~ = 홈 디렉토리

<br>
<br>

---

<br>
<br>

## 기본적인 명령어

* touch 파일이름.확장자: 파일 만들기

* mkdir 폴더이름: 폴더 만들기

* ls: 현재 경로내의 파일 확인
  *  ls -A: 숨김 파일까지 모두 확인
* rm 파일이름: 파일 삭제하기
  * rm -f 파일이름: 강제로 파일 삭제하기(강력한 명령어)
  * rm -r 폴더이름: 디렉토리 삭제하기
  * rm -rf 폴더이름: 강제로 디렉토리 삭제하기(강력한 명령어)

* start 파일명: 파일 실행하기

* code 파일명: vscode로 파일 실행하기(vscode필요)
  
<br>
<br>

---

<br>
<br>

## CLI에서 가장 중요한 것

<br>

* 현재 경로를 확인하기!

<br>
<br>

---

<br>
<br>

## 절대 경로 & 상대 경로

<br>

1. 절대 경로
  * Root 디렉토리부터 목적 지점까지를 모두 작성
  * cd C:/Users/SSAFY/Codes/Startcamp

2. 상대 경로
  * 현재 작업 디렉토리 기준으로 계산한 상대적 위치
  * C:/Users/SSAFY에서 작업중일 때의 상대경로는 Codes/Startcamp

<br>
<br>

---

<br>
<br>

# GIT

<br>
<br>

## 분산 버전 관리 시스템

* 분산 구조의 장점
  * 중앙 서버에 의존하지 않고 다양한 작업 수행 가능
  * 개발자들 간의 작업 충돌 줄이고 개발 생산성 향상
* 중앙 서버의 장애나 손실에 대비한 백업, 복구 용이
* 인터넷에 연결되지 않은 환경에서도 작업 가능
  * 변경 이력과 코드를 로컬 저장소에 저장하고 이후 업로드

## GIT의 역할

* 코드의 버전(히스토리) 관리
* 이전 버전과 변경사항 비교

## GIT의 3가지 영역

* working directory: 현재 작업

* staging area: 선별장

* repository: 저장소

<br>
<br>

---

<br>
<br>

## Staging Area

* Working Directory에서 변경된 파일 중, 다음 버전에 포함시킬 파일들을 선택적으로 추가하거나 제외하는 중간 준비 영역

<br>
<br>

---

<br>
<br>

## Commit

* 변경된 파일들을 저장하는 행위, 마치 사진을 찍듯 기록하기에 snapshot이라고도 함

<br>
<br>

---

<br>
<br>

## GIT 명령어

* `git init`
  * git으로 이 저장소를 관리하겠다는 선언(시작)
  * git 로컬 저장소 내에 또다른 git로컬 저장소를 만들지 말 것
  * git 저장소 안에 git 저장소가 존재할 경우, 가장 바깥 쪽의 저장소가 안쪽의 변경사항을 추적 불가

* `git add`: 변경 사항을 staging area에 추가

* `git commit`: repository에 변경 사항을 저장
  * `git log`: commit 목록 확인
  * `git log --oneline`: 목록 한줄 확인

* `git clone`: 저장소 복제
* `git pull`: github repository를 local에 가져옴
* `git push`: local 변경점을 github repository로 보냄
* `git config --global -l`: 현재 config설정 조회
