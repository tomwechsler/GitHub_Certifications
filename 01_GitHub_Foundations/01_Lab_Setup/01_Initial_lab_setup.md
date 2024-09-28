### Working on your own computer

**Installing Git**  

Windows: 
```
winget install -e --id Git.Git
```

macOS: 
```
brew install git
```

Ubuntu/Debian: 
```
sudo apt-get install git
```

CentOS/Red Hat: 
```
dnf install git
```

Check your installation: 
```
git --version
```

**Adding Git to the System Path**  
Git is usually automatically configured with environment variable defaults during installation.

**What is git config?**  
Git config is a command-line utility that allows you to set configuration variables that control all aspects of how Git looks and operates.

**Where is the Git config file stored?**  
The Git config file is stored in the home directory of the user. Within a specific Git repository, the configurations are stored inside the hidden .git/ folder in a Git config file called config.

**First Time Git Setup - git config username and email**  

```
git config --global user.name <user name>
```

```
git config –global user.email <email address>
```

**Git Text Editor Configuration Settings**  

```
git config --global core.editor "code --wait --new-window"
```

**How Do I See My git config?**  

```
git config --list
```

```
git config --global --list
```

**How Do You Open the Default Git Config File?**  

```
git config --global -e
```

**Set the default branch name**  

```
git config --global init.defaultBranch main
```