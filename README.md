# TimeBoxPlanner
> 🚧 Solo-developed Android app, currently in active development.

> 🇰🇷 한국어 설명은 아래에,  
> 🇺🇸 English version follows.

---

## 🇰🇷 프로젝트 개요

**TimeBoxPlanner**는 하루를 시간 단위로 시각화하여  
사용자가 가장 중요한 일(Big3)을 중심으로  
집중 루틴을 설계하고 실행할 수 있도록 돕는 안드로이드 앱입니다.

단순한 할 일 관리가 아니라,  
**시간의 흐름 속에서 ‘무엇에 집중할 것인가’를 결정하고 실천하는 경험**에 초점을 둡니다.

---

## 🎯 기획 의도

- 하루를 **시간 블록 단위로 시각화**
- 가장 중요한 3가지 일(Big3)을 중심으로 우선순위 명확화
- 드래그 기반 인터랙션을 통한 직관적인 계획 수립
- 실행 → 수정 → 회고가 자연스럽게 이어지는 UX 설계

**핵심 키워드**  
타임박싱 · 집중 루틴 · 시각적 계획 · 드래그 앤 드롭 · 카테고리 기반 통계

---

## 🧱 앱 구조

### 📍 탭 1 — TimeBox (계획 & 실행)

- **중앙 타임라인**
  - 하루 시간대(예: 6:00–24:00)를 고정된 세로 타임라인으로 표시
  - 할 일을 시간 블록으로 배치

- **Todo (브레인 덤프) 영역**
  - 우선순위 없이 자유롭게 할 일을 작성
  - 드래그를 통해 타임라인 또는 Big3로 이동

- **Big3 영역**
  - 오늘 가장 중요한 3가지 할 일 선택
  - 타임라인에서 강조된 블록 형태로 표시

- **타임라인 인터랙션**
  - 드래그로 시간 배치
  - 블록 높이 = 소요 시간
  - 탭 / 더블탭 / 드래그 핸들을 통한 빠른 수정

---

### 🏷 카테고리 시스템

- 기본 카테고리 제공 (공부 / 일 / 운동 / 기타)
- 사용자 정의 카테고리 생성 (이름 + 색상)
- 타임라인 및 Todo에 색상 태그 표시
- 카테고리별 집중 시간 및 달성률 자동 집계

---

### 🔄 사용 흐름

1. **계획**
   - Todo 브레인 덤프 → 카테고리 선택 → Big3 지정 → 타임라인 배치

2. **실행**
   - Big3 시작/종료 알림
   - 실행 중에도 자유로운 수정 및 이동

3. **회고**
   - 완료된 블록 하이라이트
   - Big3 달성률 및 집중 시간 확인

---

## 📊 탭 2 — 마이페이지

- 집중 시간 및 성취율 통계 대시보드
- 주간 / 월간 Big3 달성률
- 시간대별 집중도, 요일별 패턴 분석
- 카테고리별 통계 필터링
- 다크모드, 카테고리 관리, 로그인 설정

---

## 🔐 로그인 및 데이터 관리

- 비로그인 상태: **게스트 모드 (Room DB)**
- Google 로그인 시 기존 로컬 데이터 서버 업로드
- 로컬 ↔ Firestore 양방향 동기화
- 로그아웃 시 데이터 삭제가 아닌 **숨김 처리**
- 재로그인 시 기존 데이터 복원
- 회원 탈퇴 시 로컬 및 서버 데이터 완전 삭제

---

## 📐 Architecture Decision Records (ADR)

이 프로젝트는 주요 아키텍처 및 UX 설계 결정을  
**ADR(Architecture Decision Record)** 문서로 기록하고 있습니다.

각 ADR은 “왜 이런 설계를 선택했는지”에 대한 맥락과 판단을 담고 있습니다.

### 🇰🇷 설계 결정 목록

- **ADR 001** — 그리드 기반 타임라인 UI 설계  
  `docs/adr/001-grid-based-timeline-ui.md`

- **ADR 002** — 게스트 모드 및 로그인 데이터 동기화 전략  
  `docs/adr/002-guest-login-sync-strategy.md`

- **ADR 003** — 타임라인 제스처 인터랙션 모델  
  `docs/adr/003-timeline-gesture-model.md`

---

## 🧩 설계 및 리팩토링

- Home 기능을 역할 단위로 분리하여 책임 명확화
- 타임라인 UI를 **그리드 기반 구조**로 통합
- 블록 높이 = 시간 길이로 직관성 강화
- 제스처 충돌을 유발하던 기존 리스트/스와이프 UI 제거

---

## 🚧 현재 상태

- 개인 프로젝트로 **활발히 개발 중**
- UX 완성도 및 퍼포먼스 지속 개선 중

---

---

## 🇺🇸 Overview (English)


Step-based time-block planning Android app built with Jetpack Compose.  
TimeBoxPlanner helps users design and execute focused daily routines by visualizing their day in time blocks, centered around their most important tasks (Big3).

---

## 🎯 Goal

TimeBoxPlanner is designed to help users:
- Visualize their day in **time units**
- Focus on what matters most through **Big3 prioritization**
- Build and execute **intentional, distraction-free routines**

**Keywords**  
Timeboxing · Focused Routine · Visual Planning · Drag & Drop · Category-based Statistics

---

## 🧱 App Structure

### 📍 Tab 1 — TimeBox (Planning & Execution)

#### Core Layout

| Area | Description |
|----|------------|
| Central Timeline | Vertical timeline showing a fixed daily range (e.g. 6:00–24:00). Tasks are placed by time. |
| Todo (Brain Dump) | Free-form list of tasks for the day. No order or priority required. Supports drag & drop. |
| Big3 Area | Select the 3 most important tasks. Big3 items are highlighted and visually emphasized on the timeline. |
| Timeline Blocks | Tasks can be dragged into the timeline. Block height represents time duration. |
| Progress State | Visual states for ongoing / completed / incomplete tasks using color and opacity changes. |

#### Timeline Interaction
- Drag tasks to assign time blocks
- Resize blocks by dragging handles (time length = block height)
- Single tap → edit / delete bottom sheet
- Double tap → toggle complete / incomplete
- Completed tasks show strikethrough and reduced opacity

#### Smart Assistance
- Detects empty time slots between Big3 blocks
- Allows quick filling with existing Todos
- Notifications for Big3 start/end times

---

### 🏷 Category System

| Feature | Description |
|----|------------|
| Default Categories | Study / Work / Exercise / Others |
| Custom Categories | User-defined name & color |
| Visual Tags | Category color shown in timeline & Todo |
| Toggle Display | Option to show/hide category colors |
| Statistics | Auto aggregation by category (focus time, completion rate, frequency) |

---

### 🔄 UX Flow

**1. Planning**  
Brain dump Todos → Select category → Choose Big3 → Place on timeline



**2. Execution**
- Big3 notifications
- Tasks can be moved or edited anytime
- Empty time suggestions

**3. Daily Review**
- Highlight completed blocks
- Show Big3 achievement rate & focus time

---

## 📊 Tab 2 — My Page

### Features
- Focus & achievement dashboard
- Shareable statistics
- Settings (dark mode, category management, login)
- Login / Logout / Account deletion

### Core Statistics
- Big3 completion rate (daily / weekly / monthly)
- Time-of-day focus distribution
- Weekly consistency patterns
- Consistency score with streak indicators
- Category-based filtering for all metrics

---

## 🔐 Login & Data Management

- App starts in **Guest Mode** (local Room DB only)
- Google login uploads local data to Firestore
- Bidirectional sync (local ↔ server)
- Logout hides account data instead of deleting it
- Re-login restores previously hidden data
- Account deletion removes all related data (local + server)

---

## 🧩 Architecture & Refactoring

### 🇺🇸 Architecture Decisions

This project documents key architectural and UX decisions using ADRs.

Each record explains **why** a particular decision was made, rather than how it was implemented.

- **ADR 001** — Grid-based timeline UI  
  `docs/adr/001-grid-based-timeline-ui.md`

- **ADR 002** — Guest mode & login data sync strategy  
  `docs/adr/002-guest-login-sync-strategy.md`

- **ADR 003** — Timeline gesture interaction model  
  `docs/adr/003-timeline-gesture-model.md`

### Home Feature Refactor (2025-12)

| File | Responsibility |
|----|---------------|
| HomeScreen.kt | Host & navigation |
| HomeViewModel.kt | State, events, business logic |
| HomeStep1.kt | Todo input & dialogs |
| HomeStep2.kt | Big3 selection |
| HomeStep3.kt | Timeline placement |
| HomeTimeline.kt | Shared timeline UI & bottom sheets |

**Design Decision**  
Timeline UI was unified into a grid-based system where block height directly represents time duration (similar to Google Calendar).  
Previous list/swipe UI was removed to prevent gesture and layout conflicts.

---

## 🧪 Development Log Highlights

### 2025-11-27
- Improved Step3 timeline drag & time-based repositioning

### 2025-12-04
- Introduced `HomeTimeline.kt`
- Implemented quick edit mode (swipe actions, bottom sheets, undo snackbar)

### 2025-12-05
- Added “Unscheduled Todos” notification concept

### 2025-12-12
- Major file responsibility refactor
- Separated UI, logic, and routing clearly

### 2025-12-13
- Timeline interactions finalized:
  - Single tap → edit sheet
  - Double tap → complete toggle
  - Drag handle → adjust time range

---

## 🚧 Current Status

Active development.  
Remaining tasks include:
- AM/PM timeline labels (1–24 format)
- Visual divider between morning / afternoon
- Polished edit bottom sheet UX
- Bidirectional complete toggle via double tap
- Performance and UX polish


---

## 🛠 Tech Stack

- Kotlin
- Jetpack Compose
- Room
- Firebase Firestore
- MVVM Architecture

---

## 📌 Notes

This project is a **solo-developed Android app**, covering:
- UX planning
- Architecture decisions
- Implementation
- Refactoring
- Store-ready data handling

It focuses on balancing **user-centered design** with **maintainable architecture**.
