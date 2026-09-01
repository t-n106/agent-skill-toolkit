# Routing Smoke Tests

Routingルールを変更した後の軽量チェックとして使用します。目的はタスクそのものを解くことではなく、不要なSkillを追加せず、期待したSkill群が選択されることを確認することです。

| シナリオ | 期待するSkill | 通常は避ける |
|---|---|---|
| 境界の明確な1タスクを新規Execution Agentへ委譲する | `delegation-context-policy` | 独立性が必要でないreview |
| 承認済み挙動はあるがacceptance criteriaが曖昧 | `requirements-specification` | 実際にユーザー判断が未解決でない限りalignment |
| 外部から見える2つの挙動のどちらを採用するかユーザー判断が必要 | `requirement-alignment-gate` | design/planningで勝手に決めること |
| 2つの妥当なmodule boundaryに意味のあるtrade-offがある | `solution-design` | 外部事実が不足していない限りresearch |
| 既知の5タスクに実際の依存関係とcheckpoint制約がある | `planning` | 構造が確定済みならdesign |
| 現在のprovider/API挙動を情報源から確定する必要がある | `research` | 証拠が揃う前のsynthesis |
| 収集済み証拠を正規化して比較する必要がある | `analysis` | 重要な証拠不足が残っていない限り追加research |
| 複数のfindingsを注意事項付きの1つの推奨へまとめる | `synthesis-decision` | 現在のauthorityを越えた意思決定 |
| 結果は完成して見えるが、失敗証拠の確認が自明ではない | `evaluation-verification` | 価値がないのに自動的に独立review |
| 複数の妥当な説明があり、非自明な不確実性が残る | `problem-solving` | ソフトウェア障害でない限りdebugging |
| 再現可能なソフトウェア不具合だが原因が不明 | `debugging`、必要に応じて `problem-solving` | 不具合が要件・設計問題を露呈していない限りrequirements/design |
| self-verification後の高影響な統合変更 | `review-cycle-policy`、reviewerは必要に応じて `evaluation-verification` | 修正のたびに自動re-review |

良いRouting Systemは、明白・低リスク・直接実行可能な作業ではMethodをロードしないことも重要です。

## Task Boundary互換性チェック

| シナリオ | 期待するBoundary動作 |
|---|---|
| Orchestration LayerなしでSkillを直接利用 | User / HostのTask Contextを作業Boundaryとして使い、追加Authorityを勝手に作らない |
| Host側Persona / RoleがScopeやConstraintを定義済み | そのRole、Scope、Constraintを維持したままSkillを適用する |
| Routing / Orchestration LayerがAuthorityやStop Conditionを定義済み | 既存Boundaryに従い、ロードされたSkillが上書きしない |
| Role / Authority / Scopeが明示されていない | 現在のTaskから必要最小限の作業Boundaryだけを扱い、Methodを理由にScopeを拡大しない |
