# Auto_blog_postting (AutoTistory)

티스토리 글을 **자동으로 작성/업로드**하기 위한 개인용 자동화 프로젝트입니다.  
현재 사용 불가한 코드입니다.

---

## 프로젝트 구성

- `AutoTistroyMain.py` : 메인 실행 파일
- `AutoTistorySetting.py` : 설정/환경 세팅 관련
- `requirements.txt` 
- `AutoTistroyMain.spec`, `AutoTistorySetting.spec` : PyInstaller 빌드 스펙
- `setting/`, `data/`, `hooks/` : 실행/빌드 시 사용하는 리소스 폴더
- `dist/`, `build/` : 빌드 산출물(생성됨)

---

## 준비물

- Python 3.x
- Windows 환경(권장)  
  (브라우저 자동화/GUI 자동화가 포함된 형태일 가능성이 높아 OS 영향이 큽니다.)

---

## 설치

### 1) 가상환경 생성/활성화

```bash
# 가상환경 생성
python -m venv venv

# (Windows) 가상환경 활성화
venv\Scripts\activate

# (macOS/Linux) 가상환경 활성화
source venv/bin/activate

# 가상환경 비활성화
deactivate
```

### 2) 의존성 설치

```bash
pip install -r requirements.txt
```

---

## 실행

> 레포에 메인 파일이 `AutoTistroyMain.py`로 포함되어 있습니다.

```bash
python AutoTistroyMain.py
```

설정만 따로 실행/테스트하려면(구성에 따라):

```bash
python AutoTistorySetting.py
```

---

## 설정(가이드)

레포에 `setting/` 폴더가 존재합니다.
구체 설정 파일명/형식은 프로젝트 구현에 따라 다를 수 있으니, 아래처럼 정리해두고 사용하면 관리가 편합니다.

권장 형태(예시):

- `setting/config.json`
  - 티스토리 계정/토큰(또는 쿠키) 정보
  - 글 카테고리/태그 기본값
  - 업로드/대기 시간(랜덤 딜레이) 등
- `data/`
  - 업로드할 글 원본(템플릿/소스)
  - 업로드 성공/실패 로그
- `hooks/`
  - PyInstaller 빌드 훅 또는 자동화 훅

---

## 빌드 (PyInstaller)

레포에 `.spec` 파일이 포함되어 있으므로, 아래처럼 빌드할 수 있습니다. 
```bash
pip install pyinstaller
pyinstaller AutoTistroyMain.spec
```

빌드 결과물은 일반적으로 `dist/`에 생성됩니다.
