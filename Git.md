# GIT
## GIT 설치하기
1. Windows에 설치
+ https://git-scm.com/downloads/win
    ```
    Other Git for Windows downloads
    Standalone Installer
    > 64-bit Git for Windows Setup.
    > Download
    ```
+ Git-2.47.1.2-64-bit.exe 실행

## GitHub 주소
+ https://github.com/sungho7777

## GIT 명령어
+ **git --version** : 버전확인하기.
    ```cmd
    $ git --version
        git version 2.47.1.windows.2
    ```
+ **git config --global** : 이름, 이메일 설정하기.
    ```cmd
    $ git config --global user.name PSH
    $ git config --global user.email PSH@gmail.com
    ```
+ **git config -l** : 설정확인하기.
    ```cmd
    $ git config -l
        diff.astextplain.textconv=astextplain
        filter.lfs.clean=git-lfs clean -- %f
        filter.lfs.smudge=git-lfs smudge -- %f
        filter.lfs.process=git-lfs filter-process
        filter.lfs.required=true
        http.sslbackend=openssl
        http.sslcainfo=C:/Program Files/Git/mingw64/etc/ssl/certs/ca-bundle.crt
        core.autocrlf=true
        core.fscache=true
        core.symlinks=false
        pull.rebase=false
        credential.helper=manager
        credential.https://dev.azure.com.usehttppath=true
        init.defaultbranch=master
        user.name=PSH
        user.email=PSH@gmail.com
    ```
+ **git init** : 새로운 Git 저장소(reoisutory)를 생성(초기화).
    ```cmd
    $ git init
        Initialized empty Git repository in C:/MarkDown/.git/
    ```
+ **git remote add** : Git 원격저장소 연결.
    ```cmd
    $ git remote add origin https://github.com/sungho7777/MD.git
    ```
+ **git remote -v** : Git remote 버전 확인.
    ```cmd
    $ git remote -v
        origin  https://github.com/sungho7777/MD.git (fetch)
        origin  https://github.com/sungho7777/MD.git (push)
    ```
+ **git branch --show-current** : 현재 브랜치 확인
    ```cmd
    $ git branch --show-current
        master
    ```
+ **git pull** : 원격저장소에 있는 프로젝트의 변경사항을 그대로 로컬저장소에 옮겨와 자동으로 병합
    ```cmd
    $ git pull origin main
        remote: Enumerating objects: 3, done.
        remote: Counting objects: 100% (3/3), done.
        remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
        Unpacking objects: 100% (3/3), 863 bytes | 95.00 KiB/s, done.
        From https://github.com/sungho7777/MD
        * branch            main       -> FETCH_HEAD
        * [new branch]      main       -> origin/main
    ```
+ **git status** : 현재 상태 확인
    ```cmd
    $ git status
        On branch master
        Changes not staged for commit:
        (use "git add <file>..." to update what will be committed)
        (use "git restore <file>..." to discard changes in working directory)
                modified:   README.md

        no changes added to commit (use "git add" and/or "git commit -a")
    ```
+ **git add .** : 변경된 파일을 추가한다.
    ```cmd
    $ git add .
    $ git status
        On branch master
        Changes to be committed:
        (use "git restore --staged <file>..." to unstage)
                modified:   README.md
    ```
+ **git commit -m 'annotation' -a** : 변경된 파일을 추가한다.(주석포함)
    ```cmd
    $ git commit -m 'annotation' -a
        [master 246f9a9] annotation
        1 file changed, 60 insertions(+), 1 deletion(-)
    $ git status
        On branch master
        nothing to commit, working tree clean
    ```
+ **git reset --soft HEAD^** : commit 된 목록 취소하기.
    ```cmd
    $ git log
        commit 62f5b0e66207a588f6ab964a7c78c85d86f9c3e7 (HEAD -> master)
        Author: PSH <PSH@gmail.com>
        Date:   Wed Feb 12 13:51:12 2025 +0900

            annotation

        commit 15666807c0ef36a0b57ebd14af5c44964035b84d (origin/main)
        Author: 성호 <mzncvmc@gmail.com>
        Date:   Wed Feb 12 13:40:45 2025 +0900

            Initial commit

    $ git reset --soft HEAD^
    $ git status
        On branch master
        Changes to be committed:
        (use "git restore --staged <file>..." to unstage)
                modified:   README.md

        Changes not staged for commit:
        (use "git add <file>..." to update what will be committed)
        (use "git restore <file>..." to discard changes in working directory)
                modified:   README.md
    ```
+ **git reset HEAD .** : 추가된 add 파일을 취소한다.
    ```cmd
    $ git reset HEAD .
        Unstaged changes after reset:
        M       README.md
    $ git status
        On branch master
        Changes not staged for commit:
        (use "git add <file>..." to update what will be committed)
        (use "git restore <file>..." to discard changes in working directory)
                modified:   README.md

        no changes added to commit (use "git add" and/or "git commit -a")
    ```
+ **git push -u origin main** : commit 된 파일을 gethub 에 push 한다.
    + add + commit + push
        ```cmd
        $ git add .
        $ git status
            On branch master
            Changes to be committed:
            (use "git restore --staged <file>..." to unstage)
                    modified:   README.md
        $ git commit -m 'annotation' -a
            [master ea40d34] annotation
            1 file changed, 170 insertions(+), 1 deletion(-)
        $ git status
            On branch master
            nothing to commit, working tree clean
        $ git push -u origin master
            Enumerating objects: 5, done.
            Counting objects: 100% (5/5), done.
            Delta compression using up to 4 threads
            Compressing objects: 100% (2/2), done.
            Writing objects: 100% (3/3), 1.96 KiB | 1.96 MiB/s, done.
            Total 3 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
            remote:
            remote: Create a pull request for 'master' on GitHub by visiting:
            remote:      https://github.com/sungho7777/MD/pull/new/master
            remote:
            To https://github.com/sungho7777/MD.git
            * [new branch]      master -> master
            branch 'master' set up to track 'origin/master'.
        ```
+ **git reset --hard** : 로컬 브랜치를 리모트 상태로 강제 동기화하며 삭제된 파일도 복구
    ```cmd
    $ git reset --hard origin/master
        HEAD is now at 12104b4 annotation
    ```
+ **git restore** 또는 **git checkout** : 로컬에서 삭제된 개별파일 복구시키기
    ```cmd
    $ git status
        On branch master
        Changes not staged for commit:
        (use "git add/rm <file>..." to update what will be committed)
        (use "git restore <file>..." to discard changes in working directory)
                deleted:    README.md

        no changes added to commit (use "git add" and/or "git commit -a")
    $ git restore README.md
    $ git checkout -- README.md
    ```
