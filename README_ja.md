# Agent Skill Toolkit — 日本語版

構造化された思考、委譲、要件調整、レビュー、検証を行うための、再利用可能なConditional Skill集。

この配布版は、特定のRouting / Orchestration実装を**意図的に規定しない**。個別Skillを単独で使うことも、既存のAgent、Orchestrator、System Promptなどの利用環境へ組み込むこともできる。

## 設計原則

> 役割認識、Authority、Scope、Routingは利用環境側に置く。再利用可能なMethod / Policyは、その仕事が実際に必要になったときだけ読む。

ユーザー、利用環境、またはRouting / Orchestration LayerによってAuthority、Scope、Role、Constraintがすでに定義されている場合はそれを優先する。明示的な定義がない場合は、現在のTask Contextを作業上のBoundaryとして扱う。

目的はSkill数を減らすことではない。
目的は、責務を明確かつ再利用可能に保ちながら、**常時ロードされるContextを最小化すること**である。

## 収録Skill

### Governance Policies

- `delegation-context-policy` — Agent境界、Task Packet、Context継承、継続利用、統合責任。
- `requirement-alignment-gate` — Requirement Authority、Proposal、User Alignment、下流へのPropagation境界。
- `review-cycle-policy` — 条件付き独立Review、Adjudication、Correction、Re-review。

### Thinking Methods

- `requirements-specification` — 承認済みIntentを観測可能なRequirement、Constraint、Non-goal、Acceptance Criteria、Open Questionへ落とす。
- `solution-design` — 重要な構造、Boundary、Interface、State Ownership、Trade-offを選ぶ。
- `planning` — Dependency、不確実性、Checkpoint、Parallelism、実行可能単位に基づいて作業順序を決める。
- `research` — Provenance、Freshness、矛盾処理を含め、Sourceから信頼できるFactを確立する。
- `analysis` — Comparison、Normalization、Alternative Explanation、Robustness、Quantitative ReasoningによってEvidenceを解釈する。
- `synthesis-decision` — EvidenceとConstraintをRecommendation / Decisionへ統合する。ただしDecision Authority自体は追加しない。
- `evaluation-verification` — Success / Failureを区別するEvidenceを設計し、Evidenceの強さに合わせてClaimを調整する。
- `problem-solving` — Evidence、Hypothesis、Information Gain、Method変更、Minimum Sufficient Interventionによって不確実性を減らす。
- `debugging` — Reproduction、Runtime Evidence、Discriminating Observation、Root Cause、Regression Verificationで原因不明のSoftware Failureを診断する。

## 概念上のWorkflow

すべての工程が必要な場合、Methodは次のように組み合わせられる。

`Intent → Requirements → Design → Planning → Research → Analysis → Synthesis / Decision → Execution → Evaluation / Verification → Output`

ただしこれは**必須チェックリストではない**。
すでに確定している、単純である、または無関係な工程は飛ばす。

`problem-solving` と `debugging` は横断Methodであり、不確実性やSoftware Failureが現れた場所へ必要に応じて差し込む。

## Governance と Method の分離

重要な原則：

> **Method SkillをロードしてもAuthorityは増えない。**

例：

- `requirements-specification` はProposalを整理できるが承認はできない。
- `solution-design` はより良いBehaviorを発見しても勝手にRequirement化できない。
- `research` が新Factを確立しても、それだけでRequirement Authorityは発生しない。
- `synthesis-decision` はRecommendationを出せるが、User-owned Decisionを代行できない。
- `evaluation-verification` はEvidence不足を指摘できるが、AuthorityなしにAcceptance Criteriaを変更できない。

Authority / Agent境界にはGovernance Policyを使い、Reasoning ProcedureにはThinking Methodを使う。

## 組み込み方

任意のRouting / Orchestration Layerには、**Skillが必要だと判断できる最小限のRouting条件だけ**を持たせる。

例：

- Agent委譲・Context移送 → `delegation-context-policy`
- User-visible Requirementが未決定 → `requirement-alignment-gate`
- 独立したAssuranceに実質的価値がある → `review-cycle-policy`
- 承認済みIntentが実行可能な粒度まで具体化されていない → `requirements-specification`
- 重要な構造選択がある → `solution-design`
- Dependencyや作業順序が非自明 → `planning`
- Source-sensitive Factが不足 → `research`
- Evidenceはあるが比較・解釈が必要 → `analysis`
- FindingをRecommendationへまとめる必要がある → `synthesis-decision`
- Completion Evidenceが自明でない → `evaluation-verification`
- 不確実性自体が進行を止めている → `problem-solving`
- Software Behaviorが誤っていて原因が不明 → `debugging`

最小構成例は `docs/ROUTING_ORCHESTRATION_EXAMPLE.md` を参照。

## Anti-Overengineering Rule

概念上のWorkflowで次の箱にあるという理由だけでSkillをロードしない。

そのSkill固有の責務が実際に存在するときだけ使う。

新しいSkillも、単に名前を付けられるという理由だけで増やさない。原則として以下を満たす場合に独立Skill化する。

1. 外から独立して認識可能なTriggerがある。
2. そのTrigger以外では不要となる十分な内容がある。
3. Circular LoadingなしにResponsibility Boundaryを説明できる。
4. 明示的なDomain Skillでない限り、狭い1ケースを超えて再利用価値がある。
5. Routing Decisionを1つ増やすコストに見合うBehavioral Valueがある。

## Directory Layout

```text
skills/
  delegation-context-policy/
  requirement-alignment-gate/
  review-cycle-policy/
  requirements-specification/
  solution-design/
  planning/
  research/
  analysis/
  synthesis-decision/
  evaluation-verification/
  problem-solving/
  debugging/

docs/
  ROUTING_ORCHESTRATION_EXAMPLE.md
  ROUTING_SMOKE_TESTS.md
```

## 配布版に含めないもの

このPackageは次を規定しない。

- 特定のModel / Vendor
- 特定のDecision Owner / Execution Owner構成
- Multi-agent必須のTopology
- 特定Runtime / Skill Loader
- 万能なAuthority Model
- 全Skillの自動発火

RoutingとAuthorityは利用環境に合わせて設定する。

## Platform固有の補足

Skill本体はプラットフォーム非依存です。ランタイム固有の設定値や対応付けは `docs/platform-notes/` に分離しています。

- `docs/platform-notes/codex.md` — Codex固有のContext継承設定（例: `fork_turns`）との対応表。


## ライセンス

MIT Licenseです。詳細は [`LICENSE`](LICENSE) を参照してください。
