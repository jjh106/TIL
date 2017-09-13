### blog posting

#### 1. 포스트할 md 만들기

```
hexo new post '포스트명'
```

#### 2. 작성 & 확인

> source의 _post의 md에 작성하기

```
// 변경된 부분 확인하기
hexo server
```

#### 3. 포스팅하기

```
hexo generate --deploy
```

---

#### * blog repo에 관리하기

```
git add .
```

```
git commit -m ""
```

```
git push origin master
```

---

#### * 다른 로컬에서 관리하기

```
git clone blog주소
```

```
npm i -g hexo-cli
```

```
cd blog
```

```
npm i
```

```
npm install hexo-deployer-git --save
```

```
평소처럼 포스팅 하기
```



