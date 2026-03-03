# U — SETUP TASK (MK2-SCM)

Цел: Git да е инсталиран и конфигуриран във VM (Ubuntu), така че да можеш да комитваш с валидни author данни.

## A) Влизане във VM
Host:
```powershell
cd .\vm
vagrant ssh
```

## B) Проверка дали Git е инсталиран
VM (Ubuntu):
```bash
git --version
```

Ако липсва (само тогава инсталирай):
```bash
sudo apt-get update
sudo apt-get install -y git
git --version
```

## C) Базова Git конфигурация (във VM)
```bash
git config --global user.name "VK-7X"
git config --global user.email "vk-7x@local"
git config --global init.defaultBranch main
git config --global pull.rebase false
```

Проверка:
```bash
git config --global --list
```

## D) Бързи alias-и (по избор, но препоръчително)
```bash
git config --global alias.st status
git config --global alias.br branch
git config --global alias.co checkout
git config --global alias.sw switch
git config --global alias.lg "log --oneline --graph --decorate --all"
```

## E) Sanity checks (във VM)
```bash
git --version
git config --global user.name
git config --global user.email
git config --global init.defaultBranch
```

## PASS CRITERIA
Setup Task = PASS ако:
- `git --version` работи във VM
- `user.name` и `user.email` са зададени (не празни)
- `init.defaultBranch` е `main`
- нямаш грешки при изпълнение на командите
