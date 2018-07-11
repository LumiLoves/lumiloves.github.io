---
title: 'git에 올린 file을 move/rename할 때 히스토리 유지시키는 방법'
description: 'how to keep file history when renaming or moving'
tag: [ git ]
---


개발하다보면  
파일이름을 수정하거나, 위치를 이동시키는 일이 잦은데  
그럴 때마다 그 파일의 이전 히스토리가 안보여서 
해결방법을 찾아보게 되었고 기억하기 위해 글 씀!
<br>
<br>
[ 방법 1 : 이름 변경, 폴더 변경해도 git log 확인시 계속 지난 히스토리가 보이도록 기본 설정. (이 값이 디폴트가 아닌 이유는, 성능이슈 때문이라고 함) ]
1. (해당 Repo만 설정)  git config log.follow true<br> 
  (전역 설정) git config --global log.follow true<br>
2. git mv foo.txt bar.txt
3. git commit -m 'rename: foo.txt --> bar.txt'
4. 히스토리 잘 보이는지 확인<br>
    git log bar.txt 

[ 방법 2 : 디폴트로 설정하지 않고, 단일 파일 하나당 log 확인하고 싶을 때 ]
1. git mv foo.txt bar.txt
2. git log --follow -p {파일이름}


[참고]
* [Preserving History When Renaming Files in git](http://thisbythem.com/blog/preserving-history-when-renaming-files-in-git/)
* [Why does git log not default to git log --follow?](https://stackoverflow.com/questions/12150899/why-does-git-log-not-default-to-git-log-follow/32039661)
* [git issue: History of files should optionally show include logs from a rename (git log --follow) #2487](https://github.com/gogs/gogs/issues/2487)
