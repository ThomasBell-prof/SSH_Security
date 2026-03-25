<h2 align="center"><span style="white-space: nowrap;">📚👨🏽‍🎓 Using SSH Keys to Manage Multiple GitHub Identities 🔐</span></h2>

> A Developer’s Guide to Multi‑GitHub SSH Configuration
>
> > by: Thomas Bell

### Why?:

> The purpose of this guide is to help those with multiple GitHub accounts whether professional or personal on a single computer to start using SSH keys for more secure accessibility.

- Industry Standard
- Clean and Scalable
- No login / logout switching necessary
- Supports unlimited user accounts
---

### 1️⃣ Generate SSH keys for each account

> Click copy and paste the code in your terminal and press enter, one at a time to create each ssh key.
>
> > The following commands creates a new SSH key pair, a secure way to authenticate with GitHub without typing your password.

#### Professional

```bash
ssh-keygen -t ed25519 -f ~/.ssh/github_professional_key -C "your-professional-email@provider.com"
```

> -t specifies the type of key to generate.

#### Personal

```bash
ssh-keygen -t ed25519 -f ~/.ssh/github_personal_key -C "your-personal-email@provider.com"
```

> ed25519 is a modern, secure and fast algorithm preferred over old types like RSA.

#### Freelance

```bash
ssh-keygen -t ed25519 -f ~/.ssh/github_freelance_key -C "your-freelance-email@provider.com"
```

> -f sets the file name and location for the key pair, ultimately creating a public and private key. -C adds a comment to Github so that it may be easily identifiable.
---

### 2️⃣ Create SSH Config file

> Click copy and paste the code in your terminal and press enter to create the ssh config file.

```bash
chmod 600 ~/.ssh/config
chmod 700 ~/.ssh
```

> What the above code does:
>
> > It ensures the config file is readable/writable only by you and the directory is only accessible by you. If you run the above code and the files already exists, it will not hurt anything.

```bash
code ~/.ssh/config
```

> This adds the config file even if it doesn't exist and opens it in vs-code.
---

### 3️⃣ Edit Config file

- vs-code allows you to use the same config file to add multiple accounts
    > Click copy and paste into your config file.

```yaml
# Professional Github account
Host github-professional
HostName github.com
User git
IdentityFile ~/.ssh/github_professional_key

# Personal Github account
Host github-personal
HostName github.com
User git
IdentityFile ~/.ssh/github_personal_key

# Freelance Github account
Host github-freelance
HostName github.com
User git
IdentityFile ~/.ssh/github_freelance_key
```

> Be sure to save the file before exiting
---

### 4️⃣ Setup Github SSH

 🐙 Login to your "Professional" GitHub account

 ↳ 👤 Click your profile picture in the top right corner

 ↳ ⚙️ Select **Settings**

 ↳ 🔐 Choose **SSH and GPG keys**

 ↳ ➕ Click **New SSH key**

- Give the key a title
- Key type = Authentication Key
- For the Key box you need to copy your key and paste it there
> Let's do this step programmatically from your terminal...
```bash
cat ~/.ssh/github-professional_key.pub
```

↳ Click **Add SSH key** 
> Repeat step 4 for each account you have and remember to call the appropriate public key (personal, freelance, etc.)
---

### 5️⃣ Add Keys to the SSH Agent

- In your vs-code terminal
```bash
eval "$(ssh-agent -s)"
```

```bash
ssh-add ~/.ssh/github-professional_key
```
> Repeat step 5 for each account

- You can use...
```bash
ssh-add -l
```
 - to list all active agents
---

### 6️⃣ Test

- In your vs-code terminal

```bash
ssh -T git@github-professional
```

```bash
ssh -T git@github-personal
```

```bash
ssh -T git@github-freelance
```

- If everything was done correctly up unto this point, you should receive a terminal message of:
```diff
+ Hi username! You've successfully authenticated, but GitHub does not provide shell access.
```
---

### 7️⃣ 🏁 Last step - Clone your Repo

```bash
git clone git@github-professional:"your-professional-username"/"your-professional-repo".git
```
> You are done at this point.  Happy coding and good luck!
---

#### For your information

> If at any time you made a mistake and need to delete a key from your machine, enter the following code.
```bash
ssh-add -d ~/.ssh/github-professional_key
```

> If you want to delete all your keys and go back to entering your password everytime with Github ☹️
```bash
ssh-add -D
```
---

I hope this repo has been helpful.  Thank you!