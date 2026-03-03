# MK2 — SCM (Git Version Control)

## INDEX
MK2-SCM въвежда Git като стандарт за контрол на версиите във VK-7X.
Цел: да разбираш трите зони, историята като граф (DAG), branching/merge и да можеш да мислиш при проблем, не само да изпълняваш команди.
След модула трябва да можеш да диагностицираш състояние с `git status/diff/log`, да решаваш конфликти и да поддържаш чист repo.

## THEORY

### 1) Какво е Git (реалният модел)
Git не е “система за файлове”, а система за snapshot-и.
Всеки commit е пълен snapshot на проекта + метаданни.
Git не пази diff като основна единица — пази състояния.

### 2) Историята като граф (DAG модел — критично)
Commit-ите образуват насочен ацикличен граф (DAG).
- Всеки commit сочи към parent commit.
- Merge commit има два parent-а.
- Branch НЕ е копие на код — той е просто movable pointer.
- HEAD сочи към текущия branch (или директно към commit при detached).
Когато commit-неш, branch pointer се мести напред.

### 3) Трите зони (working → staging → repo)
- Working tree: файловете на диска.
- Staging area (index): какво ще влезе в следващия commit.
- Repository (.git): историята (objects/refs).
Мисловен модел:
Working → add → Staging → commit → Repo

### 4) Как да четеш `git status` (оперативно мислене)
Git status показва 4 категории:
- untracked (не се следят)
- modified (променени, не са staged)
- staged (готови за commit)
- ahead/behind (спрямо remote)
Ако разбираш status, можеш да диагностицираш всичко.

### 5) Diff и диагностика
- `git diff` = разлика working vs staging
- `git diff --staged` = staging vs last commit
- `git log --oneline --graph --decorate --all` = структурата на историята

### 6) Restore vs Reset (decision model)
Ако файл е modified и искаш да го върнеш → `git restore <file>`
Ако файл е staged и искаш да го махнеш от staging → `git restore --staged <file>`
Ако искаш да пренапишеш локална история:
- `git reset --soft` (мести HEAD, пази staging)
- `git reset --mixed` (default, маха staging)
- `git reset --hard` (изтрива всичко локално)
ВАЖНО: Никога не прави reset върху вече push-ната история без политика.

### 7) Branching (истинското значение)
Branch е просто име, което сочи към commit.
`git switch -c feature-x` създава нов pointer.
Branch не копира код — commit-ите се споделят.

### 8) Merge и конфликт
Merge комбинира два клона.
Конфликт възниква когато една и съща част е променена различно.
Процедура:
1) отвори файла
2) реши конфликтните маркери
3) `git add`
4) `git commit`

### 9) Remote (концептуално)
Remote е просто URL + име (origin).
`git push` изпраща commits.
`git pull` = fetch + merge.
Local history и remote history могат да се разминават.

### 10) .gitignore и чистота
Ignore спира бъдещо track-ване.
Ако файл вече е tracked → `git rm --cached`.
Чист repo = `git status` без шум.

### 11) Problem-Solving Framework (най-важното)
При проблем:
1) `git status` — какво се случва?
2) `git diff` — какво точно е променено?
3) `git log --graph` — къде съм в историята?
4) restore/reset/merge според ситуацията.

### Cheatsheet (минимум за PASS)
`git status`
`git diff`
`git diff --staged`
`git add -p`
`git commit -m`
`git log --oneline --graph --decorate --all`
`git switch -c <branch>`
`git merge <branch>`
`git restore <file>`
`git restore --staged <file>`
`git reset --soft|--mixed|--hard`

## INSTRUCTIONS
1) Прочети THEORY и направи схема на DAG + трите зони.
2) U: Study Test (≥ 7/10).
3) Setup: Git във VM + user.name/user.email.
4) X: Commands Test (≥ 7/10) + Practical (branch → commit → merge → доказателство в log).
5) Commit само при PASS.

## TO COMPLETE
PASS изисква:
- Study Test: PASS (≥ 7/10)
- Setup Task: Git работи във VM
- Commands Test: PASS (≥ 7/10)
- Practical Task: PASS (merge без счупена история)
- Host repo: `git status` чист

## FINAL
```powershell
git add mk2-scm
git commit -m "mk2-scm: module complete"
git push   # само ако има remote
```
