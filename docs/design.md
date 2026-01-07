---
marp: true
theme: default
paginate: true
header: "Next.js 기반 멀티테넌트 사이트 생성 솔루션"
footer: "© 2026 Solution Architecture"
backgroundColor: #f9f9f9
---

# Next.js 기반 
# **멀티테넌트 디플 미니샵 생성 솔루션**
### 단일 빌드로 구현하는 무한 확장형 웹 서비스

---

## 1. 핵심 컨셉: "물리적 생성" vs "논리적 생성"

- **과거 방식:** 업체 가입 시 새로운 HTML/JS 파일을 생성하고 개별 빌드
- **Next.js 솔루션:** - 단일 코드 베이스(Codebase) 유지
  - 요청 도메인에 따라 DB에서 설정을 불러와 실시간 렌더링
  - **빌드 없이 즉시 사이트 개설 가능**

---

## 2. 시스템 아키텍처

1. **Middleware:** 들어오는 커스텀 도메인(`A.com`, `B.com`) 식별
2. **Rewriting:** 내부적으로 기본 도메인 `app/[tenant]/page.tsx`로 경로 연결
3. **Data Fetching:** 해당 테넌트의 UI 설정값(JSON) 로드
4. **Dynamic Rendering:** 설정에 따라 HTML 구성 요소 조합

---

## 3. 업체별 맞춤형 UI 구현 (Flexible HTML)

> "가운데 버튼뿐만 아니라 전체 구조를 다르게"

- **컴포넌트 조립 방식:**
  - `Hero`, `Product`, `Order`, `Result` 등 표준 컴포넌트 보유
  - DB에 저장된 **Layout Schema** 순서에 따라 컴포넌트 배치
- **스타일 동적 주입:**
  - 업체별 고유 컬러, 폰트, 로고 등을 CSS Variable로 실시간 적용

---

## 4. 기술적 차별점

| 항목 | 구현 방식 | 기대 효과 |
| :--- | :--- | :--- |
| **확장성** | Dynamic Routing (`[tenant]`) | 수만 개 업체도 추가 빌드 없이 수용 |
| **속도** | ISR (On-demand Revalidation) | 정적 페이지 수준의 속도 + 실시간 업데이트 |
| **유지보수** | 단일 코드베이스 | 모든 업체의 버그 수정/기능 업데이트가 한 번에 반영 |
| **도메인** | Middleware Rewrites | 업체별 커스텀 도메인 완벽 지원 |

---

## 5. 비즈니스 가치

- **운영 비용 절감:** 자동화된 사이트 생성 프로세스로 인건비 최소화
- **즉각적인 서비스:** 결제 완료 직후 사이트 활성화 (Time-to-Market)
- **데이터 통합 관리:** 모든 테넌트 데이터를 한 곳에서 분석 및 관리

---

# Q&A
### 감사합니다.
