---
title: 'git에 올린 file을 move/rename할 때 히스토리 유지시키는 방법'
description: 'how to keep file history when renaming or moving'
tag: [ git ]
---


개발하다보면  
파일이름을 수정하거나, 위치를 이동시키는 일이 잦은데  
그럴 때마다 그 파일의 git 히스토리가 사라져서 아까운 마음에  
해결방법을 찾아보게 되었고 기억하기 위헤 글 씀!
<br>
<br>
1. (로그가 계속 따라오도록 설정. 이 값은 디폴트가 아닌데 그 이유는, 성능이슈때문이라고 함) git config log.follow true 또는 git config --global log.follow true
2. git mv foo.txt bar.txt
3. git commit -m 'rename: foo.txt --> bar.txt'
4. (히스토리 잘 이어졌는지 확인) git log bar.txt 

[참고]
* [Why does git log not default to git log --follow?](https://stackoverflow.com/questions/12150899/why-does-git-log-not-default-to-git-log-follow/32039661)
* [git issue: History of files should optionally show include logs from a rename (git log --follow) #2487](https://github.com/gogs/gogs/issues/2487)

