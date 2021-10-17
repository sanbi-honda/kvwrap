# kvwrapfigパッケージ

図表の回り込みを行うための定番であるwrapfigパッケージが提供するwrapfigure環境，wraptable環境はその引数の順番がいつも分からなくなります．そこでこの引数を`<key>=<val>`形式にします．ただし，必須の引数である「幅」は`<key>=<val>`にはしません．また「位置」の引数もwrapfigパッケージでは必須なのですが，これは単独のオプションとします．

wrapfigパッケージをベースにして，本文との間隔を変えやすく，また引数の指定を容易にしています．

## パッケージオプション

````
\usepackage[<keyval>]{kvwapfig}

<keyval> := <key>\s*=\s*<val>
<key> := pos | sep | overhang
<val> :=  r | l | i | o | R | L | I | O  (if <key>=pos)
          <dim> (otherwise)
````
ここで`<dim>`は寸法とみなせるTeXのトークン（列）です．

- posキー：wrapfigure（wraptable）環境に与えることのできる「位置」を定める文字列が値です．デフォルトは`o`（outer，小口）です．
- sepキー：本文との間隔がその値です．デフォルトは`\columnsep`です．
- overhangキー：wrapfigure（wraptable）環境に与えることのできる「overhang」を定める値です．デフォルトは`0pt`です．

以上の値は，文書全体で共通となり，この値を変更するときのみ，それぞれの回り込みでオプションとして指定します．


## 定義される環境

wrapfigパッケージに準じて，wrapfigure環境に対応するkvwrapfigure環境，wraptable環境に対応するkvwraptable環境を定めます．これらの書式は同じなのでkvwrapfigure環境のみ示します．

````
\begin{kvwrapfigure}{<width>}[<pos>]<<keyval list>>
<contents>
\end{kvwrapfigure}
````
`<width>`は環境内の`<contents>`の幅です．ベースのwrapfigure環境の「幅」に相当する必須の引数であり，kvwrapfigure環境では必須引数はこれのみです．wrapfigure環境で要求される他の引数はパッケージオプションから引き継がれるか，各環境のオプション引数で与えられます．

最初のオプション引数は`[`と`]`で囲んで与え，その値の`<pos>`はパッケージオプションのposキーと同じです．パッケージオプションの指定をここで上書きします．


`<keyval list>`は二つ目のオプション引数で`<`と`>`で囲んで与えます．以下のキーと値のカンマ区切りリストです．

- linesキーには`<contents>`が何行に相当するかの行数を与えます．wrapfigure環境でもこの行数はオプションであり通常は内部的に計算されますが，それと同じでます．
- sepキーはパッケージオプションのsepキーと同じです．パッケージオプションの指定をここで上書きします．
- posキーはパッケージオプションのposキーと同じです．パッケージオプションの指定をここで上書きします．
- seposキーはパッケージオプションのposキーと同じです．パッケージオプションの指定をここで上書きします．
- overhangキーはパッケージオプションのposキーと同じです．パッケージオプションの指定をここで上書きします．

## 動作環境

TeXLive2018でテストしています．regexpatchパッケージとxparseパッケージを使っていることもありTeXLive2017以降であれば動作すると思いますが，TeXLive2018以降を想定しています．


## 更新履歴

- 2021/10/18 バージョン等を追加（v.1.0），動作環境の注意を追記．
- 2021/10/15 initial commit



