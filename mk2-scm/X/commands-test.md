# X — COMMANDS TEST (MK2-SCM)
PASS ≥ 7/10

Цел: да изпълняваш основните Git команди без подсказване и да интерпретираш резултата.
Работи във VM (Ubuntu).

## Commands (тренирай ги, после тест без гледане)
1) Проверка статус и промени
```bash
git status
git diff
```

2) Staging и unstage
```bash
git add <file>
git add -p
git restore --staged <file>
```

3) Commit и история
```bash
git commit -m "msg"
git log --oneline --graph --decorate --all
```

4) Branching
```bash
git switch -c feature-x
git switch main
git branch
```

5) Merge
```bash
git merge feature-x
```

6) Remote (ако има)
```bash
git remote -v
```

## TEST ITEMS (10 точки)
Отговори/демонстрирай без подсказване:
1) Как разбираш какво е staged vs unstaged? (status)
2) Как виждаш unstaged diff? (diff)
3) Как stage-ваш част от файл? (add -p)
4) Как махаш файл от staging без да губиш промяната? (restore --staged)
5) Как правиш commit с message?
6) Как виждаш графа на историята?
7) Как създаваш и сменяш към нов branch?
8) Как се връщаш на main?
9) Как merge-ваш feature branch в main?
10) Как проверяваш дали има remote?

## PASS CRITERIA
Commands Test = PASS ако:
- ≥ 7/10 items са изпълнени/отговорени правилно
- няма объркване на staging vs working tree
- можеш да обясниш какво прави всяка команда
