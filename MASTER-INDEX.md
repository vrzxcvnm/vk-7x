# VK-7X — MASTER INDEX

## PURPOSE
VK-7X е структурирана DevOps инженерна система от 8 последователни модула.  
MK1 създава Virtual Core (Ubuntu VM чрез Vagrant).  
Всички останали модули (mk2 → mk8) се изпълняват вътре в тази VM.  
Host машината служи като hypervisor + orchestration слой.

---

## PROJECT STRUCTURE (DEEP TREE)
vk-7x/
- MASTER-INDEX.md
- README.md
- mk1-vcor/
- mk2-scm/
- mk3-xci/
- mk4-ans1/
- mk5-doc/
- mk6-k8s/
- mk7-iac/
- mk8-sc1/

Всеки модул има:
- core.md
- U/ (study-test.md, setup-task.md)
- X/ (commands-test.md, practical-task.md)
- FINAL.md

---

## GLOBAL STANDARD (VALID FOR EVERY MODULE)
core.md съдържа задължително секциите в този ред:
1) INDEX
2) THEORY
3) INSTRUCTIONS
4) TO COMPLETE
5) FINAL

U съдържа:
- STUDY TEST
- SETUP TASK

X съдържа:
- COMMANDS TEST
- PRACTICAL TASK

PASS = ≥ 70% общо от U + X.  
След PASS → Git Commit на цялата папка за модула.

---

## HOST REQUIREMENTS (INSTALL BEFORE MK1)
### Mandatory
- Hyper-V: OFF
- VirtualBox (Type 2 Hypervisor)
- Vagrant
- Git for Windows
- PowerShell (Admin access)

### Recommended
- Windows Terminal
- PowerShell 7
- VS Code
- 7-Zip

### Host Checks
```powershell
VBoxManage --version
vagrant --version
git --version
bcdedit /enum | findstr /I hypervisorlaunchtype