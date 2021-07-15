# git

> bash를 통해 git을 remote에 올려놓기



![image-20210715175452710](command.assets/image-20210715175452710.png)

> 로컬(Local)에 있는 파일들을 add, commit, push를 통해 리모트(remote)에 업로드한다.



### 시작하기

##### 로컬 저장소 설정

- 등록할 로컬 저장소에 .git 폴더를 생성하여 준비한다. 해당 디렉토리의 옆에는 (master) 가 표시된다.

```bash
$ git init
```



##### 원격 저장소 등록

- 로컬에 원격 저장소 링크를 저장한다. 매번 링크를 입력할 필요없이 커밋할 수 있다.

```bash
$ git remote add origin https://github.com/.../TIL.git
```



##### commit 작성자(author) 설정

```bash
$ git config --global user.email <email>
$ git config --global user.name <username>
```



##### 현재 git 상태 확인하기

```bash
$ git status
```





### 커밋하기

##### add

- 로컬 파일을 커밋할 목록에 추가한다.

```bash
$ git add <filename>
```



##### commit

- 업데이트 사항을 적고 commit한다.

```bash
$ git commit -m "<updates>"
```



##### push

- commit한 내용들을 위에 저장한 원격 저장소(origin)에 push한다.

```bash
$ git push origin master
```

