
# MK1 — VCOR (Virtual Core)

## INDEX
MK1-VCOR изгражда основната виртуална среда за целия проект.
В този модул се подготвя Windows Host (Hyper-V OFF), инсталират се VirtualBox + Vagrant и се създава Ubuntu VM чрез Vagrantfile.
Тук се въвеждат основите: virtualization, hypervisor, VM vs container, reproducible environment и VM lifecycle.
След завършване трябва да можеш да управляваш VM без подсказване и да различаваш ясно Host vs VM отговорности.
Тази VM ще бъде единствената execution среда за mk2 → mk8.

## THEORY

### Virtualization
Virtualization позволява стартиране на отделна операционна система върху физически компютър чрез виртуален хардуер.
VM има собствен kernel и пълна OS.

### VM vs Container
VM виртуализира хардуер и стартира пълна OS.
Container споделя kernel-а на хоста и изолира процеси (по-лек и по-бърз).
В този проект VM е sandbox средата; контейнерите идват в mk5.

### Hypervisor
Hypervisor управлява ресурсите (CPU, RAM, Disk, Network) и ги разпределя към виртуалните машини.

### Type 1 vs Type 2
Type 1 работи директно върху хардуера.
Type 2 работи върху Host OS.
VirtualBox е Type 2 hypervisor.

### Vagrant
Vagrant автоматизира създаването и управлението на VM чрез Vagrantfile (конфигурация като код).

### Vagrantfile
Конфигурационен файл, който описва box image, CPU, RAM и provider настройки (VirtualBox).

### Reproducible Environment
Среда, която може да бъде създадена идентично на различни машини, което елиминира “при мен работи”.

### VM Lifecycle
Create → Start → Access → Stop → Reload → Destroy

## INSTRUCTIONS
1) Прочети THEORY.
2) Изпълни U (Study Test + Setup).
3) Изпълни X (Commands Test + Practical Task).
4) Ако U PASS и X PASS и Practical PASS → премини FINAL.
5) Направи Git commit за mk1-vcor.

Важно:
- MK1 = Host + VM setup.
- MK2 → MK8 се изпълняват само във VM.
- Един модул = един commit.
- Не смесвай root промени с module commit.

## TO COMPLETE
PASS изисква:
- Study Test: PASS (≥ 5/7)
- Setup Task: PASS (всички проверки + инсталации успешни)
- Commands Test: PASS (VM lifecycle без подсказване)
- Practical Task: PASS (реална валидация на CPU/RAM/OS във VM)
- Структурата на папката е правилна (tree -L 3)

## FINAL
При PASS:

```powershell
git add mk1-vcor
git commit -m "mk1-vcor: module complete"
git push
```
