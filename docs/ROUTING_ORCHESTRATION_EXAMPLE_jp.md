# 最小 Routing / Orchestration 例

このToolkitは、特定のRouting / Orchestration Architectureを規定しません。Skillを直接呼び出して使うことも、利用環境側に薄いRouting / Orchestration Layerを置いて、条件付きSkillが必要な状況を判定させることもできます。

## Task Boundaryのフォールバック

ユーザー、利用環境、またはRouting / Orchestration LayerによってAuthority、Scope、Role、Constraintがすでに定義されている場合はそれを優先する。明示的な定義がない場合は、現在のTask Contextを作業上のBoundaryとして扱う。

これにより、専用のRouting / Orchestration Layerがある場合でもない場合でも同じSkillを利用できる。Routing LayerはSkill選択には使えるが、単独利用時のTask Boundaryを成立させるために必須ではない。

## 最小ルール

> 実質的な作業に入る前に、各条件付きSkillのTriggerが現在の状況に該当するかを確認する。該当するSkillだけをロードし、Toolkit全体を既定でロードしない。

## Routing例

| 状況 | ロードするSkill |
|---|---|
| Agent境界を新規作成・再利用する、またはContextを引き渡す | `delegation-context-policy` |
| 製品意図、ユーザーに見える挙動、要件承認が未解決 | `requirement-alignment-gate` |
| 独立Reviewが検証上の実質的な価値を持つ | `review-cycle-policy` |
| 承認済みの意図が、実装・評価可能なほど具体化されていない | `requirements-specification` |
| 影響のある構造や境界について複数の妥当な案がある | `solution-design` |
| 依存関係、順序、Checkpoint、並列化に意味のある問題がある | `planning` |
| 情報源依存または最新性が重要な事実が不足している | `research` |
| Evidenceはあるが、比較・解釈・Robustness分析が必要 | `analysis` |
| FindingをRecommendationや選択へまとめる必要がある | `synthesis-decision` |
| 成功・失敗のEvidence、またはClaimの強さの評価が自明ではない | `evaluation-verification` |
| 重要な不確実性が残り、進むべき経路が明確でない | `problem-solving` |
| Software Behaviorが誤っており、原因が確定していない | `debugging` |

## 薄いRouting Layerの例

```text
役割、Authority、Scope、Stop Conditionは利用環境側に保持する。

実質的な作業に入る前に:
1. 現在の責任とAuthority Boundaryを分類する;
2. Routing Tableを確認する;
3. Triggerが実質的に該当する条件付きSkillだけをロードする;
4. そのSkillに従って作業する;
5. Task Stateが大きく変化したらRoutingを再確認する。

ロードされたMethodを追加Authorityとして扱わない。
すべてのMethodをChecklistのように一括ロードしない。
```

## Skillの直接利用

Routing Layerは必須ではありません。Userまたは利用アプリケーション側で必要な能力がすでに分かっている場合は、そのSkillを直接呼び出して使えます。

例:

- 情報源依存の事実調査 → `research`
- 収集したEvidenceの解釈 → `analysis`
- 原因不明のSoftware Failure診断 → `debugging`
- 承認済みIntentのRequirement具体化 → `requirements-specification`

## 重要事項

Routing Layerは、対象Skillをまだ読んでいなくてもTriggerを認識できる必要があります。Skillを読まなければTriggerを説明できない場合、その境界は循環的すぎるか、細分化しすぎている可能性があります。

## 選択ルールの補足

現在未解決の責務に最も直接合う手法を選び、確定済みの結果を再利用します。他スキルへの言及だけではロードしません。専門スキル内の通常の推論・検証に追加スキルは不要です。親の問題設定と子の局所問題の解決は別責務なので、problem-solvingの併用自体は禁止しません。

要件ゲートは既存の承認を先に確認します。UIに見える変更であることだけを停止理由にせず、依頼範囲内の判断は進めます。真正の新規製品要件は承認まで提案として保持します。
