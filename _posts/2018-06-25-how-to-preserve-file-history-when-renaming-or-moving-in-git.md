---
layout: post

title: 'Git/Github에서 file의 이름이나 경로를 변경할 때(rename, move) 히스토리 유지시키는 방법'
description: 'how to preserve file history when renaming or moving in git'
tag: [ git ]
---

## Git에서 history 유지하기

개발하다보면  
파일이름을 수정하거나, 위치를 이동시키는 일이 잦은데  
그럴 때마다 그 파일의 이전 히스토리가 안보여서 
해결방법을 찾아보게 되었고 기억하기 위해 글 씀!

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

<br>

## Github 에서 history 유지하기

그러나 아직 완벽하지 않았다.  
위의 방법은 히스토리를 git에서만 볼 수 있고, Github History에서는 여전히 볼 수가 없다. (Blame탭에서는 가능)  
그래서 방법을 또 찾아봄

<br>

* [Chrome브라우저의 extension app: Github Follow](https://chrome.google.com/webstore/detail/github-follow/agalokjhnhheienloigiaoohgmjdpned)라는 것이 있었다.
  * (이 아이를 설치한 브라우저에 한해서) 변경되기전 파일의 'follow링크'가 렌더링되고, 클릭하면 이전 파일의 history 페이지가 나온다.

<br>

## 참고로 이런 (불편한) 일이 일어나는 이유는, 
* git은 file이 아닌 content기준으로 tracking을 하기 때문이고
* (이미 많은 사람들이) Github에 유사한 문의를 올렸는데, known issue이고 추후 개발할 수도 있다는 답변을 줬다고 한다.

<br>

### (참고한 문서들)
* [Preserving History When Renaming Files in git](http://thisbythem.com/blog/preserving-history-when-renaming-files-in-git/)
* [Why does git log not default to git log --follow?](https://stackoverflow.com/questions/12150899/why-does-git-log-not-default-to-git-log-follow/32039661)
* [git issue: History of files should optionally show include logs from a rename (git log --follow) #2487](https://github.com/gogs/gogs/issues/2487)
* [How to make github follow directory history after renames?](https://stackoverflow.com/questions/5646174/how-to-make-github-follow-directory-history-after-renames)
