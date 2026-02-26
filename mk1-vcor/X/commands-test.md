# X — COMMANDS TEST (MK1-VCOR)

Цел: да управляваш VM lifecycle с Vagrant (VirtualBox provider) без подсказване.

Работи в `vk-7x\vm\` на Host.

## 1) Initialize (box: bento/ubuntu-24.04)
```powershell
vagrant init bento/ubuntu-24.04
```

## 2) Edit Vagrantfile (resources)
Отвори `.\Vagrantfile` и задай ресурси (пример):
- CPUs: 4
- RAM: 8192

Ако host не позволява — намали, но запиши реалната стойност в FINAL.md.

## 3) Bring up
```powershell
vagrant up
```

## 4) Status
```powershell
vagrant status
```

## 5) SSH into VM
```powershell
vagrant ssh
```

## 6) Exit VM (back to host)
```bash
exit
```

## 7) Halt (stop VM)
```powershell
vagrant halt
```

## 8) Reload (restart VM)
```powershell
vagrant reload
```

## 9) Global status (visibility)
```powershell
vagrant global-status
```

## 10) Destroy (само ако трябва в края)
```powershell
vagrant destroy -f
```

## PASS CRITERIA
Commands Test = PASS ако:
- изпълниш 1→9 без грешка
- можеш да влезеш с `vagrant ssh` и да излезеш коректно
- можеш да обясниш разликата: `halt` vs `reload` vs `destroy`
