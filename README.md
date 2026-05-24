# Dual Model Operation Kit

このフォルダは、2つのAIロールを使って大きめの作業を安定して進めるための汎用テンプレートです。

目的は、会話ログやコピペに依存せず、ファイルを通じて次の2つを分けることです。

- Manager: 方針、優先順位、境界、停止条件を決める
- Coder: 指示に従って小さく実装、検証、状態報告を行う

## ファイル構成

```text
dual-model-operation-kit/
  README.md
  DUAL_MODEL_OPERATION.md
  DUAL_MODEL_INTERFACE.md
  MANAGER_INSTRUCTIONS.md
  CODER_STATUS.md
```

## 使い方

1. プロジェクトにこのフォルダをコピーします。
2. ユーザーがプロジェクトの内容、計画書、AIとのやり取りの要点を整理します。
3. `DUAL_MODEL_OPERATION.md` の `Project Principle` を、ユーザー自身で書くか、AIに書かせます。
4. Manager役とCoder役の両方に、次の5ファイルを読ませます。

```text
README.md
DUAL_MODEL_OPERATION.md
DUAL_MODEL_INTERFACE.md
MANAGER_INSTRUCTIONS.md
CODER_STATUS.md
```

5. それぞれのAIに、自分の役割がManagerかCoderかを明示します。
6. Manager役のAIが `MANAGER_INSTRUCTIONS.md` を更新します。
7. Coder役のAIに `MANAGER_INSTRUCTIONS.md` を読ませます。
8. Coder役のAIが作業し、`CODER_STATUS.md` を更新します。
9. Manager役のAIに `CODER_STATUS.md` を読ませます。
10. 以後、6〜9を繰り返します。

## 役割

Manager は「何をするか」「何をしないか」を決めます。

Coder は「決められた範囲を実装し、検証して報告する」ことに集中します。

## 適している作業

- 大きなリファクタリング
- 長期的な設計変更
- 複数段階のリリース準備
- ヒューリスティックや判断ロジックが絡む変更
- AIに任せると作業目標がぶれやすいプロジェクト

## 運用上の重要点

- Managerは必ず `MANAGER_INSTRUCTIONS.md` を更新します。
- Coderは必ず `CODER_STATUS.md` を更新します。
- Coderは判断ロジックを勝手に増やしません。
- Managerは次の作業範囲と停止条件を明記します。
- 古い情報は短く圧縮し、現在の状態を先頭に置きます。

## 最小ルール

- 迷ったら、Coderは止まって `CODER_STATUS.md` に報告します。
- 迷ったら、Managerは作業を小さく切ります。
- 重要な判断はコードではなく、まず指示書に残します。
