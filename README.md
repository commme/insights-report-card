# 🎓 Claude Code 성적표 생성기

> Claude Code의 Insights 리포트를 읽어, 한 달 사용 내역을 **5과목 성적표** HTML로 자동 생성하는 프롬프트

![preview](assets/preview-placeholder.png)

---

## ✨ 무엇인가요?

Claude Code가 자동 생성하는 `~/.claude/usage-data/report.html` 파일을 분석해,  
아래 5개 과목으로 점수를 산출하고 **1280×980 성적표 카드**를 만들어줍니다.

| 과목 | 측정 기준 |
|------|----------|
| 🔥 활용력 | 총 시간 ÷ (활동일 × 5) |
| 🎨 다양성 | 프로젝트 영역 수 × 20 |
| 🚀 완성도 | (Fully + Mostly) ÷ 전체 결과 |
| 💬 소통력 | 긍정 만족도 응답 비율 |
| 💡 창의성 | 총 세션 수 기반 |

등급: **A+ ≥ 90 / A ≥ 80 / B+ ≥ 70 / B ≥ 60 / C ≥ 50 / D < 50**

---

## 🚀 사용법 (3단계)

### 0. 사전 준비

Claude Code의 Insights 리포트가 필요합니다.

```
# Claude Code에서 실행 (CC v2.1.0+)
/insights
```

생성된 파일 확인:
```
~/.claude/usage-data/report.html
```

> 파일이 없으면 Claude Code를 더 사용한 뒤 다시 시도하세요.

### 1. 프롬프트 복사

`prompt-final.md` 파일을 열어 코드 블록 안의 내용을 전체 복사합니다.

### 2. Claude Code에 붙여넣기

Claude Code (Sonnet 이상 권장) 채팅창에 붙여넣기 → 전송

### 3. 완성

`~/.claude/usage-data/report-card-YYYYMMDD.html` 파일이 생성되고 브라우저가 자동으로 열립니다.

---

## 📁 파일 구조

```
insights-report-card/
├── README.md              ← 이 파일
├── prompt-final.md        ← Claude Code에 붙여넣는 프롬프트
├── assets/
│   └── claude-pixel-mascot.svg   ← 마스코트 아이콘
├── report-card-sample.html        ← 생성 결과 샘플
└── LICENSE
```

---

## ⚠️ 한계

- 온라인 환경 필요 (Pretendard 폰트, Iconify 아이콘 CDN 사용)
- `report.html`이 없으면 실행 불가 (Claude Code Insights 먼저 생성)
- 점수는 참고용 지표 — 재미로 보는 성적표입니다 😄

---

## 🙏 크레딧

- 디자인 템플릿: [Gist v16-final](https://gist.github.com/commme/910c3c0538979a3e2ffcc73f39d9bd2e)
- 폰트: [Pretendard](https://github.com/orioncactus/pretendard) (OFL-1.1)
- 아이콘: [Phosphor Icons](https://phosphoricons.com/) via [Iconify](https://iconify.design/)
- 마스코트: Claude pixel mascot

---

© 2026 COMMME · Built with Claude Code · [MIT License](LICENSE)
