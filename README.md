## 프로젝트 개요
### 1.1 목표
본 프로젝트는 모바일 퍼스트 기준의 정적 랜딩 페이지를 HTML·CSS 중심으로 구현하는 퍼블리싱 프로젝트이다. 디자인 시안 기반으로 구조 설계, 레이아웃 구현, 컴포넌트 분리를 단계적으로 진행하며, 실제 실무 퍼블리싱 프로세스를 그대로 재현하는 것을 목표로 한다.

시맨틱 마크업을 기본 원칙으로 header, main, section, footer 구조를 명확히 구분하고, 접근성을 고려한 heading 구조, visually-hidden 처리, 적절한 alt 텍스트와 ARIA 속성을 적용한다. 클래스 네이밍은 BEM 컨벤션을 사용해 역할과 책임이 드러나도록 설계한다.

CSS는 reset, base, layout, main, components 단위로 분리하여 관리하며, 전역 디자인 토큰을 변수로 정의해 색상·타이포그래피·간격의 일관성을 유지한다. 레이아웃은 flexbox를 중심으로 구성하고, 미디어 쿼리를 통해 PC 환경까지 자연스럽게 확장 가능한 구조를 만든다.

---

### 1.2 주요 기능

- 모바일 퍼스트 반응형 레이아웃 구현
모바일 기준으로 구조를 설계하고 미디어 쿼리를 통해 PC 환경까지 확장한다. 동일한 마크업을 유지한 채 레이아웃만 전환되도록 구성한다.

---

- 시맨틱 마크업 및 문서 구조 확보
header, main, section, footer를 명확히 구분한다. 
<table>
  <tr>
    <td>
      <div style="display: flex; justify-content: center;">
        <img src="./log/1-2 시맨틱 마크업.png">
      </div>
    </td>
    <td>
      <div style="display: flex; justify-content: center;">
        <img width="600" src="./log/1-2 시멘틱 마크업(2).png">
      </div>
    </td>
  </tr>
</table>

---

- 접근성 대응 

<img src="./log/1-2 접근성 대응.png" alt="히어로 섹션" width="400">

    ```HTML
    .visually-hidden{
        position: absolute; (문서 흐름에서 제거)
        width: 1px; (화면에 보이지 않도록 렌더 영역을 극소화)
        height: 1px;
        padding: 0; (초기화, 영역 생기는 것 방지)
        margin: -1px; (1px 영역조차 화면에 남지 않도록)
        overflow: hidden; (박스 밖에서도 보이지 않게)
        clip: rect(0, 0, 0, 0); (시각적으로 완전 비노출 상태)
        white-space: nowrap; (줄바꿈으로 인해 렌더링 영역이 생기는 것을 방지)
        border: 0; (테두리 방지)
    }
    ```

   visually-hidden 헤딩, 의미 있는 alt 텍스트, ARIA 속성을 적용해 접근성을 확보 한다.


---

 BEM 기반 클래스 네이밍

```mermaid
graph TD

page-header --> page-header__inner
page-header__inner --> page-header__logo
page-header__inner --> page-header__menu-btn
page-header__menu-btn --> page-header__menu-icon
page-header__inner --> page-header__nav-pc
page-header__nav-pc --> page-header__nav-list
page-header --> page-header__nav

page-header__nav --> nav-drawer
nav-drawer --> nav-drawer__header
nav-drawer__header --> nav-drawer__close-btn
nav-drawer__close-btn --> nav-drawer__close-icon
nav-drawer --> nav-drawer__body
nav-drawer__body --> nav-drawer__list
nav-drawer__list --> nav-drawer__item
nav-drawer__item --> nav-drawer__link

hero --> hero__content
hero__content --> hero__title
hero__content --> hero__description
hero --> hero__image

profile --> profile__image
profile --> profile__text
profile__text --> profile__title
profile__text --> profile__description

gallery --> gallery__text
gallery__text --> gallery__title
gallery__text --> gallery__description
gallery --> gallery__slider
gallery__slider --> gallery__track
gallery__track --> gallery__slide
gallery --> gallery__outro
gallery__outro --> gallery__description

subscribe --> subscribe__text
subscribe__text --> subscribe__title
subscribe__text --> subscribe__description
subscribe --> subscribe__form
subscribe__form --> subscribe__input-wrapper
subscribe__input-wrapper --> subscribe__icon
subscribe__input-wrapper --> subscribe__input

footer --> footer__brand
footer__brand --> footer__logo
footer__brand --> footer__social
footer__social --> footer__social-item
footer --> footer__menu
footer__menu --> footer__nav

modal --> modal__dim
modal --> modal__content
modal__content --> modal__image
modal__content --> modal__text
modal__text --> modal__title
modal__text --> modal__description

```

   블록·엘리먼트·모디파이어 역할이 드러나도록 네이밍한다. 스타일 충돌을 방지하고 유지보수를 용이하게 한다.


---

- CSS 레이어 분리 구조
<img src="./log/1-2 모바일 퍼스트 반응형 레이아웃 구현 - css파일 링크.png" alt="히어로 섹션" width="400">

link 태그로 외부 CSS파일 연결
reset, base, layout, main, components 단위로 CSS를 분리한다. 전역 변수로 디자인 토큰을 관리해 일관성을 유지한다.
브라우저가 각 CSS 파일을 병렬로 요청·캐싱
초기 로딩과 재방문 성능이 안정적
 파일 단위로 책임이 분리되어 역할 경계가 명확해지고, 변경 영향 범위가 예측 가능합니다.
 DevTools에서 파일별로 규칙을 추적하기 쉬워 디버깅과 유지보수가 수월합니다.

 ---  

- 히어로·프로필·갤러리·구독 섹션 구현
<img src="./log/1-2 히어로·프로필·갤러리·구독 섹션 구현.png" alt="히어로 섹션" width="400">
<img src="./log/1-2 히어로·프로필·갤러리·구독 섹션 구현(2).png" alt="히어로 섹션" width="400">

각 섹션을 독립적인 레이아웃 단위로 구성한다. 섹션별 제목, 콘텐츠, 버튼 구조를 명확히 분리한다.
필요에 따라 레이아웃 배치를 위해 컨테이너를 추가한다.

---

- 네비게이션 드로어
모바일 환경에서 햄버거 버튼을 통해 슬라이드형 네비게이션을 제공한다. PC 환경에서는 헤더 네비게이션으로 전환된다.

---

- 모달 컴포넌트
body 직속 레이어 구조로 모달을 구현한다. 배경 차단, 포커스 흐름 제어를 고려한 구조를 적용한다.

---

- 공용 버튼 컴포넌트
<img src="./log/1-2 공용 버튼 컴포넌트.png" alt="히어로 섹션" width="400">
<img src="./log/1-2 공용 버튼 컴포넌트(2).png" alt="히어로 섹션" width="400">


디자인과 인터랙션이 동일한 버튼을 컴포넌트화한다. 섹션별로 재사용 가능하도록 설계한다.

---

- Git 커밋 단위 기록 방식
<img src="./log/1-2 git 커밋 단위 기록 방식.png" alt="히어로 섹션" width="400">

각 작업을 하나의 커밋 단위로 관리한다. 이슈, 원인, 해결 과정, 코드 변경 내용을 문서화해 기록 자산으로 남긴다.

---

- 정적 퍼블리싱 중심 구조
JavaScript 의존 없이 HTML·CSS 중심으로 완성한다. 이후 인터랙션 확장이 가능하도록 구조적 여지를 남긴다.

---

### 1.3 팀 구성

<table style="width:100%; border-collapse:collapse;">
    <tbody>
        <tr>
            <td style="text-align:center; vertical-align:middle; height:3rem;">
                이현규
            </td>
            <td style="text-align:center; vertical-align:middle; height:3rem;">
                위니브 스승님
            </td>
            <td style="text-align:center; vertical-align:middle; height:3rem;">
                GPT
            </td>
        </tr>
        <tr>
            <td style="padding:0; height:200px;">
                <img 
                    src="./log/1-3  팀구성.png"
                    style="display:block; width:100%; height:100%; object-fit:cover;"
                    alt=""
                >
            </td>
            <td style="padding:0; height:200px;">
                <img 
                    src="./log/1-3 위니브.png"
                    style="display:block; width:100%; height:100%; object-fit:cover;"
                    alt=""
                >
            </td>
            <td style="padding:0; height:200px;">
                <img 
                    src="./log/1-3 gpt.png"
                    style="display:block; width:100%; height:100%; object-fit:cover;"
                    alt=""
                >
            </td>
        </tr>
    </tbody>
</table>


본 프로젝트는 개인 단독 개발을 중심으로 진행되었으며, 설계 방향과 구현 과정에서 멘토진의 조언을 참고하였다. 개발 전반에서는 GPT를 활용해 구조 검토, 문제 해결, 문서 정리를 보조 도구로 활용하였다.

---
## 개발 환경 및 배포

### 2.1 개발 환경
- HTML5, CSS3 (Semantic Markup)
- VS Code

### 2.2 배포 URL
- https://lhk0721.github.io/MiniProject-02/

---

## 요구사항 명세 및 기능 명세
```mermaid
flowchart TD
    A[페이지 진입] --> B[스크롤 없음]
    B -->|스크롤 발생| C[스크롤 중]

    C --> D[헤더 고정]
    C --> E[Top 버튼 표시]

    E -->|Top 버튼 클릭| F[부드러운 스크롤로 최상단 이동]
    F --> G[최상단 도달]

    G --> H[헤더 고정 해제]
    G --> I[Top 버튼 숨김]

```

---

```mermaid
flowchart TD
    A[Subscribe 버튼 클릭] --> B[이메일 유효성 검사]

    B -->|유효하지 않음| C[alert 경고 표시]
    C --> D[모달 닫힘 상태 유지]

    B -->|유효함| E[모달 표시]
    E --> F[OK! I love HODU 클릭]
    F --> G[form 제출]
    G --> H[모달 닫힘]

```

---

```mermaid
stateDiagram-v2
    [*] --> 초기로드

    초기로드 : 헤더 비고정
    초기로드 : Top 버튼 숨김
    초기로드 : 모달 닫힘

    초기로드 --> 스크롤중

    스크롤중 : 헤더 고정
    스크롤중 : Top 버튼 표시

    스크롤중 --> 푸터근처

    푸터근처 : Top 버튼 푸터 위 고정

    스크롤중 --> Subscribe클릭
    Subscribe클릭 : 이메일 유효성 검사

    Subscribe클릭 --> 모달열림
    모달열림 : 모달 표시

    모달열림 --> 확인클릭
    확인클릭 : form 제출
    확인클릭 : 모달 닫힘

    확인클릭 --> 스크롤중

```


---


## 프로젝트 구조 및 개발 일정
4.1 프로젝트 구조
```
MiniProject-02/
├─ index.html
├─ README.md
│
├─ img/
│  ├─ arrow-left.svg
│  ├─ arrow-right.svg
│  ├─ blog.svg
│  ├─ box-cat.png
│  ├─ cat-subscribe.png
│  ├─ facebook.svg
│  ├─ img_1.jpg
│  ├─ img_2.jpg
│  ├─ img_3.jpg
│  ├─ img_4.jpg
│  ├─ img_5.jpg
│  ├─ instagram.svg
│  ├─ logo.png
│  ├─ logo.svg
│  ├─ mail.svg
│  ├─ main.png
│  ├─ menu.svg
│  ├─ Miniproject-02.html
│  ├─ modal-bg-img.png
│  ├─ nos_down.exe
│  ├─ top-btn.svg
│  └─ youtube.svg
│
├─ src/
│
└─ style/
   ├─ reset.css
   ├─ base.css
   ├─ componenets.css
   ├─ components-temp.css
   ├─ layout.css
   ├─ layout-temp.css
   ├─ main.css
   └─ main-temp.css

```


### 4.2 개발 일정(WBS)
```mermaid
gantt
    title MiniProject-02 커밋 단위 작업 일정표
    dateFormat  YYYY-MM-DDTHH:mm
    axisFormat  %m/%d %H:%M

    section 12/16 (Tue) 초기 세팅
    프로젝트 디렉토리·에셋 초기 구성        :c1, 2025-12-16T14:02, 2025-12-16T14:10
    page-wrapper 레이아웃 구조 확정           :c2, 2025-12-16T14:10, 2025-12-16T14:20
    header·nav 시멘틱 구조 리팩터링           :c3, 2025-12-16T14:20, 2025-12-16T14:45

    section 12/16 (Tue) 메인 섹션 초안
    공용 버튼 컴포넌트 CSS 추가               :c4, 2025-12-16T19:41, 2025-12-16T19:55
    hero 섹션 레이아웃 초안                   :c5, 2025-12-16T20:06, 2025-12-16T20:20
    profile 섹션 레이아웃 초안                :c6, 2025-12-16T20:59, 2025-12-16T21:05
    gallery 섹션·슬라이더 베이스               :c7, 2025-12-16T21:05, 2025-12-16T21:20

    section 12/17 (Wed)
    subscribe 폼 구조 개선                    :c8, 2025-12-17T13:34, 2025-12-17T14:10
    메인 하단 배경 오버레이 적용              :c9, 2025-12-17T14:10, 2025-12-17T15:30
    modal 구조 확정                           :c10, 2025-12-17T15:30, 2025-12-17T17:14

    section 12/19 (Fri) 전역·하단
    footer 레이아웃 및 네비 구조               :c11, 2025-12-19T12:24, 2025-12-19T13:00
    전역 디자인 변수 정의                     :c12, 2025-12-19T13:15, 2025-12-19T13:30
    meta description 적용                     :c13, 2025-12-19T13:46, 2025-12-19T14:00

    section 12/19 (Fri) 헤더·Hero
    header/nav 구조 분리                      :c14, 2025-12-19T14:09, 2025-12-19T14:20
    nav-drawer 스타일 완성                    :c15, 2025-12-19T14:20, 2025-12-19T14:33
    hero 섹션 디자인 완성                     :c16, 2025-12-19T14:33, 2025-12-19T14:51

    section 12/19 (Fri) 메인 섹션
    profile 섹션 스타일 구현                  :c17, 2025-12-19T15:13, 2025-12-19T15:25
    gallery 섹션 디자인·버튼 개선              :c18, 2025-12-19T15:29, 2025-12-19T15:46
    subscribe 섹션 디자인 완성                :c19, 2025-12-19T16:09, 2025-12-19T16:20
    footer·modal 디자인 보완                  :c20, 2025-12-19T16:20, 2025-12-19T16:40
    로고 링크·alt 접근성 개선                 :c21, 2025-12-19T16:40, 2025-12-19T16:49

    section 12/19 (Fri) PC 대응
    PC 헤더 네비게이션 추가                   :c22, 2025-12-19T20:17, 2025-12-19T21:00
    README initial commit                     :c23, 2025-12-19T21:58, 2025-12-19T22:05

    section 12/20 (Sat)
    섹션 정렬 로직 수정                       :c24, 2025-12-20T01:04, 2025-12-20T01:16
    profile PC 미디어쿼리                     :c25, 2025-12-20T01:16, 2025-12-20T01:32
    subscribe PC 미디어쿼리                   :c26, 2025-12-20T02:32, 2025-12-20T02:41
    footer PC 미디어쿼리                      :c27, 2025-12-20T02:41, 2025-12-20T02:55
    README 초안 병합                          :c28, 2025-12-20T04:09, 2025-12-20T04:10

```
---

## 와이어프레임 / UI / BM
###  와이어프레임, 화면 설계, 메인 기능 설명
<img src="./log/5. 와이어프레임.png" alt="와이어프레임 전체 가진" width="400">

<table style="width:100%; border-collapse:collapse;">
<tbody>
 <tr>
     <td style="padding:10px 12px; text-align:left; vertical-align:middle; font-size:14px; line-height:1.6;">
         MiniProject02-HODU<br>
         화면 구성의 방향성과 주요 UI 흐름을 빠르게 공유하기 위한 초안입니다. 각 화면은 후속 퍼블리싱 및 기능 구현의 기준으로 사용합니다.
     </td>
 </tr>

 <tr>
     <td style="padding:8px 12px; text-align:center; vertical-align:middle; height:3rem; font-weight:600;">
         Main-PC
     </td>
 </tr>
 <tr>
     <td style="padding:0; height:800px;">
         <img src="./log/5.1 와이어프레임/프로젝트_ 랜딩페이지_PC.png" alt="메인 와이어프레임" style="display:block; width:100%; height:100% object-fit:cover;">
     </td>
 </tr>

 <tr>
     <td style="padding:8px 12px; text-align:center; vertical-align:middle; height:3rem; font-weight:600;">
         modal
     </td>
 </tr>
 <tr>
     <td style="padding:0; height:400px;">
         <img src="./log/5.1 와이어프레임/modal.svg" alt="모달열림 와이어프레임" style="display:block; width:100%;  object-fit:cover;">
     </td>
 </tr>

 <tr>
     <td style="padding:8px 12px; text-align:center; vertical-align:middle; height:3rem; font-weight:600;">
         Main-mobile
     </td>
 </tr>
 <tr>
     <td style="padding:0; height:3500px;">
         <img src="./log/5.1 와이어프레임/프로젝트_랜딩페이지_Mobile.png" alt="메인-모바일 와이어프레임" style="display:block; width:100%;  object-fit:cover;">
     </td>
 </tr>

 <tr>
     <td style="padding:8px 12px; text-align:center; vertical-align:middle; height:3rem; font-weight:600;">
         Navigation-drawer
     </td>
 </tr>
 <tr>
     <td style="padding:0; height:1000px;">
         <img src="./log/5.1 와이어프레임/프로젝트_랜딩페이지_Mobile_2.png" alt="네비게이션 서랍" style="display:block; width:100%;  object-fit:cover;">
     </td>
 </tr>
</tbody>
</table>

---

### 데이터베이스 모델링(ERD)

```mermaid
erDiagram
    USER ||--o{ USER_AUTH : has
    USER ||--o{ SESSION : creates
    USER ||--o{ TRANSLATION : owns
    USER ||--o{ FAVORITE_TRANSLATION : bookmarks
    USER ||--o{ GLOSSARY_TERM : manages
    USER ||--o{ SEARCH_LOG : searches

    LANGUAGE ||--o{ TRANSLATION : source
    LANGUAGE ||--o{ TRANSLATION : target
    LANGUAGE ||--o{ GLOSSARY_TERM : language

    TRANSLATION ||--o{ TRANSLATION_VERSION : versions
    TRANSLATION ||--o{ TRANSLATION_TAG : tagged
    TAG ||--o{ TRANSLATION_TAG : used_by

    USER {
        bigint user_id PK
        varchar email UK
        varchar password_hash
        varchar display_name
        varchar phone UK
        varchar role
        boolean is_active
        timestamp created_at
        timestamp updated_at
        timestamp last_login_at
    }

    USER_AUTH {
        bigint auth_id PK
        bigint user_id FK
        varchar provider
        varchar provider_user_key
        varchar access_token
        varchar refresh_token
        timestamp token_expires_at
        timestamp created_at
    }

    SESSION {
        bigint session_id PK
        bigint user_id FK
        varchar session_token UK
        varchar ip_address
        varchar user_agent
        timestamp created_at
        timestamp expires_at
        timestamp revoked_at
    }

    LANGUAGE {
        smallint language_id PK
        varchar code UK
        varchar name
        boolean is_supported
    }

    TRANSLATION {
        bigint translation_id PK
        bigint user_id FK
        smallint source_language_id FK
        smallint target_language_id FK
        text source_text
        text translated_text
        varchar status
        int latency_ms
        timestamp created_at
        timestamp updated_at
    }

    TRANSLATION_VERSION {
        bigint version_id PK
        bigint translation_id FK
        int version_no
        text translated_text
        varchar editor_type
        timestamp created_at
    }

    FAVORITE_TRANSLATION {
        bigint favorite_id PK
        bigint user_id FK
        bigint translation_id FK
        timestamp created_at
    }

    TAG {
        bigint tag_id PK
        varchar name UK
        timestamp created_at
    }

    TRANSLATION_TAG {
        bigint translation_id FK
        bigint tag_id FK
        timestamp created_at
    }

    GLOSSARY_TERM {
        bigint term_id PK
        bigint user_id FK
        smallint language_id FK
        varchar term
        varchar meaning
        varchar note
        timestamp created_at
        timestamp updated_at
    }

    SEARCH_LOG {
        bigint search_id PK
        bigint user_id FK
        varchar query
        varchar scope
        int result_count
        timestamp created_at
    }

```

---

### 아키텍처 설계

```mermaid
flowchart TB
    USER[사용자 브라우저]
    
    USER -->|HTTPS| GITHUB_PAGES[GitHub Pages<br>정적 프론트엔드]

    GITHUB_PAGES -->|API 요청| API_GATEWAY[API Gateway]

    API_GATEWAY -->|인증/인가| AUTH_SERVICE[Auth Service]
    API_GATEWAY -->|비즈니스 요청| APP_SERVER[Application Server]

    AUTH_SERVICE -->|JWT 발급/검증| REDIS[Redis<br>Session / Token Cache]

    APP_SERVER -->|CRUD| DATABASE[(RDBMS<br>User / Translation / Glossary)]
    APP_SERVER -->|번역 요청| AI_ENGINE[AI Translation Engine]

    APP_SERVER -->|로그 저장| LOG_SERVICE[Logging Service]
    LOG_SERVICE -->|적재| LOG_DB[(Log Storage)]

    DATABASE -->|백업| BACKUP[Backup Storage]

    subgraph Frontend
        GITHUB_PAGES
    end

    subgraph Backend
        API_GATEWAY
        AUTH_SERVICE
        APP_SERVER
        AI_ENGINE
    end

    subgraph Data
        DATABASE
        REDIS
        LOG_DB
        BACKUP
    end
```

### 에러 및 트러블슈팅
<img src="./log/이슈.png" alt="히어로 섹션" width="400">
<img src="./log/이슈2.png" alt="히어로 섹션" width="400">
<img src="./log/이슈3.png" alt="히어로 섹션" width="400">
<img src="./log/이슈4.png" alt="히어로 섹션" width="400">
<img src="./log/이슈5.png" alt="히어로 섹션" width="800">
<img src="./log/이슈5-1.png" alt="히어로 섹션" width="400">

