---
tittle: "[Git commit history 일괄 삭제"
excerpt: "안전한 전체 커밋 히스토리 삭제 방법"
categories:
  - Git
tags:
  - 깃
  - 깃허브
last_modified_at: 2020-01-14
---

![](https://github.com/gyumeen/blog-images/blob/main/2021/01/Delete%20commits%20history/1.jpg?raw=true)

<U>.git</U> 디렉터리 자체를 삭제하는 건 레파지토리에 문제를 발생시킬 수 있는 단점이 있다.  
따라서 현재 깃허브에 올려져 있는 코드 상태를 그대로 유지한 채,  
모든 커밋 히스토리를 삭제할 수 있는 방법은 다음과 같다.

<br/>

Check out to a temporary branch  

```
git checkout --orphan TEMP_BRANCH
```

고이 브랜치로 이동

<br/>

Add all the files

```
git add -A
```

<br/>

Commit the changes  

```
git commit -am "Initial commit"
```

모든 커밋에 메시지를 부여

<br/>

Delete the old branch

```
git branch -D master
```

master 브랜치를 강제로 삭제(git branch -d가 삭제할 수 없는 브랜치를 지울 때 사용)

<br/>

Rename the temporary branch  

```
git branch -m master
```

Finally, force update to our repository  

```
git push -f origin master
```

