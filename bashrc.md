#
# ~/.bashrc
#
# If not running interactively, don't do anything

[[ $- != *i* ]] && return

#tmux

##################################
###### prompt colours ############
##################################

## Regular Colors##       Bold High Intensity         ## Underline                ## Background
# Black="\[\033[0;30m\]"  # BIBlack="\[\033[1;90m\]"  # UBlack="\[\033[4;30m\]"   # On_Black="\[\033[40m\]" 
# Red="\[\033[0;31m\]"    # BIRed="\[\033[1;91m\]"    # URed="\[\033[4;31m\]"     # On_Red="\[\033[41m\]" 
# Green="\[\033[0;32m\]"  # BIGreen="\[\033[1;92m\]"  # UGreen="\[\033[4;32m\]"   # On_Green="\[\033[42m\]"
# Yellow="\[\033[0;33m\]" # BIYellow="\[\033[1;93m\]" # UYellow="\[\033[4;33m\]"  # On_Yellow="\[\033[43m\]"
# Blue="\[\033[0;34m\]"   # BIBlue="\[\033[1;94m\]"   # UBlue="\[\033[4;34m\]"    # On_Blue="\[\033[44m\]"
# Purple="\[\033[0;35m\]" # BIPurple="\[\033[1;95m\]" # UPurple="\[\033[4;35m\]"  # On_Purple="\[\033[45m\]" 
# Cyan="\[\033[0;36m\]"   # BICyan="\[\033[1;96m\]"   # UCyan="\[\033[4;36m\]"    # On_Cyan="\[\033[46m\]" 
# White="\[\033[0;37m\]"  # BIWhite="\[\033[1;97m\]"  # UWhite="\[\033[4;37m\]"   # On_White="\[\033[47m\]"

#################################
############ prompt #############
#################################

PS1='\[\033[1;96m\]\u\[\033[1;97m\]:\[\033[1;94m\]\h \[\033[1;97m\]\w \[\033[1;97m\]'
# PS1='Σ>―(\[\033[36m\]\u\[\033[0m\]○°ω°○\[\033[34m\]\h \[\033[37m\]\w \[\033[0m\])♡ '
# PS1='\[\033[1;97m\]╭─ \[\033[1;91m\]\u\[\033[1;97m\]:\[\033[1;94m\]\h\[\033[1;97m\]\n╰──╮⋆.°🦋˖⁺\[\033[1;91m\]♡\[\033[1;97m\] ˚\[\033]1;91m\]♥ \[\033[1;97m\]˖⋆ \[\033[1;97m\]\[\033[1;97m\]\n˖\[\033[1;91m\]❤ \[\033[1;97m\]₊╰┈➤  \[\033[1;97m\]\w '

case ${TERM} in
  Eterm*|alacritty*|aterm*|foot*|gnome*|konsole*|kterm*|putty*|rxvt*|tmux*|xterm*)
    PROMPT_COMMAND+=('printf "\033]0;%s@%s:%s\007" "${USER}" "${HOSTNAME%%.*}" "${PWD/#$HOME/\~}"')

    ;;
  screen*)
    PROMPT_COMMAND+=('printf "\033_%s@%s:%s\033\\" "${USER}" "${HOSTNAME%%.*}" "${PWD/#$HOME/\~}"')
    ;;
esac

#################################
######### fastfetch #############
#################################

if [ -f /usr/bin/fastfetch ]; then
	fastfetch
fi

#################################
####### bash completion #########
#################################

if [ -f /usr/share/bash-completion/bash_completion ]; then
	. /usr/share/bash-completion/bash_completion
elif [ -f /etc/bash_completion.d/000_bash_completion_compat.bash ]; then
	. /etc/bash_completion/000_bash_completion_compat.bash
fi

################################
########### aliases ############
################################

#dirs ##################
alias ..='cd ..'
alias ...='cd ../../../'
alias ....='cd ../../../../'
alias .....='cd ../../../../'
alias rr='d /'
alias bin='d /bin'
alias boot='d /boot'
alias dev='d /dev'
alias etc='d /etc'
alias home='d /home'
alias lib='d /lib'
alias lib64='d /lib64'
alias mnt='d /mnt'
alias opt='d /opt'
alias proc='d /proc'
alias root='d /root'
alias run='d /run'
alias sbin='d /sbin'
alias srv='d /srv'
alias sys='d /sys'
alias tmp='d /tmp'
alias usr='d /usr'
alias var='d /var'
alias dld='d ~/Downloads'
alias cfg='d ~/.config'
#A #######################
alias ipa='ip addr'
#B #######################
alias bi='blkid'
#C #######################
alias cat='cat -n'
alias c='clear'
alias cp='cp -ir'
alias cSbash='r ~/.bash_history'
alias co='testcolors'
#D ######################
alias d='cd'
alias df='df -Th'
alias dff='df -Tha'
alias du='du -h --time'
alias duu='dua -ha --time'
alias dir='dir --color=auto'
alias disable='sudo systemctl disable'
alias dmesg='dmesg --color'
alias dl='l && d'
alias dll='ll && d'
#E #######################
alias enable='sudo systemctl enable'
#F #######################
alias f='find . | grep '
alias fw='sudo firewall-cmd'
alias fwz='sudo firewall-cmd --get-zones'
alias fwaz='sudo firewall-cmd --get-active-zones'
alias fwl='sudo firewall-cmd --list-all --permanent'
alias fwch='firewall-cmd --check-config'
alias fwp='firewall-cmd --list-ports'
#G #######################
alias grep='grep --color=auto'
#H #######################
alias h='history | grep '
alias ho='d ~/'
#I #######################
alias ip='ip -color'
#J #######################
alias j='journalctl'
alias jr='journalctl -r'
#K #######################
alias kinit='sudo pacman-key --init'
alias kpop='sudo pacman-key --populate'
#L #######################
alias l='ls'
alias ll='ls -lhas'
alias llr='ls -lhasr'
alias lr='ls -r'
alias lz='lz4 -1'
alias less='less -R'
alias ls='ls --color=auto'
alias less='less --use-color'
alias lb='lsblk'
#M #######################
alias msf='msfconsole'
alias mkd='mkdir -p'
alias mv='mv -i'
#N #######################
alias n='nano'
alias nkill='sudo firewall-cmd --panic-on'
alias non='sudo firewall-cmd --panic-off'
alias nmkill='sudo systemctl stop NetworkManager.service'
alias nmrestart='sudo systemctl restart NetworkManager.service'
alias nmon='sudo systemctl start NetworkManager.service'
alias nbash='nano ~/.bashrc'
#O #######################
#P #######################
alias ports='netstat -nape --inet'
alias ping='ping -c 10'
alias ps='ps auxf'
alias p='ps aux | grep '
alias psmem='ps auxf | sort -nr -k 4'
alias psmem10='ps auxf | sort -nr -k 4 | head -10'
alias py='python'
alias pi='/usr/bin/octopi'
#Q #######################
alias qs='sudo pacman -Qs'
alias ql='sudo pacman -Ql'
alias qi='sudo pacman -Qi'
alias qg='sudo pacman -Qg'
alias qd='sudo pacman -Qd'
#R #######################
alias R='sudo pacman -R'
alias rdd='sudo pacman -Rdd'
alias r='rm -fr'
alias restart='sudo systemctl restart'
alias ren='repo-add --new'
alias rens='repo-add --new --sign'
alias rer='repo-add --remove'
alias res='repo-add --sign'
#S #######################
alias serve='mkdocs serve'
alias s='su'
alias S='sudo pacman -S'
alias sy='sudo pacman -Sy'
alias syu='sudo pacman -Syu'
alias suy='sudo pacman -Suy'
alias sc='pacman -Sc'
alias scc='pacman -Scc'
alias start='sudo systemctl start'
alias stop='sudo systemctl stop'
alias stat='sudo systemctl status'
alias sauce='source ~/.bashrc'
#T #######################
alias t='tar -cvf'
alias tg='tar -cvzf'
alias tt='tar -tvf'
alias tdel='tar --delete -f'
alias tup='tar -uvf'
alias tconf='nano ~/.tmux.conf'
alias tsauce='source ~/.tmux.conf'
alias tmux="tmux -f ${HOME}/.tmux.conf"
#U #######################
alias unt='tar -xvf'
alias untg='tar -xvzf'
alias unlz='lz4 -d'
#V #######################
alias vdir='vdir --color=auto'
#W #######################
alias wg='sudo wg'
alias wget='wget -c'
alias wgup='sudo wg-quick up'
alias wgdn='sudo wg-quick down'
#X #######################
#Y #######################
alias ys='yay -S'
alias ysc='yay -Sc'
alias yscc='yay -Scc'
alias ysyu='yay -Syu'
alias ysuy='yay -Suy'
alias yr='yay -R'
alias yrd='yay -Rd'
alias yrdd='yay -Rdd'
alias yq='yay -Q'
alias yqs='yay -Qs'
alias yql='yay -Ql'
alias yqi='yay -Qi'
alias yqg='yay -Qg'
alias yqd='yay -Qd'
#Z #######################

#################################
############ xdg ################
#################################

# export XDG_DATA_HOME="$HOME/.local/share"
export XDG_CONFIG_HOME="$HOME/.config"
# export XDG_STATE_HOME="$HOME/.local/state"
export XDG_CACHE_HOME="$HOME/.cache"
# export GNUPGHOME="$XDG_DATA_HOME"/gnupg

#################################
######### testing colours #######
#################################

function testcolors() {
    DEFAULT="\033[39m"
    RESET="\033[0m"
    NORMAL="\033[22m" # Normal color or intensity Neither bold nor faint
    BOLD="\033[1m"    # Bold or (bad behavior) increased intensity
    FAINT="\033[2m"

    echo -e "${BOLD}${DEFAULT}DEF(39)    BLA   RED   GRE   YEL   BLU   MAG   CYA   WHI"

    echo -e -n "${RESET}${BOLD}${DEFAULT} Bold     "
    for i in {30..37}; do
        printf "\e[${i}m %d  " "$i"
    done
    printf "\e[0m\n"

    echo -e -n "${RESET}${NORMAL} Intense  "
    for i in {30..37}; do
        printf "\e[${i}m %d  " "$i"
    done
    printf "\e[0m\n"


    echo -e -n "${RESET}${NORMAL} Normal   "
    for i in {30..37}; do
        printf "\e[${i}m %d  " "$i"
    done
    printf "\e[0m\n"

    echo -e -n "${RESET}${FAINT} Faint    "
    for i in {30..37}; do
        printf "\e[${i}m %d  " "$i"
    done
    printf "\e[0m\n"
}
