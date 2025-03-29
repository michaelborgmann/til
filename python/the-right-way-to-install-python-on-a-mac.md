# The right way to install Python on a Mac

To install Python on a Mac, use [pyenv](https://github.com/pyenv/pyenv) and [pyenv-virtualenv](https://github.com/pyenv/pyenv-virtualenv). This setup allows you to manage multiple Python versions and create isolated environments for each project.

## Steps:

1. **Install Xcode Command Line Tools**:
```
$ xcode-select --install
```
2. **Install Homebrew**:
```
$ /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
3. **Install pyenv and pyenv-virtualenv**:
```
$ brew install pyenv pyenv-virtualenv
```
4. **Configure for Z Shell (zsh)**: Add to `~/.zshrc`:
```
eval "$(pyenv init -)"
if which pyenv-virtualenv-init > /dev/null; then eval "$(pyenv virtualenv-init -)"; fi
```
Restart your terminal.
5. **Install Python Version**: List available versions:
```
$ pyenv install --list
```
Install a version:
```
$ pyenv install 3.x.y
```
6. **Create a Virtual Environment**: Create and activate:
```
$ pyenv virtualenv 3.x.y myproject
$ pyenv local myproject
```
7. **Delete a Virtual Environment**:
```
$ pyenv virtualenv-delete myproject
```
