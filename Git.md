
## Git 개요
#### Git 이란
소스코드를 효과적으로 관리할 수 있게 해주는 무료 소프트웨어로 **버전 관리 시스템**의 일종이다.

#### Git과 Github에 대해
Git은 로컬 디렉토리에 있는 파일들의 버전을 관리하기 위한 툴이고 Github는 웹에서 파일들의 버전을 관리하고 저장한다고 생각하면 된다.  
Github에서 파일들을 저장하는 공간을 **Repository** 혹은 **원격 저장소**라고 한다.  



#### Git  자료
생활 코딩의 [지옥에서 온 Git](https://www.youtube.com/watch?v=hFJZwOfme6w&list=PLuHgQVnccGMA8iwZwrGyNXCGy2LAAsTXk)을 통해 학습  
[Git for Windows](https://gitforwindows.org/)를 다운로드 후 설치

## Git 기본 명령어
### git init  
initialize(초기화)의 약자로, Git을 위한 초기 설정을 한다. 이때 **.git** 폴더가 생성되는데 ***절대*** 삭제하면 안된다.  
```bash
git init
```

### git remote
Github repository와 연결한다.  
```bash
git remote add <저장소 명> <repository URL>
```
연결된 repository 목록을 확인한다.
```bash
git remote -v
```
연결된 repository를 삭제한다.
```bash
git remote remove <저장소 명>
```

### git config
git이 commit할때 저장할 사용자의 정보를 설정한다.
```bash
git config --global user.name <유저명>
```
```bash
git config --global user.email <이메일>
```

### git status  
폴더 내 파일들의 상태를 알려준다.
```bash
git status
```
#### 파일의 상태에 대해
워킹 디렉토리(작업 중인 로컬 디렉토리)의 파일은 **Untracked, Tracked** 두 가지 상태로 나뉜다.

**Untracked** :  파일을 추적하지 않는 상태, 파일을 수정 해도 Git에서 기록하지 않는다.
**Tracked** :  파일을 추적하지 않는 상태, 파일을 수정하면 Git이 기록한다.

Git에서 파일 수정에 관해 기록하는 영역을 **Staging Area** 혹은 **스테이징 영역**이라고 한다.  

파일을 **Staging Area**에 추가, **Tracked** 상태로 변경하고 싶으면 `git add` 명령어를 사용하면 된다.  
파일을 **Staging Area**에서 제거, **UnTracked** 상태로 변경하고 싶으면 `git restore` 명령어를 사용하면 된다.

**Tracked** 상태는 크게 3가지 상태로 나뉜다.  
**Unmodified** : 파일이 수정되지 않은 상태이다.
**Modified** : 파일이 수정된 상태이다.
**Staged** : 파일이 **Staging Area**에 있는 상태이다.  

<img src=https://git-scm.com/book/en/v2/images/lifecycle.png>

### git add
워킹 디렉토리의 파일을 스테이징 영역에 추가한다.
```bash
git add <파일명>
```

### git restore
스테이징 영역에 있는 파일을 제거한다.
```bash
git restore --staged <파일명>
```

### git commit
스테이징 영역에 있는 파일을 저장한다.
```bash
git commit
```
-m 옵션을 이용하면 vim을 사용하지 않고 메세지를 저장할 수 있다.
```bash
git commit -m "<저장할 메세지>"
```

### git log
git의 로그를 출력한다. 커밋 ID를 확인할 수 있다.
```bash
git log
```
--branches 옵션을 이용하면 자신이 있는 branch 외에 다른 branch의 로그도 보여준다.
--decorate 옵션을 이용하면 branch가 어떤 commit을 가르키고 있는지 보여준다.
```bash
git log --branches -- decorate
```
-p 옵션을 이용하면 소스코드가 어떻게 변했는지 비교하여 보여준다.
```bash
git log -p
```

### git diff
마지막 커밋과 현재 수정한 코드를 비교해준다.
```bash
git diff
```
두 커밋의 소스 상의 차이를 보여준다.
```bash
git diff <커밋ID 1>..<커밋ID 2>
```

### git reset
버전 id로 돌아간다.
```bash
git reset --hard <버전 id>
```
cf) 원격 저장소가 아닌 본인 PC 버전에 대해서만 reset을 진행해야한다.

### git revert
버전 id의 커밋을 취소한 내용을 새로운 버전으로 만드는 명령
```bash
git revert <버전 id>
```

### git push
원격 저장소에 commit 내용 저장한다.
```bash
git push <저장소 명> <branch 명>
```
`git push origin main`을 많이 사용한다.

### git pull
원격 저장소의 내용을 가져온다.
```bash
git pull
```

### git clone
원격 저장소의 내용을 복제한다.
init 파일도 복제된다.
```bash
git clone <repository URL>
```


## Git Branch 기초
### git branch
로컬 branch 정보를 보여준다.
```bash
git branch
```
뒤에 생성할 branch 명을 적어 branch를 생성할 수도 있다.
```bash
git branch <branch 명>
```

### git checkout
입력한 branch로 전환한다.
```bash
git checkout <branch 명>
```




## Git 명령어 사용 빈도
***기울어지고 강조된 글씨***는 위에서 소개한 기본 명령어이다.  
google results는 구글 검색량을 의미하며 기본 명령어만 40%인 것을 알 수 있다.  
기본 명령어부터 익히는 것을 목표로 하자.  
|command|google results|%|
|:---|---:|---:|
|***commit***|***528,000***|***7.981980075***|
|push|523,000	|7.906393143|
|pull|506,000|7.649397572|
|clone|489,000|7.392402002|
|checkout|470,000|7.105171658|
|***add***|***446,000***|***6.742354382***|
|branch|439,000|6.636532676|
|***log***|***388,000***|***5.865545964***|
|***diff***|***369,000***|***5.578315621***|
|fetch|355,000|5.36667221|
|merge|354,000|5.351554823|
|***init***|***343,000***|***5.185263572***|
|***status***|***286,000***|***4.323572541***|
|***reset***|***267,000***|***4.036342197***|
|tag|246,000|3.718877081|
|rebase|203,000|3.068829461|
|rm|142,000|2.146668884|
|show|104,000|1.572208197|
|bisect|62,800|0.9493718726|
|grep|49,400|0.7467988934|
|mv|44,700|0.6757471768|

