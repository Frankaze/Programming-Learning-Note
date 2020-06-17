# Clone Repository Fails From GitHub.com And GitLab.com by SourceTree

## Issue
When you generate ssh key by SourceTree and import into GitHub.com or GitLab.com, you clone remote repositories unsuccessfully.

## Cause
SourceTree writes the wrong Host and HostName into  **config** in **~/.ssh**. It uses account and remote. For example:

```
# --- Sourcetree Generated ---
Host Frankaze-GitHub
HostName github.com
```

## Solution
Edit the **config** in **~/.ssh** and correct Host and Hostname as below:

- GitHub.com

```
# --- Sourcetree Generated ---
Host github.com
HostName github.com
```

- GitLab.com

```
# --- Sourcetree Generated ---
Host gitlab.com
HostName gitlab.com
```
