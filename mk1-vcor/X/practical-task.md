# X — PRACTICAL TASK (MK1-VCOR)

Цел: да създадеш и валидираш Ubuntu VM с Vagrant и да докажеш CPU/RAM вътре в VM.

## Steps (Host → VM)
1) Влез в `vk-7x\vm\` (Host).
2) `vagrant init bento/ubuntu-24.04`
3) В `Vagrantfile` задай ресурси:
   - CPUs: 2
   - RAM: 4096
4) `vagrant up`
5) `vagrant ssh`
6) Във VM изпълни командите за валидация:

```bash
nproc
free -h
uname -a
ip a
```

7) Излез от VM: `exit`
8) На Host провери: `vagrant status`

## PASS CRITERIA
Practical Task = PASS ако:
- VM стартира успешно (`vagrant up` без runtime грешки)
- `vagrant ssh` работи
- `nproc` показва 2 (или стойността, която си задал)
- `free -h` показва ~4GB (или близко спрямо зададеното)
- имаш мрежов интерфейс във `ip a`
