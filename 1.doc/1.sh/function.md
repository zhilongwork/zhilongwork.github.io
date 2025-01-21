
```bash
# !/bin/bash

function isCmdExist() {
    local cmd="$1"
    if [ -z "$cmd" ]; then
        echo "Usage: $0 yourCmd"
        return 1
    fi

    which "$cmd" >/dev/null 2>&1
    if [ $? -eq 0 ]; then
        return 0
    fi

    return 2
}
function isExist() {
  local zdir="$1"
  if [ -z "$zdir" ]; then
    echo "Usage: $0 yourCmd"
      return 0
  fi
  if [ -e ${zdir} ]; then
    return 1
  elif [ -d ${zdir} ];then
    return 2
  elif [ -f ${zdir} ];then
    return 3
  else
    echo "Unknown file type!!!"
	return 0
  fi
}
function isFileExist() {
  local zdir="$1"
  if [ -z "$zdir" ]; then
    echo "Usage: $0 yourCmd"
      return 0
  fi
  if [ -f ${zdir} ]; then
    echo "file: (${zdir}) exist"
    return 1
  else
    echo "Unknown file type!!!"
	return 0
  fi
}

function isDirectoryExist() {
  local zdir="$1"
  if [ -z "$zdir" ]; then
    echo "Usage: $0 yourCmd"
      return 0
  fi
  if [ -d ${zdir} ]; then
    echo "dir: (${zdir}) exist"
    return 1
  else
    echo "Unknown file type!!!"
	return 0
  fi
}

function ask_install() {
  local package="$1"
  local choice
  read -p "install $package (y/n)Y?:" choice
  choice=$(echo $choice | tr [a-z] [A-Z])
  if [ x"$choice" = x"N" ];then
    echo "already installed, continue ..."
  else
    echo ${rootpass} | sudo -S apt -qq install -y $package
  fi
}

function ubuntuVer() {
  local DIST_NAME=`lsb_release -r --short 2>/dev/null | head -n1`

  echo "ubuntu: "$DIST_NAME
  if [ x"$DIST_NAME" = x"16.04" ];then
    return 16
  elif [ x"$DIST_NAME" = x"18.04" ];then
    return 18
  elif [ x"$DIST_NAME" = x"20.04" ];then
    return 20
  elif [ x"$DIST_NAME" = x"21.04" ];then
    return 21
  else
    return 0
  fi
}
```
