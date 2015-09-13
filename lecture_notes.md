# Create an empty repository

* `git init --bare h4_workshop.git`

# Clone repository

## John

* `git clone h4_workshop.git john_h4_workshop`
* `cd john_h4_workshop`
* `git config user.name "John"`
* `git config user.email "john@hackingthursday.org"`
* `git config --list | grep user.name | tail -1`
* `git config --list | grep user.email | tail -1`

## Mary

* `git clone h4_workshop.git mary_h4_workshop`
* `cd mary_h4_workshop`
* `git config user.name "Mary"`
* `git config user.email "mary@hackingthursday.org"`
* `git config --list | grep user.name | tail -1`
* `git config --list | grep user.email | tail -1`

# Merge

## John

* `echo "# H4 Git Workflows Workshop" > README.md`
* `git add README.md`
* `git commit -m "Add a README file"`
* `git log`
* `git push origin master`

## Mary

* `touch LICENSE`
* `open LICENSE`
* Paste http://opensource.org/licenses/MIT into `LICENSE` file.
* `git add LICENSE`
* `git commit -m "Add the MIT license"`
* `git log`
* `git push origin master`

```
To /home/hackingthursday/Documents/h4_workshop.git
 ! [rejected]        master -> master (fetch first)
```

* `git fetch origin`
* `git push`

```
To /home/hackingthursday/Documents/h4_workshop.git
 ! [rejected]        master -> master (non-fast-forward)
```

* `git merge origin/master`

```
Merge made by the 'recursive' strategy.
 README.md | 1 +
 1 file changed, 1 insertion(+)
 create mode 100644 README.md
```

* `git push`

```
To /home/hackingthursday/Documents/h4_workshop.git
   6b65a07..2ad38cf  master -> master
```

# Pull (rebase)

## John

* `git pull`
* `open LICENSE`

```
-Copyright (c) <year> <copyright holders>
+Copyright (c) 2015 Hacking Thursday
```

* `git add LICENSE`
* `git commit -m "Update year and copyright holders"`
* `git push`

## Mary

* `open README.md`

```
# H4 Git Workflows Workshop
+
+## Agenda
+
+* Centralized workflow
```

* `git add README.md`
* `git commit -m "Add agenda section in README"`
* `git push`

```
To /home/hackingthursday/Documents/h4_workshop.git
 ! [rejected]        master -> master (fetch first)
```

* `git pull --rebase`

```
First, rewinding head to replay your work on top of it...
Applying: Add agenda section in README
```

* `git push`