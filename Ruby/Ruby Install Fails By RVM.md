# Ruby Install Fails By RVM

## Issue

Fails to install Ruby by RVM on macOS 10.13 High Sierra. The error message in installation log shows:

```
Error: Could not create /usr/local/Cellar
Check you have permission to write to /usr/local
```

## Cause

RVM install Ruby via Homebrew. User needs permission to create or access `/usr/local/Cellar`. Because macOS 10.13 High Sierra does't allow user to chown `/usr/local`, both of the following shells don't work:

```bash
sudo chown -R $(whoami) /usr/local
```
```bash
sudo chown -R $(whoami) $(brew --prefix)/*
```

## Solution

Reinstall Homebrew can solve problem. First, unintall Homebrew:

```bash
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/uninstall)"
```

And install Homebrew again:

```bash
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```