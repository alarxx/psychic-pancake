---
creation_time: 2024-07-13 06:17
parents:
  - "[[Git]]"
  - "[[GitHub]]"
---
Fork of [[freeCodeCamp.org (Youtube) - Git and GitHub for Beginners - Crash Course]].

# Installation
```sh
sudo apt install git
```

# Initialization project with Git

```sh
cd /home/john/Git   
mkdir MyProject  
ls  
MyProject  
cd ./MyProject/  
# ~/Git/MyProject
git init   
```
**Output:** 
hint: Using 'master' as the name for the initial branch. This default branch name is subject to change. To configure the initial branch name to use in all of your new repositories, which will suppress this warning, call: 
==change default name of initial branch==
```sh
git config --global init.defaultBranch <name>
```
Names commonly chosen instead of 'master' are 'main', 'trunk' and 'development'. The just-created branch can be ==renamed== via this command: 
```sh
git branch -m <name>
```
	`-m` - `--move`

Initialized empty Git repository in /home/john/Git/MyProject/.git/

```sh
git help branch
```

---

# Configuration

```sh
git config --global user.name "John Doe"
git config --global user.email johndoe@example.com
```
Если нужно идентифицироваться по разному в разных проектах, то пишем без `--global`.

Default branch name:
```sh
git config --global init.defaultBranch <name>
```

Default editor:
```sh
git config --global core.editor emacs
```

Checking Your Settings:
```sh
git config --list
# specific key’s value
git config user.name
```

Links:
- Github Docs: [Setting user.name](https://docs.github.com/en/get-started/getting-started-with-git/setting-your-username-in-git);
- Git: [Configuration](https://git-scm.com/book/en/v2/Customizing-Git-Git-Configuration);
- Git: [Getting Started](https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup);

---

# Workflow

![[Screenshot_20240721_121008.png|500]]

---

**Configure SSH-keys** 
-> [[Git - SSH to GitHub Remote Repositories]]
-> Как работает SSH: 
- [[SSH - from Telegram, Wikipedia - 01-06-2024]]
- [[Secure Shell Protocol (SSH)]]

---

Initialize locally:
```sh
git init
```
or clone remote repository:
```sh
git clone git@github.com:user/repo.git
```

---

Storage and commit changes:
```sh
git add .
git commit -m "message title name" -m "what and why description"
```



If you're in local repository:
```sh
git remote add <origin> <git@github.com:user/repo.git>

git remote -v 
```
Добавление удаленного репозитория GitHub. Основной обычно под именем origin. Названия для удаленных репозиториев могут быть полезными при использовании внешних репозиториев как модули.

```sh
git push -u <origin> <master>
```
 `-u` - is "upstream", means setting default branch origin, so now we can just type:
```sh
 git push
```


А что если выполнить:
```sh
git branch --list
```

----

# Git Branching

**Master branch** - name convention for "Main" branch.

**Feature branch** - another branch, at first code the same, we can make updates to the feature branch so those changes will only be seen in feature branch, each individual branch only keeping track of what changes are made on its own branch. It is useful because it allows us work in somewhat like sandbox area before we merge it back into the main branch of the code-base, so we won't be able to brake main branch, it is helpful when we have many different people working in the same repository an once. 

**Hot Fix Branch** 


![[Screenshot_20240721_123049.png]]

----

**Commands**

To see branches:
```sh
git branch
```

To create a new branch, also can use `switch -c`:
```sh
git checkout -b feature-11-description
```

To delete branch:
```sh
git branch -d имя_ветки
```

`checkout` is using for switching (changing) between branches, also can use `switch`:
```sh
git checkout master
```

Get back to newly created branch:
```sh
git checkout feature-11-description
git branch
```

Change something in the code-base, then:
```sh
git status
clear
# cls

git add .
git commit -m "updated"
```

Check that nothing changed in master branch:
```sh
git checkout master
```

What changes have been made:
```sh
git diff checkout feature-11-description
```
`---` - минусы показывают каких изменений нет в настоящей ветке, то есть **добавленные** строки
`+++` - получается то, что есть в настоящей, получается это **удалили** в другой ветке.


We can merge locally:
```sh
git merge feature-11-description
```

But we are going to push on that changes up to GitHub and then make a Pull Request (PR):
```sh
git checkout feature-11-description
git status
git push --set-upstream origin feature-11-description
```
`--set-upstream` = `-u`


**Pull Request (PR)** - это функционал GitHub, который делается через web-интерфейс GitHub. Очень удобный интерфейс. Можно задавать вопросы, комментировать конкретные строки кода и т.д.


---

# Questions

##### **`checkout` vs. `switch`?**

Я помню, что при switch-е между ветками у нас удалялись все внесенные изменения в других ветках? Не знаю.

Кажется, `switch` является более новой версией `checkout`. У `checkout` большая функциональность. `checkout` может всё, что может `switch`.

Создание и переключение на новую ветку:
```sh
# ---switch---
git switch -c new-feature-branch
# git switch feature-branch

# ---checkout---
git checkout -b new-feature-branch
# git checkout feature-branch
```

---
##### **Ещё есть вопрос что за `fetch`?**

`fetch` просто загружает отдельно репозиторий, который потом можно анализировать, в то время, как `pull` это про слияние (pull=fetch+merge).

Добавляем удаленный репозиторий
```sh
git remote add myrepo https://github.com/user/repo.git
```

Загрузить изменения из удаленного репозитория, но не merge-ит с локальными ветками:
```sh
git fetch myrepo
```

Запулить - fetch+merge:
```sh
git pull myrepo <branch>
```

---

# Merge conflicts

**`stash`** - временное хранение, но не `commit`.

Merge конфликты появляются, когда в разных ветках работали над одними и теми же файлами, поэтому Git не знает что с ними делать.

```sh
git checkout my-branch
git diff master
git merge master
```

Разрешаем конфликты в файлах.

Дальше:
```sh
git status
git diff
git commit -am "merged with master"
# add + message (but not newly created files)
```


Я не совсем понял. Кажется проверяется на конфликты не весь файл, а именно изменения. То есть обе стороны должны изменять строку, чтобы получился merge conflict. На счет полного удаления файла я хз, кажется там можно даже не заметить и замерджить как есть.

if conflict in file:
```python
<<<<<<< HEAD
print("Hello, world!")
======= 
print("Привет, мир!")
>>>>>>> branch
```

Conflict when deleting a file:
```sh
git merge delete-pancake-file 
```
CONFLICT (modify/delete): psychic-pancake.md deleted in delete-pancake-file and modified in HEAD.  
Version HEAD of psychic-pancake.md left in tree.  
Automatic merge failed; fix conflicts and then commit the result.


---

# Undo 

**Undo staging for a commit (undo add):**
```sh
git status
# Changes not staged for commit:
# modified: file
git add ./file
git status
# Changes to be committed:
# modified: file

git reset ./file
git status
# Changes not staged for commit:
# modified: file
```


**Undo commit:**
```sh
git add .
git commit -m "updated"
```

```sh
git reset HEAD~1
# git reset to one commit back from current HEAD commit
```
	`HEAD` - pointer to current commit, 
	`~1` point back one commit 
Чаще всего, HEAD это тот commit, который вы ошибочно сделали и хотите откатить.


to go at specific commit:
```sh
git log
# check the hash of commit you want
git reset <hash>
```

Изменения остаются, а commit и stage (индекс) удаляются.

`reset` имеет флаги
	`--soft` - удаляет commit, а изменения остаются в индексе
	`--mixed` - default, изменения не добавлены в индекс
	`--hard` - изменения удаляются

Чтобы полностью откатить до определенного коммита, unstage (удалить из индекса) и удалить все изменения:
```sh
git reset --hard <hash>
```


---

Создаст коммит и отменит изменения коммита
```sh
git revert commit_hash
```

---

# Forking

Fork - это ответвление в **отдельный репозиторий** независимый от основных авторов проекта. Но, Fork - это **не ветка**.

Fork в основном используется, если хочешь **полностью скопировать**, внести крупные изменения и не собираешься merge-ить с основной веткой проекта, теперь это твой проект. 

Но, Fork может вести себя точно также как ветка, можно за-merge-ить Fork-репозиторий с репозиторием основного проекта.

Fork это функционал GitHub. 

---

# subtree
https://docs.github.com/en/get-started/using-git/about-git-subtree-merges

git subtree могут быть полезны для импортирования репозиториев, как библиотек или модулей. Ещё, например, если ты fork-нул репозиторий, изменил и используешь у себя в проекте. В случае с fork-ом удобно соблюдать условия лицензии LGPL, например, то есть в таком случае ты работаешь с библиотекой на расстоянии вытянутой руки.