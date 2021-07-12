# oh-my-zsh
### This is how the Final Setup will look like : 😎
![bash](./assets/git-bash.png)
## Install oh-my-zsh on Git Bash
1. Create a <b>git</b> folder in <b>%HOMEPATH%/.config</b>
2. Save this file as git-prompt.sh in git

    ```
    PS1='\[\033]0; Bash | \W\007\]' 		# set window title
    PS1="$PS1"'\n'							# new line
    PS1="$PS1"'\[\e[30;47m\] [\A] '					# insert real-time clock
    PS1="$PS1"'\[\e[97;104m\] \u '					# insert user
    PS1="$PS1"'\[\e[30;46m\] (@\h) '				# insert @host
    PS1="$PS1"'\[\e[30;43m\] <\W> '					# insert current working directory

    if test -z "$WINELOADERNOEXEC"
    then
        GIT_EXEC_PATH="$(git --exec-path 2>/dev/null)"
        COMPLETION_PATH="${GIT_EXEC_PATH%/libexec/git-core}"
        COMPLETION_PATH="${COMPLETION_PATH%/lib/git-core}"
        COMPLETION_PATH="$COMPLETION_PATH/share/git/completion"
        if test -f "$COMPLETION_PATH/git-prompt.sh"
        then
            . "$COMPLETION_PATH/git-completion.bash"
            . "$COMPLETION_PATH/git-prompt.sh"
            PS1="$PS1"'\[\e[97;45m\]'  # change color to cyan
            PS1="$PS1"'`__git_ps1` '   # bash function
        fi
    fi
    PS1="$PS1"'\[\033[0m\]'        # change color
    PS1="$PS1"'\n'                 # new line
    PS1="$PS1"'$ '                 # prompt: always $

    MSYS2_PS1="$PS1"               # for detection by MSYS2 SDK's bash.basrc

    # Evaluate all user-specific Bash completion scripts (if any)
    if test -z "$WINELOADERNOEXEC"
    then
        for c in "$HOME"/bash_completion.d/*.bash
        do
            # Handle absence of any scripts (or the folder) gracefully
            test ! -f "$c" ||
            . "$c"
        done
    fi
    ```
3. Clone [base16-mintty](https://github.com/iamthad/base16-mintty)
    ```
    git clone https://github.com/iamthad/base16-mintty.git
    ```
4. Paste all mintty themes in <b>%HOMEPATH%/.mintty/themes</b>
5. Download Meslo font
    ```
    git clone https://github.com/powerline/fonts.git
    ```