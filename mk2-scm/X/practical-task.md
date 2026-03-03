# X — PRACTICAL TASK (MK2-SCM)

Цел: да направиш мини-репо workflow с branch + merge и да докажеш историята с git log graph.
Работи във VM (Ubuntu).

## Scenario
Създаваш нова папка `mk2-git-lab`, правиш repo, 2 commits на feature branch, merge в main, и показваш графа.

## Steps
1) Създай лаб папка и repo
```bash
mkdir -p ~/mk2-git-lab
cd ~/mk2-git-lab
git init
```

2) Създай файл и първи commit (main)
```bash
printf "VK-7X mk2 lab\\n" > README.md
git status
git add README.md
git commit -m "init: add README"
```

3) Направи feature branch и 2 commits
```bash
git switch -c feature-notes
printf "\\nNotes:\\n- staging vs working tree\\n" >> README.md
git add README.md
git commit -m "docs: add notes section"
printf "- branch + merge basics\\n" >> README.md
git add README.md
git commit -m "docs: extend notes"
```

4) Merge към main
```bash
git switch main
git merge feature-notes
```

5) Доказателство (history)
```bash
git log --oneline --graph --decorate --all
```

6) Repo state clean
```bash
git status
```

## PASS CRITERIA
Practical Task = PASS ако:
- repo има поне 3 commits (1 main + 2 feature)
- merge е успешен (fast-forward или merge commit — и двете са ок)
- `git log --oneline --graph --decorate --all` показва feature историята
- `git status` е clean в края
