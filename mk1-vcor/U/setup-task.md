# U — SETUP TASK (HOST)

Цел: Host да е готов за VirtualBox + Vagrant + Git, и Hyper-V да не пречи на VirtualBox.

## A) Hyper-V проверка (трябва Off)
```powershell
bcdedit /enum | findstr /I hypervisorlaunchtype
```

Очакване: `hypervisorlaunchtype    Off`

Ако е `Auto`, поправка (изисква Admin + рестарт):
```powershell
bcdedit /set hypervisorlaunchtype off
```

## B) Проверка на инструментите (версии)
```powershell
VBoxManage --version
vagrant --version
git --version
```

## C) Provider sanity (VirtualBox)
```powershell
vagrant plugin list
```

## D) Проектна VM директория (изпълнявай Vagrant оттук)
```powershell
New-Item -ItemType Directory -Force .\vm | Out-Null
Set-Location .\vm
```

## E) Мини-проверка на Vagrant (без VM старт)
```powershell
vagrant -v
```

## PASS CRITERIA
Setup Task = PASS само ако:
- Hyper-V е Off (или е приложен fix и след рестарт е Off)
- `VBoxManage`, `vagrant`, `git` връщат версии без грешка
- `.\vm\` директорията е създадена и си вътре в нея
