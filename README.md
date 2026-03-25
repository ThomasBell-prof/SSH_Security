# SSH Keys for Multi-Github account Authentication

> A How to Guide - by: Thomas Bell

## Reasons:

> The purpose of this guide is to help those with multiple GitHub accounts whether professional or personal on a single computer to start using SSH keys for more secure accessibility

- Industry Standard
- Clean and Scalable
- No login / logout switching necessary
- Supports unlimited user accounts
---

### 1. Generate SSH keys for each account

> Click copy and paste the code in your terminal and press enter, one at a time to create each ssh key

#### Professional
```bash
ssh-keygen -t ed25519 -f ~/.ssh/github_professional_key -C "your-professional-email@provider.com"
```

#### Personal
```bash
ssh-keygen -t ed25519 -f ~/.ssh/github_personal_key -C "your-personal-email@provider.com"
```

#### Freelance
```bash
ssh-keygen -t ed25519 -f ~/.ssh/github_freelance_key -C "your-freelance-email@provider.com"
```
---

### 2. Create SSH Config file

> Click copy and paste the code in your terminal and press enter to create the ssh config file

```bash
chmod 600 ~/.ssh/config
chmod 700 ~/.ssh
```
> what the above code does: it ensures the config file is readable/writable only by you and the directory is only accessible by you
* Note: if you run the above code and the files already exist, it will not hurt anything.

```bash
code ~/.ssh/config
```
> this adds the config file even if it doesn't exist and opens it in vs-code
---

### 3. Edit Config file
- In VS-code you can use the same config file to add multiple accounts

```yaml
Host github-professional
HostName github.com
User git
IdentityFile ~/.ssh/github_professional_key

Host github-personal
HostName github.com
User git
IdentityFile ~/.ssh/github_personal_key

Host github-freelance
HostName github.com
User git
IdentityFile ~/.ssh/github_freelance_key
````