# P!ckMap

> **여행할 장소를 골라서 뽑자! 국내 여행 미션 추천 앱**

P!ckMap은 국내 여행 중 "다음엔 뭘 해야 하지?"라는 고민을 줄이기 위해 개발된 Android 애플리케이션입니다. 여행자들이 해당 지역에서 할 수 있는 활동과 방문할 만한 장소를 미션 형식으로 제안하고 공유할 수 있습니다.

## 프로젝트 정보

- **팀명**: adm@p (admin + map의 합성어)
- **앱 이름**: P!ckMap (Pick + Map의 합성어)
- **과목**: GURU2 6조
- **개발 기간**: 2024학년도

## 주요 기능

### 1. 회원가입/로그인
- Firebase Authentication을 활용한 이메일 기반 인증
- 안전한 사용자 계정 관리

### 2. 홈 화면
- Google Maps API를 통한 현재 위치 지도 표시
- 검색 기능으로 미션 목록 화면 이동
- 기본 위치: 서울여자대학교 (에뮬레이터 환경)

### 3. 미션 검색 및 관리
- 지역별 미션 검색 기능
- 미션 완료 체크박스 기능
- 북마크 기능으로 원하는 미션 저장

### 4. 미션 생성
- 다이얼로그 형식의 미션 추가 인터페이스
- 지역과 미션 내용 입력
- Firebase Firestore에 실시간 저장

### 5. 마이페이지
- 완료한 미션 리스트 확인
- 사용자 이메일 정보 표시
- 로그아웃 기능
- 회원탈퇴 기능

## 기술 스택

### Frontend
- **Language**: Kotlin
- **UI Framework**: Android SDK
- **View Binding**: ViewBinding

### Backend & Database
- **Authentication**: Firebase Authentication
- **Database**: Firebase Firestore
- **Real-time Sync**: Firestore Snapshot Listeners

### API & Libraries
- **Google Maps API**: 지도 표시 및 위치 서비스
- **Google Play Services**: 위치 권한 관리
- **RecyclerView**: 미션 리스트 표시
- **Material Design Components**: UI/UX 디자인

### Development Tools
- **IDE**: Android Studio
- **Build System**: Gradle (Kotlin DSL)
- **Version Control**: Git

## 디자인

### 색상 팔레트
- **메인 컬러**: `#41924B` (녹색)
- **서브 컬러**: `#BCCFBD` (연한 녹색)
- **포인트 컬러**: `#FFCF52` (노란색)

### 폰트
- Apple SD Gothic Neo

## 프로젝트 구조

```
pickmap/
├── app/
│   └── src/
│       └── main/
│           ├── java/com/example/guruapp/
│           │   ├── MainActivity.kt              # 메인 액티비티
│           │   ├── LoginActivity.kt             # 로그인 화면
│           │   ├── SearchActivity.kt            # 미션 검색 화면
│           │   ├── HomeFragment.kt              # 홈 화면 (지도)
│           │   ├── MissionFragment.kt           # 미션 데이터 모델
│           │   ├── MypageFragment.kt            # 마이페이지
│           │   ├── MissionAdapter.kt            # 미션 리스트 어댑터
│           │   ├── customdialog.kt              # 미션 생성 다이얼로그
│           │   └── LozationProvider.kt          # 위치 제공자
│           ├── res/
│           │   ├── layout/                      # XML 레이아웃 파일
│           │   ├── drawable/                    # 이미지 리소스
│           │   ├── values/                      # 색상, 문자열 리소스
│           │   └── font/                        # 폰트 파일
│           └── AndroidManifest.xml              # 앱 설정 파일
└── docu/                                         # 프로젝트 문서
    ├── 기획서.pdf
    └── 육은서_개발_일지.pdf
```

## 주요 화면

### 1. 로그인 화면
사용자 인증을 위한 이메일 기반 로그인

### 2. 홈 화면
Google Maps를 활용한 현재 위치 표시 및 검색 기능

### 3. 미션 검색
지역별 미션 검색 및 완료 체크

### 4. 미션 생성 다이얼로그
간편한 미션 추가 인터페이스

### 5. 마이페이지
완료한 미션 리스트 및 계정 관리

# 주요 개발 내용
- UI/UX 디자인 및 목업 제작
- 다이얼로그 기반 미션 생성 기능 구현
- Firebase 연동 및 데이터베이스 설계
- Google Maps 통합

## 기술 상세

### 미션 데이터 구조
```kotlin
data class Mission(
    val id: String = "",
    val location: String = "",
    val mission: String = "",
    val isBookmarked: Boolean = false
)
```

### Firebase 컬렉션 구조
```
missions/
  └── {userId}/
      └── userMissions/
          └── {missionId}
              ├── location: String
              └── mission: String

users/
  └── {userId}/
      └── bookmarkedMissions/
          └── {missionId}
              ├── id: String
              ├── location: String
              ├── mission: String
              └── isBookmarked: Boolean
```

## 앱 권한

앱에서 사용하는 권한:
- `INTERNET`: Firebase 및 Google Maps API 통신
- `ACCESS_FINE_LOCATION`: 정확한 위치 정보 접근
- `ACCESS_COARSE_LOCATION`: 대략적인 위치 정보 접근

## 알려진 이슈

- 에뮬레이터 환경에서 현재 위치 기능 제한 (기본 위치: 서울여자대학교)
- Google API 키는 보안을 위해 별도로 관리 필요

## 기여자

### 6kitty - 디자인 & 프론트엔드 개발
**26 commits** | `sixeunseoth@gmail.com`

#### 주요 기여 내역:
- **UI/UX 디자인**
  - 전체 앱 디자인 시스템 및 색상 팔레트 구축
  - 모든 화면의 디자인 목업 제작
  - 커스텀 폰트 통합 (Apple SD Gothic Neo)

- **다이얼로그 시스템 구현**
  - `customdialog.kt` - 미션 생성 다이얼로그 컴포넌트
  - `dialog.xml` - 다이얼로그 레이아웃 디자인
  - MainActivity와 다이얼로그 통합

- **레이아웃 개발**
  - `fragment_home.xml` - 지도 뷰가 포함된 홈 화면
  - `activity_search.xml` - 미션 검색 인터페이스
  - `activity_login.xml` - 로그인 화면 레이아웃
  - `item.xml` - 미션 리스트 아이템 디자인
  - `rounded_map_view_background.xml` - 지도 스타일링
  - `baseline_check_box_24.xml` - 커스텀 체크박스 디자인

- **문서화**
  - 개발 일지 및 과정 문서화
  - 디자인 명세 및 가이드라인 작성

## 라이선스

이 프로젝트는 교육 목적으로 개발되었습니다.

## 문의

프로젝트에 대한 문의사항이 있으시면 이슈를 등록해 주세요.

---

**Made with ❤️ by adm@p Team**
