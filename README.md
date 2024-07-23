# psychic-pancake
none

psychic-pancake.md:

```sh
sudo apt install git
```

```sh
cd /home/john/Git
mkdir MyProject
ls
MyProject
cd ./MyProject/
# ~/Git/MyProject
git init
```

```sh
git config --global user.name "Alar-q"
git config --global user.email alar.akilbekov@gmail.com
```

```sh
git config --list
```

Rename branch:
```sh
git branch -m python-env
```


Можно посмотреть созданную ветку, почему-то до первого коммита её не видно:
```sh
git branch --list
```

---

Install Python and [[Package Installer for Python (PIP)|PIP]]:
```sh
sudo apt install python3
sudo apt install python3-pip
#sudo apt install python3.8
python3 --version
```

Install Virtual Environment Package:
```sh
sudo apt install -y python3-venv
```

Now can enter project directory:
```sh
cd path/to/project
```

Create environment:
```sh
python3 -m venv .venv
```
	-m - module-name, finds sys.path and runs corresponding .py file

Use this environment:
```sh
source .venv/bin/activate
```

Check if it works:
```sh
pip install numpy
```

---

**Git**

Add this environment to .gitignore:
```sh
echo ".venv" >> .gitignore
```

**To recreate environment**

Firstly, freeze current environment packages:
```sh
pip freeze > requirements.txt
```

To recreate environment in future, run:
```sh
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

---

Hello, World!
```sh
nano hello.py
```
Add:
```python
print("Hello, World!")
```
Run:
```sh
python hello.py
```

```sh
git add .
git commit -m "initial"
git branch -v
```

---

**Remote Repository**

```sh
git remote add origin git@github.com:Alar-q/psychic-pancake.git
```

```sh
git branch -v
# * master d5c86cd initial

git fetch
# From github.com:Alar-q/psychic-pancake
# * [new branch]      main       -> origin/main

git remote -v
# origin  git@github.com:Alar-q/psychic-pancake.git (fetch)
# origin  git@github.com:Alar-q/psychic-pancake.git (push)
```

```sh
git branch
git switch main
# git checkout main
```

```sh
git switch python-env
git push --set-upstream origin python-env
# Охренеть получилось! Но, название херня
```

Merge python-env with main:
```sh
git branch -m python-env

git diff main
git merge main --allow-unrelated-histories

# Resolve merge conflict
git add .
git commit -m "merge with main"
git status
git push origin python-env
```

Make Pull-Request from GitHub.

Then you can delete branch:
```sh
# Local delete branch
git branch -d <branch>
git branch -D <branch>
# Delete remote branch
git push origin -d <branch>
```
