# MK3 — XCI (CI Automation: YAML lint + validation)

## INDEX
MK3-XCI въвежда CI-подобни gate-ове локално: lint + syntax validation за YAML и Ansible.
Цел: да предотвратяваш счупени YAML/Ansible промени преди commit чрез автоматични проверки.
Изход: можеш да пуснеш yamllint + ansible-lint + ansible-playbook --syntax-check и да поправиш violations.

## THEORY

### 1) Защо lint/validation е CI gate (DevOps реалност)
- CI gate = автоматична проверка, която блокира merge/commit ако качеството е под стандарт.
- В DevOps: по-малко runtime инциденти, по-малко “работи при мен”, по-бърз feedback цикъл.

### 2) YAML: не е “само формат”, а source на бъгове
Най-чести YAML проблеми:
- indentation (грешни нива)
- tabs вместо spaces
- trailing spaces
- грешни типове (string vs bool)
- невалиден синтаксис (missing : , списъци)
YAML lint ти дава ранно предупреждение преди runtime.

### 3) yamllint
- Статичен lint за YAML: стил + базова валидност.
- Може да използва config файл (.yamllint), за да фиксираш стандарта.
Типични правила: indentation, line-length, trailing-spaces, truthy.

### 4) ansible-lint
- Статичен lint за Ansible: best practices и рискове.
- Хваща: използване на shell вместо module, липса на become където трябва, weak patterns, deprecated syntax.
- Цел: playbook-ите да са предвидими, идемпотентни и четими.

### 5) ansible-playbook --syntax-check (validation gate)
- Това е “валидатор”, не linter.
- Проверява YAML структура + Ansible syntax без да изпълнява задачите.
- Използваш го преди run и преди commit.

### 6) Gate pipeline (локално CI)
Минималният gate за mk3:
1) yamllint върху YAML файлове
2) ansible-lint върху playbooks/roles (ако има)
3) ansible-playbook --syntax-check
Ако някой gate FAIL → STOP (не минаваш към commit).

### KEY TAKEAWAYS (Study anchors — Study Test е по това)
1) CI gate = автоматична проверка преди merge/commit.
2) YAML е чувствителен към indentation и формат.
3) yamllint проверява YAML стил + базова валидност.
4) ansible-lint проверява Ansible best practices.
5) syntax-check валидира playbook без изпълнение.
6) Fail в gate = не commit-ваш.

## INSTRUCTIONS
1) Прочети THEORY + KEY TAKEAWAYS.
2) U: Study Test (≥7/10) + Setup Task (инсталация на lint/validation инструменти във VM).
3) X: Commands Test (≥7/10) + Practical Task (мини CI gate: yamllint + ansible-lint + syntax-check върху lab repo).
4) Validation на host repo и commit само при PASS.

## TO COMPLETE
PASS изисква:
- Study Test: PASS (≥ 7/10)
- Setup Task: PASS (yamllint/ansible-lint/ansible работят във VM)
- Commands Test: PASS (≥ 7/10)
- Practical Task: PASS (всички gate-ове PASS след fixes + доказателства)

## FINAL
```powershell
git add mk3-xci
git commit -m "mk3-xci: module complete"
git push   # само ако има remote
```
