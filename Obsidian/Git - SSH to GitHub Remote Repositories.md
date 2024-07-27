---
creation_time: 2024-07-21 22:40
parents:
  - "[[Git]]"
  - "[[GitHub]]"
  - "[[Secure Shell Protocol (SSH)]]"
---
# Generating a new SSH-keys

[Cloning with SSH URLs](https://docs.github.com/en/get-started/getting-started-with-git/about-remote-repositories#cloning-with-ssh-urls)

```sh
ssh-keygen -t ed25519 -C "your_email@example.com"
```
or if **[[ED25519]]** algorithm doesn't supported, may use **[[RSA]]**:
```sh
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

>output:
```
Generating public/private ed25519 key pair. 

Enter file in which to save the key (/user/.ssh/id_ed25519):    
Enter passphrase (empty for no passphrase):    
Enter same passphrase again:    

Your identification has been saved in /user/.ssh/id_ed25519  
Your public key has been saved in /user/.ssh/id_ed25519.pub  
The key fingerprint is:  
SHA256:hex user@email.com  
The key's randomart image is:  
+--[ED25519 256]--+  
+----[SHA256]-----+
```

---

# Questions
##### Passphrase

1. **Зачем нужен passphrase?**
   Passphrase используется для защиты private-key на клиенте. Это дополнительная защита на случай, если private-key оказался у третьей стороны.
   
2. **Как он работает?** 
   Passphrase используется как ключ для [[Symmetric encryption]], по типу [[Data Encryption Standard (DES)|DES]] и [[Advanced Encryption Standard (AES)|AES]].

3. **На какой стадии идет проверка passphrase?**
   На стадии аутентификации клиента сервером. 
   Passphrase расшифрует private-key, который используется для подписи рандомных байтов (challenge) от сервера для аутентификации - работа по типа [[Digital Signature Algorithm (DSA)|DSA]]. 

---

##### [[Least privilege principle]]

Почему-то он писал, что ключи создадутся в `/root/.ssh/`. 

Генерируй SSH-ключи не из root-а, а из пользователя, которым собираешься пользоваться GitHub. 

`git clone` из root-а импортирует репозиторий, который не будет доступен не-root-пользователям, то есть даже используя IDE ты не будешь иметь доступ к коду - useless. 

---

# **After generating SSH-keys**

[Checking for existing SSH keys](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/checking-for-existing-ssh-keys)

```sh
ls ~/.ssh
```
>id_ed25519  id_ed25519.pub

----

1. ssh-agent daemon:
```sh
eval "$(ssh-agent -s)"
```
>Agent pid 59566

2. Add ssh private key to daemon:
```sh
ssh-add ~/.ssh/id_ed25519
```

ssh-agent - это клиент для Linux, управляет private-key и отвечает за аутентификацию.

3. Adding a new SSH key to your GitHub account:
```shell
cat ~/.ssh/id_ed25519.pub
# Then select and copy the contents of the id_ed25519.pub file
# displayed in the terminal to your clipboard
```
публичный ключ даем гитхабу

---

```sh
*** Please tell me who you are.  
  
Run  
  
 git config --global user.email "you@example.com"  
 git config --global user.name "Your Name"  
  
to set your accounts default identity.  
Omit --global to set the identity only in this repository.  
```

---

**[Testing your SSH connection](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/testing-your-ssh-connection)**

```sh
ssh -T git@github.com
# Attempts to ssh to GitHub
```
	-T      Disable pseudo-terminal allocation.