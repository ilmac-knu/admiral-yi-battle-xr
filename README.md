# 이순신 장군의 바다 XR 체험

**저장소:** `ilmac-knu/admiral-yi-battle-xr`  
**목표:** 스마트폰에서 책상·바닥 위에 가상의 바다를 배치하고, 이순신 장군이 탑승한 판옥선이 접근하는 역사 교육용 XR 콘텐츠를 구현합니다. PC에서는 일반 3D 체험을 제공합니다.

## 실행 주소

- XR 체험: https://ilmac-knu.github.io/admiral-yi-battle-xr/
- 이 저장소: https://github.com/ilmac-knu/admiral-yi-battle-xr

> 저장소 생성 및 GitHub Pages 배포가 완료되어야 실행 주소가 작동합니다.

## 파일 구성

```text
admiral-yi-battle-xr/
├── index.html   # 3D 바다·판옥선 접근 애니메이션 및 AR 체험
└── README.md    # 사용법·외부 GLB 의존성·관리 주의사항
```

**중요:** 이 저장소에는 `.glb` 파일 두 개를 별도로 보관하지 않습니다. `index.html`이 아래 **기존 저장소의 GitHub Pages 주소**에서 불러옵니다.

## 외부 3D 모델 참조 위치

| 모델 | 파일명 | 실제 보관 저장소 | 로딩 URL |
|---|---|---|---|
| 판옥선 | `Sketchfab_panokseon.glb` | `ilmac-knu/admiral-yi-history-xr` | https://ilmac-knu.github.io/admiral-yi-history-xr/Sketchfab_panokseon.glb |
| 이순신 장군 | `admiral-yi-sunsin.glb` | `ilmac-knu/admiral-yi-history-xr` | https://ilmac-knu.github.io/admiral-yi-history-xr/admiral-yi-sunsin.glb |

기존 저장소: https://github.com/ilmac-knu/admiral-yi-history-xr

### 이렇게 구성한 이유

- `Sketchfab_panokseon.glb`는 약 **27MB**여서 GitHub 웹의 일반 파일 업로드 제한(25MB)에 걸립니다.
- 이전에 **Git Bash로 기존 저장소에 업로드**했으므로, 동일한 대용량 파일을 새 저장소에 중복 업로드하지 않고 재사용합니다.
- 저장소 용량과 파일 관리의 중복을 줄입니다.

### `index.html`에서 참조하는 방식

다음과 같은 URL 상수 또는 이에 해당하는 모델 로딩 코드가 있어야 합니다.

```javascript
const PANOKSEON_URL =
  'https://ilmac-knu.github.io/admiral-yi-history-xr/Sketchfab_panokseon.glb';
const ADMIRAL_URL =
  'https://ilmac-knu.github.io/admiral-yi-history-xr/admiral-yi-sunsin.glb';
```

> **주의:** 위 코드는 참조 위치를 설명하는 예시입니다. 실제 `index.html`의 변수명은 다를 수 있습니다. 파일을 수정할 때는 URL 문자열을 검색하여 확인하십시오.

## 유지보수 주의사항

1. **기존 `admiral-yi-history-xr` 저장소와 GitHub Pages를 삭제하거나 비공개로 전환하지 마십시오.** 새 콘텐츠가 GLB를 불러오지 못할 수 있습니다.
2. 기존 저장소의 GLB **파일명(대소문자 포함)**과 경로를 변경하면 새 `index.html`의 URL도 함께 수정해야 합니다.
3. 기존 GitHub 계정 또는 Pages 도메인을 이전하면 새 URL로 교체하고 정상 로딩 여부를 확인하십시오.
4. GitHub Pages의 배포 설정과 브라우저 개발자 도구(Network/Console)에서 GLB 로딩 오류(예: 404, CORS)를 점검하십시오.
5. 판옥선 모델은 제3자 제작물일 수 있으므로, **원본 Sketchfab 모델의 라이선스·저작자 표시 의무를 확인**하고 배포·출판 시 준수하십시오. 이 README는 사용 허가를 대신하지 않습니다.

## 사용 및 테스트

1. PC: 체험 페이지에서 일반 3D 장면과 판옥선 접근 애니메이션을 확인합니다.
2. 스마트폰: HTTPS로 접속한 후 카메라 AR 시작 기능을 실행합니다(지원 기기·브라우저 필요).
3. 책상이나 바닥을 인식하고 바다를 배치합니다.
4. 판옥선과 장군이 표시되는지 확인합니다. AR을 지원하지 않는 환경에서는 일반 3D 체험을 이용합니다.

## 향후 확장 계획

- 적선 모델 추가
- 포격·포연·물보라 효과
- 역사 해설 및 승리 장면

현재는 **바다와 판옥선 접근을 검증하는 1차 버전**이며, 역사적 전투 장면의 완성본은 아닙니다.
