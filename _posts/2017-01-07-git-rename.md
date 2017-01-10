---
layout: default
title: gitのAuthor変更と既存コミット主変更
date: 2017/01/07 19:30
---

gitでAuthorが異なってしまった場合のコミット&プッシュ主の変更方法  

# コマンド  

## Author変更  
  
```  
git config --local user.name NAME  
git config --local user.email MAIL@MAIL.COM  
```  
  
## 過去のコミット&プッシュ主変更  
  
```  
git filter-branch -f --env-filter  
"GIT_AUTHOR_NAME='NAME';  
 GIT_AUTHOR_EMAIL='MAIL@MAIL.COM';  
 GIT_COMMITTER_NAME='NAME';  
 GIT_COMMITTER_EMAIL='MAIL@MAIL.COM';  
" HEAD  
```  

OR

```
git filter-branch -f --env-filter "GIT_AUTHOR_NAME='NAME'; GIT_AUTHOR_EMAIL='MAIL@MAIL.COM'; GIT_COMMITTER_NAME='NAME'; GIT_COMMITTER_EMAIL='MAIL@MAIL.COM'; " HEAD
```
  
```  
git push -f origin master  
```  
  
# 参考  
http://qiita.com/sea_mountain/items/d70216a5bc16a88ed932  
http://tweeeety.hateblo.jp/entry/2015/03/10/211100  
  