## ページスタイルのカスタマイズ方法について

この項目は，不十分な点があるかもしれません。お気づきのことがありましたら加筆・修正（プルリクエスト）をお願いします。また，TeXwikiに書いていただけると幸いです。

fancyhdrは，ページスタイルを簡単にカスタマイズできる便利なパッケージであるが特定の条件で問題が発生することがある。詳しくは，https://oku.edu.mie-u.ac.jp/tex/mod/forum/discuss.php?d=3327 を参照されたい。

さて，fancyhdrの代替としてjlreqが提供する，`\NewPageStyle`について解説しよう。
### カスタマイズ方法
まず，フォーマットは，以下の通りである。

`\NewPageStyle{<ページスタイル名>}{<設定>}`

- ページスタイル名は，適当な名前を決めれば良い。例えば，`math-test`,`report`など。

続いて設定について解説しよう。設定については，公式ドキュメントがすでにあるので割愛し，ここでは簡単な例を示す。この設定をプリアンブルに加え，  使いたいところで`\pagestyle{preport}`とすればよい。
  
  * ページ上部左へ任意のテキスト，下部中央へページ番号/総ページ数，右側へ作成者情報としたいとき
  
  ```LaTeX
\documentclass{jlreq}
\usepackage{lastpage}
\NewPageStyle{preport}{
    running_head_position   = top-left,
    nombre_position         = bottom-center,
    nombre_ii_position      = bottom-right,
    nombre                  = \thepage/\pageref{LastPage},
    nombre_ii               = 作成者：\LaTeX 大学工学部 \LaTeX 太郎,
    odd_running_head        = \textbf{\Large ほげほげ実験 報告書}
}
\begin{document}
\pagestyle{preport}
あいうえお
\end{document}
 ```

  * 下部中央へページ番号/総ページ数としたいとき
```LaTeX
\documentclass{jlreq}
\usepackage{lastpage}
\NewPageStyle{preport}{
  nombre_position = bottom-center,
  nombre          = \thepage/\pageref{LastPage},
}
\begin{document}
\pagestyle{preport}
あいうえお
\end{document}
```

### 参考文献
* 公式ドキュメント
  * texdoc jlreq-ja
  * https://github.com/abenori/jlreq/blob/master/README-ja.md
* その他コンテンツ
  * http://abenori.blogspot.com/2018/08/jlreq-declarepagestyle-declarepagestyle.html
  * https://aznote.jakou.com/linux/latex_novel.html

