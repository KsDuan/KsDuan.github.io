# GitBash终端上隐藏删掉MINGW64

![img](https://markbuild.com/wp-content/uploads/2018/10/git_bash_featured.jpg)

Git bash 显示的 MINGW64 是什么意思呢，能隐藏么，当然可以

MINGW是代表着[Minimalist GNU for Windows](http://www.mingw.org/) – 适用于Windows的极简GNU, GNU是一个类似UNIX的操作系统

但这个文字极占用眼睛空间，还是去掉比较清爽

[![img](https://markbuild.com/wp-content/uploads/2018/10/remove-mingw.png)](https://markbuild.com/wp-content/uploads/2018/10/remove-mingw.png)

编辑: C:\Program Files\Git\etc\profile.d\git-prompt.sh 文件

```
else
        TITLEPREFIX=$MSYSTEM
 fi
 
 if test -f ~/.config/git/git-prompt.sh
 then
        . ~/.config/git/git-prompt.sh
 else
-       PS1='\[\033]0;$TITLEPREFIX:$PWD\007\]' # set window title
+       PS1='\[\033]0;$PWD\007\]' # set window title
        PS1="$PS1"'\n'                 # new line
        PS1="$PS1"'\[\033[32m\]'       # change to green
        PS1="$PS1"'\u@\h '             # user@host
-       PS1="$PS1"'\[\033[35m\]'       # change to purple
-       PS1="$PS1"'$MSYSTEM '          # show MSYSTEM
        PS1="$PS1"'\[\033[33m\]'       # change to brownish yellow
        PS1="$PS1"'\w'                 # current working directory
        if test -z "$WINELOADERNOEXEC"
        then
                GIT_EXEC_PATH="$(git --exec-path 2>/dev/null)"
                COMPLETION_PATH="${GIT_EXEC_PATH%/libexec/git-core}"
                COMPLETION_PATH="${COMPLETION_PATH%/lib/git-core}"
                COMPLETION_PATH="$COMPLETION_PATH/share/git/completion"
```

– 去掉的行 + 增加的行