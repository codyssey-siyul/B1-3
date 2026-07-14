# B1-3 노코드 자동화 기초: 워크플로우 설계  
## [프로젝트1] 자동화 도구 비교 구현
 ### 1. 도구별 워크플로우 구성 화면
+ **Zapier**  
<img width="543" height="750" alt="Image" src="https://github.com/user-attachments/assets/4bd90941-c1a0-4a1c-ac73-1ca4c56beea2" />

  
+ **Make**
<img width="1261" height="612" alt="Image" src="https://github.com/user-attachments/assets/04c79b9b-fa6b-4a46-978d-1a0f30c4881e" />

******  

### 2. 실행 결과 화면  
+ **Zapier**
<img width="1852" height="898" alt="Image" src="https://github.com/user-attachments/assets/2d31af65-1ee3-4944-8993-f2bf4b95153d" />  
<img width="745" height="523" alt="Image" src="https://github.com/user-attachments/assets/ed91c158-9a55-4969-b0d0-527481a63c27" />  
<img width="1852" height="932" alt="Image" src="https://github.com/user-attachments/assets/6f1bf6c5-c46d-4464-a9f3-b8ba5f77abd9" />

+ **Make**
<img width="1852" height="935" alt="Image" src="https://github.com/user-attachments/assets/90ded0d7-3114-4e4d-b264-008eb946721e" />
<img width="862" height="582" alt="Image" src="https://github.com/user-attachments/assets/553ef6e4-237c-4525-bc5e-9fabb86e56f0" />
<img width="1854" height="929" alt="Image" src="https://github.com/user-attachments/assets/343fde13-fa46-411d-8d68-b702ccd1640b" />  

******  

### 3. Zapier vs Make 비교 분석 보고서  
+ **사용 도구**
  
| Zapier | Make |
|------|------|
| -Trigger: Gmail (New Email) | -Trigger: Gmail (New Email) |
| -Action1: Google Sheets (Create Spreadsheet Row) | -Action1: Google Sheets (Add a Row) |
| -Filter: Contains "회의" | -Filter: Contains "회의" |
| -Action2: Google Calendar (Create Detailed Event) | -Action2: Google Calendar (Create an event) |  

  
+ **구현 과정 요약**
  
  \- Zapier: 각 모듈별로 테스트가 가능해 단계별 확인이 용이, 직관적인 UI와 순서대로 구성된 UX 덕분에 빠르게 구현 가능  
  \- Make: 모듈 셋팅 완료 후에야 테스트 가능, UI는 깔끔하지만 UX 구조가 복잡해 초보자에게는 난이도가 있음, 오류 발생 시 위치를 바로 표시해줘 수정이 용이  

  
+ **비교 항목**
  
| 항목 | Zapier | Make |
|:---:|:---:|:---:|
| UI/UX | 리스트 기반 인터페이스.<br>단계별로 구성되어 직관적 | 시각적 노드 기반 인터페이스.<br>전체 흐름을 한 눈에 볼 수 있으나 초보자에게는 복잡하게 느껴질 수 있음 |
| 설정 난이도 | 직관적이고 학습 곡선이 낮음.<br>빠른 구현 가능 | 구조 이해가 필요하지만 익숙해지면 강력한 기능 제공 |
| 연동 서비스 범위 | 7,000+ 앱 지원<br>프리미엄 앱은 유료 플랜 필요 | 3,000+ 앱 지원<br>세부 커넥터 차이가 있으며 고급 기능은 학습 필요 |
| 무료 플랜 범위 | 월 100 Tasks | 월 1,000 Ops |
| 실행 로그 확인 방식 | 단계별 테스트 가능<br>오류 발생 시 `Task Failed` 형태로 표시됨<br>실패한 단계만 확인 가능하며 원인 파악은 로그를 열어봐야 함 | 전체 셋팅 후 테스트 가능<br>오류 발생 모듈이 시각적으로 표시됨<br>어디서 오류가 났는지 직관적으로 알 수 있음 |  

  
+ **장단점**

  \[Zapier]  
    
   \- 장점: 직관적 UI/UX, 단계별 테스트 가능, 다양한 앱 연동 지원  
   \- 단점: 무료 플랜 작업 수 제한, 다단계 불가, 일부 고급 기능 앱(ex:ChatGPT) 유료  

  \[Make]  
    
   \- 장점: 시각적 워크플로우 구성에 적합, 다단계 시나리오 가능, 오류 위치 표시로 수정 용이  
   \- 단점: 초기 학습 곡선이 있음, 무료 플랜의 데이터·로그·사용량 제한이 있음  
  
+ **적합한 상황**

  \-Zapier: 초보자가 빠르게 자동화를 구현하거나, 비교적 단순한 워크플로우를 쉽게 구성·관리하는 경우
  \-Make: 여러 단계를 포함한 복잡한 시나리오를 설계해야 하거나, 실행 흐름과 오류 위치를 세부적으로 확인하며 관리해야 하는 경우
  
---  

## [프로젝트2] 자유 주제 자동화 설계 및 구현  
 ### 1. 자동화 설계  
 + 반복 업무 정의: Google Calendar에 '회의' 일정이 등록되면 일정 정보를 Google Sheets에 저장하고, AI가 미리 입력된 프롬프트를 바탕으로 회의 준비 문서를 작성한 뒤 Google Docs에 자동으로 문서를 생성  
 + 선정 도구: Zapier (직관적 UI/UX로 초보자도 빠르게 구현, 무료 범위 내 구현 가능)
 + 워크플로우 흐름:
   1. Trigger: Google Calendar - New Event  
   2. Filter: Contains '회의'  
   3. Action1: Google Sheets - Create Spreadsheet Row  
   4. AI Action: AI by Zapier - Generate Text
   5. Action2: Google Docs - Create Document From Text
