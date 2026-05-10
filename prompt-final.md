# 🎓 Claude Code 성적표 프롬프트 (v3 — Gist 템플릿 + 값 교체)

아래를 Claude Code에 그대로 붙여넣기. Sonnet이면 충분.

---

```
내 Claude Code 한 달 성적표를 만들어줘.

## 규칙
1. Read: ~/.claude/usage-data/report.html (데이터)
2. WebFetch: https://gist.githubusercontent.com/commme/910c3c0538979a3e2ffcc73f39d9bd2e/raw/v16-final.html (템플릿)
3. 템플릿의 {{플레이스홀더}}를 실제 데이터로 교체해서 Write
4. 저장 후 브라우저 열기
5. 도구 총 4회 이내. 개별 JSON 읽기 금지.

## report.html에서 추출할 데이터
- 총 세션: subtitle "N total"
- 시간: section-wins "N hours"
- 활동일: stat-value "Days"
- 프로젝트 영역: .project-area 개수
- 도구 종류: "Top Tools Used" 차트 항목 개수
- 언어 종류: "Languages" 차트 항목 개수
- Outcomes: "Outcomes" 차트 bar-value (Fully/Mostly/Partially/Not/Unclear)
- Satisfaction: "Inferred Satisfaction" 차트 bar-value
- 잘한점: .big-win-title + .big-win-desc (최대 3개)
- 마찰점: .friction-title + .friction-desc (최대 3개)

## 점수 공식
- 활용력 = min(100, 총시간 ÷ (활동일×5) × 100)
- 다양성 = min(100, 프로젝트영역수 × 20)
- 완성도 = (Fully+Mostly) ÷ (전체−Unclear) × 100
- 소통력 = (Satisfied+Likely Satisfied+Happy) ÷ 전체Satisfaction × 100
- 창의성 = min(100, 도구종류 × 10 + 언어종류 × 8)
- 종합 = 5과목 평균(반올림). 등급: A+≥90 A≥80 B+≥70 B≥60 C≥50 D<50
- 등급 CSS class: A+=gr-Aplus, A=gr-A, B+=gr-Bplus, B이하=gr-B

## 템플릿 플레이스홀더 교체표
| 플레이스홀더 | 값 |
|------------|-----|
| {{PERIOD}} | report.html subtitle 날짜 범위 |
| {{STUDENT}} | [YOUR_NAME] |
| {{SESSIONS}} | 총 세션 수 |
| {{HOURS}} | 총 시간 |
| {{TOTAL_SCORE}} | 종합 점수 |
| {{TOTAL_GRADE}} | 종합 등급 |
| {{VERDICT}} | 데이터 기반 한줄평 (예: "N개 영역을 넘나들며 꾸준히 성장한 학생") |
| {{S1_SCORE}}~{{S5_SCORE}} | 각 과목 점수 |
| {{S1_GRADE}}~{{S5_GRADE}} | 각 과목 등급 텍스트 |
| {{S1_GR}}~{{S5_GR}} | 등급 CSS class (gr-Aplus 등) |
| {{STRENGTHS}} | 잘한점 3개 HTML (아래 포맷) |
| {{IMP_COUNT}} | 개선점 개수 |
| {{IMPROVEMENTS}} | 개선점 5~7개 HTML (아래 포맷) |
| {{HOME_PATH}} | OS 홈 경로 (C:/Users/이름 또는 /Users/이름) |
| {{TEACHER_COMMENT}} | 교사소견 HTML |

## 잘한점 HTML 포맷 ({{STRENGTHS}} 자리)
<div class="strength">
  <img src="https://api.iconify.design/ph/[아이콘]-duotone.svg?color=%235C8A5E" alt="">
  <div class="strength-text">
    <div class="observation">제목 <span class="pattern">(패턴)</span></div>
    <div class="action">실천 제안</div>
  </div>
</div>

## 개선점 HTML 포맷 ({{IMPROVEMENTS}} 자리)
<div class="imp">
  <div class="imp-num">N</div>
  <div class="imp-content">
    <div class="imp-title">
      <span class="cat-badge cat-[카테고리]">[BADGE]</span>
      제목 <span class="pattern">friction 근거</span>
    </div>
    <div class="imp-action">실행 액션 (코드나 설정 포함)</div>
  </div>
</div>
카테고리 뱃지: AGENT/SKILL/HOOK/MCP/CLAUDE.md/PROJECT/OUTPUT STYLE

## 교사소견 포맷
<strong>핵심키워드</strong> + 시간/성과 언급 + 유머 한줄.
예: <strong>다재다능</strong>하고 끝까지 끌고 가는 학생. <strong>N시간</strong> 한 학기 수고 많았고, <strong>에피소드</strong>는 잊지 못할 추억.

## 저장
~/.claude/usage-data/report-card-YYYYMMDD.html (오늘 날짜)
저장 후 기본 브라우저로 열기.
```
