# Claude 자동화 지침

**새 세션을 시작할 때 이 파일을 먼저 읽으세요.**

## 자동 수행 작업

### 1. 파일 수정 시 자동 Git 작업
모든 파일 수정 후 다음을 자동으로 수행:
```bash
git add .
git commit -m "설명적인 커밋 메시지"
git push
```

### 2. Version 업데이트
파일 수정 시 `index.html`의 version을 자동으로 증가:
- **위치**: index.html 522번, 688번 라인
- **현재 버전**: v1.7.0
- **형식**: `v{major}.{minor}.{patch}`
- **규칙**:
  - 작은 수정/버그 픽스: patch 증가 (v1.5.0 → v1.5.1)
  - 새로운 기능 추가: minor 증가 (v1.5.0 → v1.6.0)
  - 대규모 변경: major 증가 (v1.5.0 → v2.0.0)

### 3. 업데이트할 version 라인
```html
<!-- 라인 522 -->
<span class="version-badge" style="position: absolute; top: 0; right: 0;">v1.7.0</span>

<!-- 라인 688 -->
<span class="version-badge">v1.7.0</span>
```

## 워크플로우 예시

1. 사용자가 파일 수정 요청
2. 파일 수정 수행
3. version 자동 증가 (index.html 두 곳)
4. git add .
5. git commit -m "설명적인 메시지"
6. git push

## 주의사항
- 모든 수정은 version 업데이트를 포함
- commit 메시지는 변경 내용을 명확히 설명
- push 전 commit 성공 여부 확인
