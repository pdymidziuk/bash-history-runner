# Bash History Runner

A simple script to search and execute commands from your bash history using `peco`, with automatic inclusion of executed commands back into history.

## Features

- Search through your bash history interactively using `peco`.
- Execute selected command directly.
- Automatically add the executed command back to the history.

## Prerequisites

- `peco`

## Installation

**Install `peco`**

```sh
sudo apt update
sudo apt install peco
```

**Add the Function to Your Shell Configuration**

Open your shell configuration file:

```ssh
nano ~/.bashrc
```

Add the following function to your `.bashrc` file:

```sh
hst() {
    selected_command=$(history | awk '{$1=""; print substr($0,2)}' | peco)
    if [ -n "$selected_command" ]; then
        history -s "$selected_command"
        eval "$selected_command"
    fi
}
```

**Reload Your Shell Configuration**

```sh
source ~/.bashrc
```

## Usage

```sh
hst
```