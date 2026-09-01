# Codex Platform Notes 日本語版

この資料は、Toolkit内のplatform-neutralな概念をCodex固有のRuntime Controlへ対応付けます。

Skill本体では、他のAgent Runtimeでも再利用できるようCodex固有のparameter名を意図的に避けています。この資料はnormativeなSkill Policyではなく、Codex向けのAdapter Noteとして扱ってください。

## Context inheritance

platform-neutralなPolicyでは、次の3概念を使用します。

- **No inheritance** — 子Agent / Reviewerを新しい会話Contextから開始し、bounded task packetとauthoritative artifactだけを渡す。
- **Limited inheritance** — 本当にtask-criticalな直近会話だけを、必要最小限引き継ぐ。
- **Full inheritance** — Artifactとbounded packetから合理的に再構築できない場合に限り、広い会話履歴を引き継ぐ。

`fork_turns` を利用できるCodex Runtimeでは、想定する対応は次の通りです。

| Toolkit概念 | Codexでの例 |
|---|---|
| No inheritance | `fork_turns: "none"` |
| Limited inheritance | 小さい正の `fork_turns` 値 |
| Full inheritance | `fork_turns: "all"` |

具体的なRuntime Syntaxにかかわらず、Toolkit Policy自体は変わりません。原則としてNo inheritanceを優先し、Limited inheritanceは直近会話そのものがtask-criticalな場合だけ使用し、Full inheritanceは例外として扱います。

## Portability rule

Codex側でRuntime Controlが追加・削除・renameされた場合、基礎となるorchestration概念そのものが変わらない限り、platform-neutralなSkill本体ではなくこのPlatform Noteを更新してください。
