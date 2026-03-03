# U — STUDY TEST (MK3-XCI) (A/B/C)
PASS ≥ 7/10

1) CI gate е:
A) ръчна проверка след deploy
B) автоматична проверка преди merge/commit
C) Docker image

2) YAML най-често се “чупи” от:
A) indentation / tabs / trailing spaces
B) липса на CPU
C) git push

3) yamllint прави:
A) изпълнява playbook-и
B) lint на YAML (стил + базова валидност)
C) създава VM

4) ansible-lint е:
A) linter за Ansible best practices
B) package manager
C) Kubernetes validator

5) `ansible-playbook --syntax-check`:
A) изпълнява задачите
B) валидира синтаксис без изпълнение
C) прави merge

6) Ако yamllint FAIL, правилното действие е:
A) commit и “ще го оправя после”
B) fix и повторно пускане на gate
C) delete repo

7) `.yamllint` файл служи за:
A) описва lint правила/конфигурация
B) описва git remote
C) описва docker registry

8) “lint” vs “validation”:
A) lint = стил/правила; validation = синтаксис/структура
B) lint = runtime; validation = GUI
C) няма разлика

9) Основният риск при пропускане на gates е:
A) по-бърз merge
B) счупени промени да стигнат production
C) по-малко commits

10) Правилният локален gate ред е:
A) commit → после lint
B) lint/validation → после commit
C) push → после syntax-check

## ANSWER KEY
1) B
2) A
3) B
4) A
5) B
6) B
7) A
8) A
9) B
10) B
