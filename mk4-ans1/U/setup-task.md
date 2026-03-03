# U — SETUP TASK (MK4-ANS1) — VM (Ubuntu 24.04)

Цел: да подготвиш Ansible във VM и да потвърдиш, че може да работи поне върху localhost.

## A) Влизане във VM (Host)
```powershell
cd .\vm
vagrant ssh
```

## B) Install / Verify (във VM)
```bash
sudo apt-get update
sudo apt-get install -y ansible openssh-client
ansible --version
ansible-playbook --version
ssh -V
```

## C) Localhost smoke test
```bash
ansible localhost -m ping -c local
```
Забележка: `-c local` казва на Ansible да работи локално (без SSH), за да докажем, че Ansible engine работи.

## D) Create minimal inventory file (optional, но препоръчително)
```bash
mkdir -p ~/mk4-ans1-lab
cat > ~/mk4-ans1-lab/inventory.ini <<'INI'
[local]
localhost ansible_connection=local
INI
cat ~/mk4-ans1-lab/inventory.ini
```

## PASS CRITERIA
Setup Task = PASS ако:
- `ansible --version` работи
- `ansible localhost -m ping -c local` е PASS (SUCCESS)
- имаш inventory.ini (ако го правиш) без грешки
