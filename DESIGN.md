# DESIGN.md — 디자인 시스템 규칙

> 출처: KOSME 중소벤처기업진흥공단 디지털지점(https://digital.kosmes.or.kr/dh/map/main.do) 실제 렌더링 CSS 분석
> 분석일: 2026-09-10 · 방식: 브라우저 `getComputedStyle()`로 실측 (추측 아님)
>
> **이후 이 프로젝트에서 만드는 모든 페이지·컴포넌트는 이 문서의 토큰과 규칙을 따른다.** 임의의 색상·간격·폰트 크기를 새로 만들지 말고 아래 토큰을 참조한다.

---

## 1. 컬러 (Color)

### 1.1 브랜드 / 주요 컬러

| 토큰 | Hex | 용도 |
|---|---|---|
| `--color-primary` | `#003994` | 브랜드 네이비. 라벨·강조 텍스트, 섹션 아이콘 배경 |
| `--color-primary-deep` | `#023894` | Primary와 거의 동일한 딥네이비. 카드 섹션 배경(예: 아이콘 6개 카드 묶음 배경) |
| `--color-accent` | `#2F6DF6` | 인터랙티브 블루. 주요 CTA 버튼, 링크, 포커스 강조 |
| `--color-accent-mid` | `#3475D3` | 컬러 액션 카드 배경(중간 톤) |
| `--color-secondary` | `#653DD6` | 보조 카테고리 컬러(퍼플). 다른 성격의 액션 카드 구분용 |

### 1.2 시맨틱 컬러

| 토큰 | Hex | 용도 |
|---|---|---|
| `--color-danger` | `#E40000` | 긴급/필독 배지, 경고 라벨 |
| `--color-success` | `#1F6E4C` *(사이트에 명시적 성공색 없음 — 임의 지정 시 이 값 사용 권장)* | 완료/성공 상태 |

### 1.3 텍스트 컬러

| 토큰 | Hex | 용도 |
|---|---|---|
| `--text-primary` | `#303030` | 본문 기본 텍스트 (가장 많이 쓰이는 색) |
| `--text-secondary` | `#333333` | 보조 텍스트 |
| `--text-tertiary` | `#373737` | 부가 설명 텍스트 |
| `--text-muted` | `#767676` | 캡션, 타임스탬프, 비활성 텍스트 |
| `--text-inverse` | `#FFFFFF` | 어두운/컬러 배경 위 텍스트 |

### 1.4 배경 / 표면

| 토큰 | Hex | 용도 |
|---|---|---|
| `--bg-page` | `#FFFFFF` | 기본 페이지 배경 |
| `--bg-header` | `#FFFFFF` | 헤더 배경 (하단에 옅은 그림자로 구분) |
| `--bg-utility` | `#292929` | 최상단 유틸리티 바(로그인/회원가입 등) 배경 |
| `--bg-tint-blue` | `#EAF1FB` | 옅은 블루 틴트. 보조 버튼/배지 배경 |
| `--bg-tint-blue-2` | `#F0F8FF` | 더 옅은 블루 틴트. 섹션 구분 배경 |
| `--bg-tint-mint` | `#F5FFFF` | 신뢰 배지 영역 등 특수 섹션 배경 |
| `--bg-hero` | `#477FE1` | 히어로 배너 배경(그라디언트의 대표값). 실제로는 짙은 남색→밝은 블루 대각선 그라디언트 |

### 1.5 경계선 / 중립

| 토큰 | Hex | 용도 |
|---|---|---|
| `--border-default` | `#DDDDDD` | 기본 구분선 |
| `--border-light` | `#ECECEC` | 옅은 구분선 |
| `--border-mid` | `#D8D8D8` | 중간 톤 구분선 |
| `--neutral-900` | `#111827` | 유틸리티성 다크 그레이(일부 컴포넌트) |
| `--neutral-700` | `#374151` | 유틸리티성 그레이 |

### 1.6 사용 규칙
- 배경이 흰색인 카드/섹션의 본문 텍스트는 반드시 `--text-primary`(`#303030`) 사용, 순수 검정(`#000`) 금지.
- 강조 CTA 버튼은 `--color-accent`(`#2F6DF6`) 계열만 사용하고, `--color-primary`(딥네이비)는 섹션 배경·라벨에만 사용해 위계를 분리한다.
- 퍼플(`--color-secondary`)은 "다른 성격의 액션"을 시각적으로 구분할 때만 예외적으로 쓴다 (남발 금지, 페이지당 1곳 이내 권장).

---

## 2. 타이포그래피 (Typography)

### 2.1 폰트 패밀리
```
font-family: "Noto Sans KR", "Nanum Gothic", sans-serif, arial;
```
전 사이트에 걸쳐 단일 폰트 패밀리만 사용 (제목/본문 구분 없이 굵기로만 위계를 만듦).

### 2.2 타입 스케일

실측값은 사이트의 `1rem = 7.2px` 기반 rem 스케일에서 나온 것이며, 아래 표는 실제 렌더링 픽셀값을 반올림한 것이다.

| 토큰 | 크기 | 굵기 | 행간 | 용도 |
|---|---|---|---|---|
| `--text-hero` | 35px | 100 (Thin) | ~1.08 | 히어로 대제목 (예: "고객을 위한 디지털 플랫폼!") |
| `--text-h1` | 35px | 300 (Light) | ~1.08 | 섹션 대제목 (예: "정책자금 온라인신청") — 히어로와 같은 크기지만 더 두꺼운 굵기로 구분 |
| `--text-h1-alt` | 35px | 500 (Medium) | ~1.08 | 페이지 본문 섹션 제목 (예: "부가서비스") |
| `--text-h2` | 19px | 700 (Bold) | 1.2 | 모달/팝업 타이틀 |
| `--text-h3` | 17px | 700 (Bold) | 1.33 | 카드 제목, 서브 내비게이션 제목 |
| `--text-label` | 14px | 500 (Medium) | 1.0 | 이터리언트 라벨 (예: "2026 정책자금"), `--color-primary` 색상과 함께 사용 |
| `--text-body` | 13px | 400 (Regular) | 1.78 | 기본 본문 텍스트 — 행간이 매우 넉넉함(가독성 우선) |
| `--text-caption` | 11–12px | 400 (Regular) | 1.2 | 캡션, 버튼 라벨, 보조 안내문 |

### 2.3 사용 규칙
- 제목은 크기보다 **굵기**로 위계를 만드는 것이 이 시스템의 핵심 특징이다 — 같은 35px에서 Thin(히어로) → Light(섹션) → Medium(본문 섹션)으로 문맥에 따라 굵기만 바뀐다. 새 페이지를 만들 때도 이 원칙(굵기 기반 위계)을 유지한다.
- 본문 텍스트의 줄간격은 폰트 크기의 **약 1.7~1.8배**로 넉넉하게 — 한글 가독성을 위해 압축하지 않는다.
- 강조가 필요한 짧은 라벨(뱃지, 태그성 텍스트)에는 `--text-label`(14px/500/`--color-primary`)을 쓴다.

---

## 3. 간격 시스템 (Spacing)

실측 padding/margin 값을 정리하면 아래와 같은 스케일을 따른다 (완전한 4px/8px 그리드는 아니고, 사이트 고유의 넉넉한 간격 체계):

| 토큰 | 값 | 용도 |
|---|---|---|
| `--space-1` | 8px | 아이콘-텍스트 사이 최소 간격 |
| `--space-2` | 11px | 소형 카드 내부 패딩 |
| `--space-3` | 16px | 카드 내부 기본 패딩(세로) |
| `--space-4` | 17px | 사이드 메뉴 항목 패딩 |
| `--space-5` | 22px | 카드 내부 패딩(가로), 섹션 간 기본 갭 |
| `--space-6` | 29px | 카드 내부 패딩(세로, 넉넉한 카드) |
| `--space-7` | 32px | 컬러 액션 카드 세로 패딩 |

### 3.1 레이아웃 매크로 스페이싱
- 헤더 높이: **58px** (흰 배경 + `box-shadow: 0 7px 10px rgba(0,0,0,.05)`로 하단 구분, 보더 없음)
- 최상단 유틸리티 바: 진한 그레이(`#292929`) 배경, 폰트 12px
- 콘텐츠 컨테이너 폭: **1275px** 고정 (반응형 브레이크포인트는 별도 확인 필요 — 고정폭 기반 레거시 그리드)

### 3.2 사용 규칙
- 카드류 컴포넌트는 항상 **가로 패딩 > 세로 패딩보다 여유 있게** 또는 22px/29px 조합을 기본값으로 쓴다 (콘텐츠가 좁고 답답해 보이지 않도록).
- 섹션과 섹션 사이는 시각적 구분을 배경색 전환(흰색 ↔ 옅은 회색/블루 틴트)으로 만들고, margin만으로 구분하지 않는다.

---

## 4. 모서리 둥글기 (Border Radius)

| 토큰 | 값 | 용도 |
|---|---|---|
| `--radius-sm` | 5px | 소형 필/버튼 (예: 로그인 버튼) |
| `--radius-md` | 9px | **기본값.** 카드, 일반 버튼 대부분 |
| `--radius-lg` | 12px | 알림/공지 카드(흰 배경, 그림자 강조형) |

→ 특별한 이유가 없으면 **9px(`--radius-md`)를 기본 모서리값**으로 사용한다.

---

## 5. 그림자 / 입체감 (Elevation)

| 토큰 | 값 | 용도 |
|---|---|---|
| `--shadow-header` | `0 7px 10px rgba(0,0,0,.05)` | 헤더 하단, 고정 바 |
| `--shadow-subtle` | `0 6px 6px rgba(0,0,0,.09)` | 흰 배경의 옅은 알림/공지 카드 |
| `--shadow-card` | `0 5px 5px rgba(0,0,0,.15)` | 흰 배경 기본 카드 (가장 흔한 카드 그림자) |
| `--shadow-strong` | `0 4px 4px rgba(0,0,0,.25)` | 컬러 배경(딥네이비) 섹션 내부 아이콘 카드 |
| `--shadow-colored-card` | `0 3px 8px rgba(0,0,0,.3)` | 컬러 배경 액션 카드(블루/퍼플) — 가장 진한 그림자, 클릭 유도용 |

→ **흰 배경 카드는 옅은 그림자, 컬러 배경 카드는 진한 그림자**를 쓰는 규칙이 일관되게 적용되어 있다 — 이 대비 규칙을 유지한다.

---

## 6. 컴포넌트 규격

### 6.1 헤더 / GNB
- 배경 흰색, 높이 58px, 보더 없이 `--shadow-header`로만 하단 분리
- 로고(좌) + 대형 드롭다운 GNB(중앙~우) + 유틸리티 아이콘(우) 구조
- 상단에 진회색(`#292929`) 유틸리티 바(로그인/회원가입/즐겨찾기) 별도 존재

### 6.2 버튼
| 종류 | 배경 | 텍스트 | 반경 | 그림자 | 예시 |
|---|---|---|---|---|---|
| Primary (컬러 액션 카드형) | `--color-accent`(#2F6DF6) 또는 `--color-accent-mid`(#3475D3) | 흰색 | 9px | `--shadow-colored-card` | "전자약정 바로가기" |
| Secondary (틴트) | `--bg-tint-blue`(#EAF1FB) | `--text-primary` | 9px | 없음 | "정책자금 애로상담 신청" |
| Pill (소형) | `--color-accent`(#256EF4 계열) | 흰색 | 5px | 없음 | "통합회원 로그인" |
| Ghost/Link | 투명 | `--text-primary` | — | hover 시 그림자 등장 `--shadow-card` | 목록형 메뉴 항목 |

- 모든 버튼/링크의 hover 전환은 **`transition: 0.2s`** — 새 컴포넌트도 이 지속시간을 기본값으로 쓴다.
- 커서는 `pointer`.

### 6.3 카드
두 가지 패턴이 명확히 구분된다:
1. **정보 카드 (흰 배경)**: `background:#fff`, `border-radius:9px`, `box-shadow:var(--shadow-card)`, padding `29px 22px` 내외. 공지/안내/일반 콘텐츠용.
2. **액션 카드 (컬러 배경)**: `background: var(--color-accent-mid)` 또는 `var(--color-secondary)`, 흰 텍스트, `border-radius:9px`, `box-shadow:var(--shadow-colored-card)`, padding `29px 8px` 내외, 세로 중앙 정렬. 클릭을 유도하는 CTA성 콘텐츠용.

### 6.4 네비게이션 (사이드/드롭다운)
- 대분류(H2, 17px/700) + 세부 링크 리스트 구조
- 세부 링크 리스트는 배경 없이 텍스트만, hover 시에만 시각 반응

---

## 7. 인터랙션 / 모션 원칙
- 전환 지속시간: **0.2s** (버튼, 링크 hover 공통)
- easing은 브라우저 기본값(별도 커스텀 큐빅베지어 미사용) — 새 컴포넌트도 과도한 easing 커스터마이징을 지양한다.
- 카드/버튼의 hover 반응은 색 변화보다 **그림자 강조** 위주 (컬러 액션 카드는 이미 그림자가 강하므로 hover 시 살짝 더 진하게/위로 떠오르는 효과 권장).

---

## 8. CSS 커스텀 프로퍼티 (그대로 복사해서 사용)

```css
:root{
  /* Color — Brand */
  --color-primary: #003994;
  --color-primary-deep: #023894;
  --color-accent: #2F6DF6;
  --color-accent-mid: #3475D3;
  --color-secondary: #653DD6;

  /* Color — Semantic */
  --color-danger: #E40000;
  --color-success: #1F6E4C;

  /* Color — Text */
  --text-primary: #303030;
  --text-secondary: #333333;
  --text-tertiary: #373737;
  --text-muted: #767676;
  --text-inverse: #FFFFFF;

  /* Color — Background */
  --bg-page: #FFFFFF;
  --bg-header: #FFFFFF;
  --bg-utility: #292929;
  --bg-tint-blue: #EAF1FB;
  --bg-tint-blue-2: #F0F8FF;
  --bg-tint-mint: #F5FFFF;
  --bg-hero: #477FE1;

  /* Color — Border */
  --border-default: #DDDDDD;
  --border-light: #ECECEC;
  --border-mid: #D8D8D8;

  /* Typography */
  --font-family: "Noto Sans KR", "Nanum Gothic", sans-serif, arial;
  --text-hero: 35px;
  --text-h2: 19px;
  --text-h3: 17px;
  --text-label: 14px;
  --text-body: 13px;
  --text-caption: 12px;

  /* Spacing */
  --space-1: 8px;
  --space-2: 11px;
  --space-3: 16px;
  --space-4: 17px;
  --space-5: 22px;
  --space-6: 29px;
  --space-7: 32px;

  /* Radius */
  --radius-sm: 5px;
  --radius-md: 9px;
  --radius-lg: 12px;

  /* Shadow */
  --shadow-header: 0 7px 10px rgba(0,0,0,.05);
  --shadow-subtle: 0 6px 6px rgba(0,0,0,.09);
  --shadow-card: 0 5px 5px rgba(0,0,0,.15);
  --shadow-strong: 0 4px 4px rgba(0,0,0,.25);
  --shadow-colored-card: 0 3px 8px rgba(0,0,0,.3);

  /* Motion */
  --transition-default: 0.2s;
}
```

---

## 9. 적용 지침 (필수 준수)

1. 이 프로젝트에서 이후 만드는 **모든 HTML/CSS는 위 CSS 커스텀 프로퍼티를 `:root`에 포함**하고, 색상·크기·간격·반경·그림자 값은 반드시 토큰을 참조한다 (하드코딩된 임의의 hex/px 금지).
2. 제목 위계는 **크기보다 굵기 우선** 원칙을 따른다 (§2.3).
3. 흰 배경 카드는 옅은 그림자, 컬러 배경 카드는 진한 그림자 — 이 대비를 항상 유지한다 (§5).
4. 버튼 기본 반경은 9px, hover 전환은 0.2s.
5. 본문 텍스트 줄간격은 폰트 크기의 1.7~1.8배로 넉넉하게.
6. 퍼플(`--color-secondary`)은 카테고리 구분이 명확히 필요할 때만 제한적으로 사용.

> 기존에 이 프로젝트에서 만든 "사업자 지원금 레이더" 3개 화면(지원금 스캐너/IoT 관리 콘솔/가이드북)은 다크 테마(네이비+시그널그린) 브랜드를 쓰고 있어 이 라이트 테마 시스템과 다르다. 앞으로 새로 만드는 페이지에 이 DESIGN.md를 적용할지, 기존 3개 화면도 이 라이트 테마로 다시 맞출지는 별도로 확인이 필요하다.
