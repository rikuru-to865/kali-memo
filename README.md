#netcatのリバースシェルを限りなく自由度を高くする。


python -c 'import pty; pty.spawn("/bin/bash")'
を実行し、ptyを呼び出したあと、ctrl+zで停止する。
攻撃側pcでstty -aを実行しrowsとcolumnsを取得する。
続いてstty raw -echoを実行する。

fgで被害者pcに戻り、resetとうつ。
完了した後
$ export SHELL=bash
$ export TERM=xterm256-color
$ stty rows 攻撃側pcで取得したrows columns 攻撃側pcで取得したcolumns
と実行するとかなり自由度の高いシェルが手に入る。
