# 第3回 解答

## 演習

- 第1回（素のLLM）とエージェントの回答の違い：
- `--trace` で見えたツール呼び出し（ツール名と引数）：search_glossary({'query': 'LoRA'})、search_glossary({'query': 'QLoRA'})
- 1つの質問での LLM 呼び出し回数（`requests`）：2回
- 追加したツールと、docstring に書いた説明：make_quizを追加。docstringにはこのツールをいつ、何のために使うかを記載

## 宿題

- 取り組んだレベル：基礎
- やったこと：app/agent.py の INSTRUCTIONS や、app/tools.py のツールの docstring を書き換えて、--trace付きで質問を実行
- 結果：「必ず search_glossary で用語集を確認する」の行を消しても、search_glossaryが呼ばれた。
docstring の「用語を1つだけ入れる」を「まとめて入れる」に変えると、tool callは一回になった。
- 気づき・疑問：
なぜsearch_glossaryが呼ばれたのか。「回答の最後に、関係する回（第N回）を示す」の行を消すと第N回の表示が消えたことからINSTRUCTIONSが無視されているわけではなさそう。複数回試したがsearch_glossarは毎回呼ばれた。偶然？
