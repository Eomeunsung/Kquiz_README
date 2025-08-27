# 키득퀴즈(Kquiz)

개인 프로젝트로 개발한 **React + Spring Boot** 기반 블로그 웹 애플리케이션 입니다.
실시간으로 여러 사용자가 함께 참여하여 퀴즈를 풀 수 있도록한 웹 기반 퀴즈 게임 플랫폼 입니다.
"Kahoot"을 벤치마킹 하여 개발 하였습니다.

## Repository
- **Front**: https://github.com/Eomeunsung/Kquiz-Front.git
- **BackEnd**: https://github.com/Eomeunsung/Kquiz-Back.git

## 주요 기능 
- **실시간 퀴즈 진행(WebSocket 기반)**
- **퀴즈 생성 및 수정 기능 (이미지 포함)**
- **실시간 참가자 입장 및 퇴장 관리**
- **게임 종료 후 순위 확인**
- **사용자 인증 / 인가 (JWT 기반)** 로그인 / 회원가입 / 권한 관리
- **REST API 설계 및 구현**

## 기술 스택
- **Frontend**: React, React Router, Axios
- **Backend**: Spring Boot, Spring Data JPA, Spring Security, JWT, WebSocket(STOMP 기반), MariaDB, Redis
- **Version Control**: Git, GitHub

## 프로젝트 후기
개인 역량을 키우고 부족했던 부분을 보완하기 위해 졸업작품을 혼자서 다시 프로젝트를 설계하고 개발하게 되었습니다. 혼자서 모든 과정을 책임지며 시행착오도 많았지만, 덕분에 많은 것을 배우고 성장할 수 있었던 것 같습니다.
다만 서술형 문제 구현은 아직 기술과 지식이 부족한 탓에 앞으로 더 개선해 나가야 할 것 같았습니다. 또한 CSS 및 디자인 역량이 아직 많이 부족해 AI를 활용하여 보완하였습니다.

## 구현시 어려웠던 부분
- **문제**: 웹 소켓을 활용한 실시간 퀴즈 플레이 구현 초기에는 각 클라이언트(참여자 및 호스트)에게 각 개별적인 질문 데이터를 전송하여, 퀴즈 풀이 하도록 하였습니다. 하지만 네트워크 지연시 타이머 불일치 하거나 문제도 다르거나 동기화 및 오류가 발생하였습니다.
  
- **해결**: 호스트 기준으로 데이터 전송 방식으로 변경하였습니다. 호스트가 웹소켓 질문 데이터를 요청하면 서버에서 조회 후 구독중인 모든 클라이언트에게 전송하도록 하였고, 타이머도 호스트 기준으로 서버에서 전송하여 모든 클라이언트가 동기화 되도록 하였습니다.
  
- **결과**: 네트워크 상태가 불안정해도 모든 클라이언트가 동일한 질문과 남은 시간을 확인하며 퀴즈 진행이 가능해졌습니다.

## ERD다이어그램
<img width="1161" height="543" alt="스크린샷 2025-08-02 15 30 32" src="https://github.com/user-attachments/assets/377df189-5e16-4c1b-a13e-8c813b4c49d7" />

## 흐름도
<table>
    <tr>
    <td>
      <img width="562" height="362" alt="스크린샷 2025-08-26 18 24 40" src="https://github.com/user-attachments/assets/e7978416-ba54-43b7-9b63-0dd9f1ed3bc3" />
    </td>
    <td>
       <img width="697" height="452" alt="스크린샷 2025-08-26 18 59 24" src="https://github.com/user-attachments/assets/8632da2a-9208-457f-8a1c-0a1afc1a19c9" />
    </td>
  </tr>
  <tr>
    <td align="center">로그인</td>
    <td align="center">회원가입</td>
  </tr>
  
  <tr>
    <td><img width="448" height="663" alt="quiz create" src="https://github.com/user-attachments/assets/8c7419fa-5dbd-47d0-ab3d-8bd0cf377674" /></td>
    <td><img width="335" height="585" alt="스크린샷 2025-07-23 13 29 40" src="https://github.com/user-attachments/assets/c4b038e0-1cfb-4676-a365-07e188ed3832" /></td>
  </tr>
  <tr>
    <td align="center">Quiz 생성</td>
    <td align="center">Quiz 수정(아직 반영 안함)</td>
  </tr>

  <tr>
    <td>
      <img width="392" height="629" alt="스크린샷 2025-07-23 13 25 31" src="https://github.com/user-attachments/assets/67dfd1ad-45aa-4f4a-b3d0-50c81f991320" />
      </td>
    <td>
      <img width="671" height="601" alt="스크린샷 2025-08-26 14 32 09" src="https://github.com/user-attachments/assets/e223e4ba-5bf0-4340-9094-82a56aec8cb7" />
    </td>
  </tr>
  <tr>
    <td align="center">Quiz 삭제</td>
    <td align="center">게임 생성</td>
  </tr>

  
  <tr>
    <td>
      <img width="403" height="554" alt="스크린샷 2025-08-26 17 20 11" src="https://github.com/user-attachments/assets/41b4b475-c91f-4e5b-ba09-b81d6cc1c77d" />
    </td>
    <td>
      <img width="390" height="631" alt="스크린샷 2025-08-26 17 55 13" src="https://github.com/user-attachments/assets/7fe9372f-e1e1-45eb-a838-bed7ee376293" />
    </td>
  </tr>
  <tr>
    <td align="center">게임 참여</td>
    <td align="center">게임 플레이</td>
  </tr>

</table>

## 프로젝트 결과물
<img width="1404" height="807" alt="main" src="https://github.com/user-attachments/assets/4bbca513-707c-49dc-adac-1ffd46ecd0b4" />

- **메인화면**
---
  
<img width="1404" height="807" alt="signUp" src="https://github.com/user-attachments/assets/c66a5589-c96d-4a51-a7c4-89f37e2c3f6b" />

- **회원가입 화면**
---

<img width="1404" height="807" alt="signIn" src="https://github.com/user-attachments/assets/90a24e79-355f-4b8b-b9c3-70c92f3467bb" />

- **로그인 화면**
---

<img width="1404" height="807" alt="quiz create" src="https://github.com/user-attachments/assets/e8f849de-144a-4f84-9b3d-f261c5834d6b" />

- **퀴즈 생성 화면**
---

<img width="1404" height="807" alt="quiz create2" src="https://github.com/user-attachments/assets/b3b78e4f-b32f-4cd1-a79b-80c166396a5b" />

- **퀴즈 제작 화면(AI 힌트 사용)**
---

<img width="1404" height="807" alt="quiz create3" src="https://github.com/user-attachments/assets/36d90d86-43f2-4d5a-9572-e26b1f15f2d5" />


- **퀴즈 제작 화면2**
---

<img width="1404" height="807" alt="quiz create main" src="https://github.com/user-attachments/assets/5544d4f4-127c-43f2-96cc-a87535ca1a94" />

- **개인 채팅 화면**
---

<img width="1404" height="807" alt="game create" src="https://github.com/user-attachments/assets/3aba3557-e23c-41bd-b184-7799363c2abf" />

- **게임 생성 화면**
---

<img width="1404" height="807" alt="lobby" src="https://github.com/user-attachments/assets/491a9122-2f0a-494b-b128-0ff42ac689cb" />

- **호스트 로비 화면**
---

<img width="1404" height="807" alt="lobby2" src="https://github.com/user-attachments/assets/491a9122-2f0a-494b-b128-0ff42ac689cb" />

- **참여자 게임 참여 화면**
---

<img width="1404" height="807" alt="lobby3" src="https://github.com/user-attachments/assets/09ac8ff7-4513-48fa-b98d-8e7362203774" />

- **참여자/호스트 로비 화면**
---

<img width="1095" height="506" alt="스크린샷 2025-08-27 11 45 31" src="https://github.com/user-attachments/assets/f1267ccb-fa7b-49f9-a835-59a564cdb525" />

- **강퇴 기능**
---

<p align="center">
  <img width="1340" height="798" alt="스크린샷 2025-08-27 12 08 49" src="https://github.com/user-attachments/assets/a6f2f88d-1f3d-4191-87dc-c890b1e12e20"  width="45%" />
  <img width="1313" height="809" alt="스크린샷 2025-08-27 12 08 54" src="https://github.com/user-attachments/assets/9f7e45d6-5a0c-4b47-aadb-645e00bbd9ff" width="45%"/>
</p>

- **문제 풀이**
---

<img width="1432" height="583" alt="스크린샷 2025-08-27 12 09 21" src="https://github.com/user-attachments/assets/efbccfec-166a-467b-a54f-f9b00088b598" />

- **게임 종료 후 랭킹 반환**
---



















