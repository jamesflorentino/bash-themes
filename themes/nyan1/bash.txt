_PREFIX="\e[0;36m└\e[0;31m ∴ •＿• ∴\e[m "
_AT="\e[0;31m.\e[m"
#_USERNAME="\e[0;36m\u\e[m"
#_HOSTNAME="\e[0;32m\h\e[m"
_POINTER="∴"
_DATE="[$(date +%k:%M:%S) ]"
_DATE=""
_POINTER="\w > "
DASH="─"

function gettop {
	s=""
	prefx="┌───"
	title=" `pwd` "
	total=$COLUMNS-${#title}-${#prefx}
	for (( i=0; i<$total; i++  ))
	do
		s="$s$DASH"
	done
	title="\033[31m$title\033[m"
	echo -e "\n\033[36m$prefx\033[m$title\033[36m$s\033[m"
}

function getbottom {
	s=""
	title="└"
	total=$COLUMNS-${#title}
	for(( i=0; i<$total; i++  ))
	do
		s="$s$DASH"
	done

	line1="\033[36m$title$s\033[m\n"
	t=""
	title="┌───────"
	total=$COLUMNS-${#title}-1
	for(( i=0; i<$total; i++ ))
	do
		t="$t$DASH"	
	done
	line2="\033[36m$title$t\033[m"
	#line3="\033[36m\n⏐\033[m$title"
	echo -e "$line1$line2$line3"
} 

TOP=gettop
BOTTOM=getbottom

alias ll="$TOP; ls -FG; $BOTTOM"
alias la="$TOP; ls -aFG; $BOTTOM"
export PS1="$_PREFIX$_USERNAME$_AT$_HOSTNAME$_DATE\e[0;36m $_POINTER \e[m\e[0;33m"
export LSCOLORS="gxfxcxdxbxegedabagacad"
export CLICOLOR=1
