# DoTask — exe 빌드 방법
> made with =_= by **DavidPark** · v1.0.0

---

## ✅ 방법 1: GitHub Actions (가장 쉬움, PC 사양 무관)

### 순서

**1단계 — GitHub 계정 만들기**
https://github.com 에서 무료 가입

**2단계 — 새 레포지토리 만들기**
- 우측 상단 `+` → New repository
- 이름: `dotask` (아무거나 OK)
- Public 또는 Private 둘 다 OK
- Create repository 클릭

**3단계 — 이 폴더 파일 전부 올리기**
레포지토리 페이지에서 `uploading an existing file` 클릭하거나
아래 Git 명령어 사용:

```bash
git init
git add .
git commit -m "DoTask v1.0.0"
git remote add origin https://github.com/본인아이디/dotask.git
git push -u origin main
```

**4단계 — 자동 빌드 시작!**
push하면 자동으로 빌드 시작됩니다.

**5단계 — 빌드 결과물 다운로드**
- GitHub 레포 페이지 → `Actions` 탭 클릭
- 빌드 완료 후 (약 5~10분) → 클릭
- 하단 `Artifacts` 섹션에서 다운로드
  - `DoTask-Windows-exe` → **DoTask Setup 1.0.0.exe**
  - `DoTask-macOS-dmg` → **DoTask-1.0.0.dmg**
  - `DoTask-Linux` → **DoTask.AppImage**

---

## ✅ 방법 2: 내 PC에서 직접 빌드

### 준비물
- Node.js v18 이상: https://nodejs.org 에서 LTS 버전 설치

### 빌드

```bash
# 이 폴더에서 실행
npm install

# Windows .exe 만들기
npm run build:win

# macOS .dmg 만들기 (Mac에서만 가능)
npm run build:mac

# Linux AppImage 만들기
npm run build:linux
```

완료되면 `dist/` 폴더에 파일이 생겨요.

---

## 폴더 구조

```
dotask-build/
├── .github/
│   └── workflows/
│       └── build.yml   ← GitHub Actions 자동 빌드 설정
├── index.html          ← DoTask 앱 전체
├── main.js             ← Electron 메인
├── preload.js          ← 보안 브릿지
├── package.json        ← 빌드 설정
└── README.md           ← 이 파일
```

---

## 자주 묻는 질문

**Q: 빌드에 얼마나 걸려요?**
GitHub Actions 기준 약 5~10분

**Q: 돈 드나요?**
GitHub Actions 무료 플랜으로 월 2,000분 무료. 빌드 1회에 약 15분이면 월 130회 가능

**Q: exe 파일 크기는?**
Electron 특성상 약 80~150MB

**Q: Windows에서 백신이 차단해요**
코드 서명 인증서가 없어서 그래요. 빌드한 본인 PC에서는 `더보기 → 실행` 누르면 됩니다

---

*DoTask · made with =_= by DavidPark*
