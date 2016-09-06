TL;DL
==========
warningの通り，いまのgitの挙動を保ちたいならmatching，現在のbranchのみ安全にpushしたいならsimpleにするとよい．

```
git config --global push.default matching
```

-----
git pushするとwarningが出るようになった

```
warning: push.default is unset; its implicit value is changing in
Git 2.0 from 'matching' to 'simple'. To squelch this message
and maintain the current behavior after the default changes, use:

  git config --global push.default matching

To squelch this message and adopt the new behavior now, use:

  git config --global push.default simple

See 'git help config' and search for 'push.default' for further information.
(the 'simple' mode was introduced in Git 1.7.11. Use the similar mode
'current' instead of 'simple' if you sometimes use older versions of Git)
```

push.defaultはrefspec（ブランチ名やタグ名）を指定しなかった場合の挙動を設定するオプション  
デフォルト設定がGit2.0からsimpleに変更になる  

simple
-----

現在のブランチをupstreamのブランチにpushする．ただしupstreamのブランチ名が現在のブランチと異なる場合はpushしない  ．
"This is the safest option and is well-suited for beginners."とのこと．あまり起きなさそうだけど，間違ったブランチをtrack設定してしまったときなどはpushできないので安全?  

matching
-----

git push時に同名のブランチ(=マッチするブランチ)をそれぞれpushする．いままでのデフォルト  

その他
-----

+ nothing  
pushしない．つまり必ずgit push origin masterのようにrefsを指定する必要がある  
+ current  
現在のブランチを同名のリモートブランチにpushする  
+ upstream  
現在のブランチをupstreamのブランチにpushする  
