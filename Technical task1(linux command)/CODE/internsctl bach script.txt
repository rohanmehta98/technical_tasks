#!/bin/bash

# Dependencies: lscpu, free, useradd, getent
if ! command -v lscpu &> /dev/null; then
  echo "Error: lscpu command not found. Please install it." >&2
  exit 1
fi
# ... (similar checks for free, useradd, getent)

# Functions for each command:

function cpu_getinfo() {
  lscpu
}

function memory_getinfo() {
  free
}

function user_create() {
  if [[ $# -ne 1 ]]; then
    echo "Usage: internsctl user create <username>" >&2
    return 1
  fi
  useradd "$1"
}

function user_list() {
  if [[ "$1" == "--sudo-only" ]]; then
    getent group sudo | cut -d: -f4
  else
    getent passwd | cut -d: -f1
  fi
}

function file_getinfo() {
  local filename options
  while [[ $# -gt 0 ]]; do
    case "$1" in
      --size | -s)
        options+=("%s")
        ;;
      --permissions | -p)
        options+=("%A")
        ;;
      --owner | -o)
        options+=("%U")
        ;;
      --last-modified | -m)
        options+=("%y")
        ;;
      *)
        filename="$1"
        ;;
    esac
    shift
  done

  if [[ -z "$filename" ]]; then
    echo "Error: Missing filename" >&2
    return 1
  fi

  if [[ ${#options[@]} -eq 0 ]]; then
    stat -c "File: %n
Access: %a
Size(B): %s
Owner: %U
Modify: %y" "$filename"
  else
    stat -c "${options[@]}" "$filename"
  fi
}

# Help function
function help() {
  cat <<EOF
internsctl v0.1.0

Usage: internsctl <command> [options]

Commands:
  cpu getinfo      - Get CPU information
  memory getinfo   - Get memory information
  user create <username>   - Create a new user
  user list [--sudo-only] - List users (with or without sudo permissions)
  file getinfo [options] <file-name> - Get file information

Options:
  --size, -s       - Print file size
  --permissions, -p - Print file permissions
  --owner, -o      - Print file owner
  --last-modified, -m - Print file last modified time
  --help            - Display this help message
  --version         - Print the script version

EOF
}

# Version function
function version() {
  echo "internsctl v0.1.0"
}



# Main script body:

if [[ $# -eq 0 ]]; then
  echo "Usage: internsctl <command> [options]" >&2
  exit 1
fi

case "$1" in
  --help)
    help
    ;;
  --version)
    version
    ;;
  cpu)
    cpu_getinfo
    ;;
  memory)
    memory_getinfo
    ;;
  user)
    shift
    case "$1" in
      create)
        user_create "$2"
        ;;
      list)
        user_list "$2"
        ;;
      *)
        echo "Invalid user subcommand: $1" >&2
        exit 1
        ;;
    esac
    ;;
  file)
    shift
    file_getinfo "$@"
    ;;
  *)
    echo "Invalid command: $1" >&2
    exit 1
    ;;
esac
