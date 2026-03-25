# How to properly setup SSH Keys for Multi-Github account Authentication

> by: Thomas Bell

## Intro

- - The purpose of this guide is to help those with multiple GitHub accounts whether professional or personal
  on a single computer to start using SSH keys for more secure accessibility

## Reasons:

- Industry Standard
- Clean and Scalable
- No login / logout switching necessary
- Supports unlimited user accounts

## 1. Generate SSH keys for each account

> Click copy and paste the code in your terminal and press enter, one at
> a time to create each ssh key

### Professional 

```
ssh-keygen -t ed25519 -f ~/.ssh/github_professional_key -C "your-professional-email@provider.com"
```

### Personal 

```
ssh-keygen -t ed25519 -f ~/.ssh/github_personal_key -C "your-personal-email@provider.com"
```

### Professional 

```
ssh-keygen -t ed25519 -f ~/.ssh/github_professional_key -C "your-professional-email@provider.com"
```