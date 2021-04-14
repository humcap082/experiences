
# リダイレクション

標準出力と標準入力とファイル書き込みなどをつなげる。

|形式|説明|
|:---|:---|
|command > path|標準出力をファイルに上書き保存|
|command >> path|標準出力をファイルに追加書き込み|
|command < path|標準入力をファイルに渡す|
|command << {keyword}multi_lines{keyword}|複数行を入力。keywordにはよくEOSやEOF、EODが使われる|
|command 2> path|標準エラー出力を書き込む|
|command1 &#124; command2|command1からcommand2に標準入出力(ファイルの代わりに渡す)する|
|command1 ; command2|command1が終わり次第、command2を実行|
|command1 & command2|command1をバックグランド実行し、command2を実行|
|command1 && command2|command1が正常な場合の限り、command2を実行|
|command &#124;&#124; command2|command1がエラーの場合、command2を実行|