# 🎵 Rhythm Game (리듬 게임)
> **추억의 리듬게임을 JavaScript로 직접 구현해보기!**

<p align="left">
  <img src="https://img.shields.io/badge/HTML-0F1689?style=flat-square&logo=HTML&logoColor=white" alt="HTML"> 
  <img src="https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=Javascript&logoColor=black" alt="JavaScript"> 
  <img src="https://img.shields.io/badge/GitHub-181717?style=flat-square&logo=GitHub&logoColor=white" alt="GitHub">
</p>

<br>


## 🚀 프로젝트 소개
JavaScript와 jQuery를 활용하여 간단한 **리듬게임(미니 게임)**을 구현했습니다.  
제한 시간 안에 화면에 표시된 키를 모두 입력하면 승리하는 게임입니다.

<br>

## ✅ 주요 기능
- 🎚 **난이도 선택**  
  - 상/중/하 난이도 → 제한 시간(10/15/20초), 시퀀스 길이(40/35/30) 자동 조정
- 🎲 **시퀀스 생성**  
  - 상/하/좌/우/스페이스(1~5 랜덤값) 이미지 배열 생성
- ⌨️ **입력 판정**  
  - keydown 이벤트와 정답 키 매칭 → 성공/실패 판정
- ❤️ **생명(라이프) 시스템**  
  - 오입력 3회 시 게임 오버
- ⏱ **타이머**  
  - 1초 단위 카운트다운, 클리어/실패 시 정지
- 🔊 **피드백 시스템**  
  - 정오답/클리어/실패별 효과음 및 UI 전환
- 🎵 **오토플레이 대응**  
  - 사용자 첫 입력 이벤트에서만 BGM 재생 (브라우저 정책 대응)

<br>

## 🔑 핵심 구현 포인트
- **반응형 그리드 레이아웃**  
  - `#game-area` → `grid-template-columns: repeat(6, minmax(10%, 1fr))`  
  - `gap: 2vw; width: 80vw; max-width: 700px` 로 퍼즐 타일처럼 배치

- **시퀀스/상태 관리**  
  - `keys[]` 배열에 이미지 DOM 저장  
  - `currentIndex`로 현재 정답 추적  
  - 난이도별 `keys.length`, `timeleft` 분기

- **입력 처리 & 판정**  
  - `e.preventDefault()` → 방향키 입력 시 화면 스크롤 방지  
  - `switch(e.keyCode)`로 키 매핑 (↑↓←→ + 스페이스)  
  - 정답 시 `visibility = hidden`, 모든 처리 시 클리어

- **게임 루프 종료 처리**  
  - `setInterval()` → 시간 종료 / 라이프 0 / 클리어 시 `clearInterval()`  
  - 게임오버/클리어 시 `$(document).off('keydown')` → 입력 해제  
  - `location.reload()`로 초기화

- **사운드 설계**  
  - 배경음악(BGM): `<audio id="bgm" loop>`  
  - 효과음: `new Audio().play()` (액션별 짧게 재생, 겹침 대응)  
  - 첫 사용자 입력 시 `{ once: true }` 옵션으로 BGM 시작

- **UX 디테일**  
  - 타이틀 페이드인: `$("#title").show(2000)`  
  - 성공/실패 시 전용 이미지 전체 출력  
  - 즉시 재시작 버튼 제공

<br>

## 🛠 트러블슈팅
- **BGM 미재생 (브라우저 오토플레이 정책)**  
  → 사용자 첫 클릭 이벤트에서 `bgm.play()` 트리거
- **방향키 입력 시 화면 스크롤 발생**  
  → `e.preventDefault()`로 기본 동작 제거


<br>

<h3 class="code-line" data-line-start=19 data-line-end=20 >✨화면 구성</h3>
<h5 class="code-line" data-line-start=20 data-line-end=21 >시작화면</h5>
<p class="has-line-data" data-line-start="21" data-line-end="22"><img src="https://github.com/user-attachments/assets/645105b6-318b-476b-b5b5-cbe2890d4d60" alt="시작화면"></p>
<h5 class="code-line" data-line-start=23 data-line-end=24 >게임설명</h5>
<p class="has-line-data" data-line-start="24" data-line-end="25"><img src="https://github.com/user-attachments/assets/bc153db5-8a81-4e76-9537-1e7fe77f4799" alt="게임설명"></p>
<h5 class="code-line" data-line-start=26 data-line-end=27 >난이도 선택</h5>
<p class="has-line-data" data-line-start="27" data-line-end="28"><img src="https://github.com/user-attachments/assets/0629c771-0a45-4d51-9ceb-4d82877c91a1" alt="Image"></p>
<h5 class="code-line" data-line-start=29 data-line-end=30 >게임 진행 화면</h5>
<p class="has-line-data" data-line-start="30" data-line-end="31"><img src="https://github.com/user-attachments/assets/9550ced8-e125-432f-8524-e45d99e40411" alt="게임진행화면면"></p>
<h5 class="code-line" data-line-start=32 data-line-end=33 >실패시</h5>
<p class="has-line-data" data-line-start="33" data-line-end="34"><img src="https://github.com/user-attachments/assets/18715882-4392-4e28-941a-cd5f6739f8dd" alt="실패"></p>
<h5 class="code-line" data-line-start=35 data-line-end=36 >성공시</h5>
<p class="has-line-data" data-line-start="36" data-line-end="37"><img src="https://github.com/user-attachments/assets/ff4d8bfc-ba97-4898-a698-0a4c801aa9d8" alt="Image"></p>
<h3 class="code-line" data-line-start=38 data-line-end=39 >☎️연락처</h3>
<p class="has-line-data" data-line-start="39" data-line-end="40">궁금한 점이 있으시면 <a href="mailto:jinayoon90@gmail.com">jinayoon90@gmail.com</a> 으로 연락주세요!</p>
