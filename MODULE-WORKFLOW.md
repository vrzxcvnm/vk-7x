# VK-7X — MODULE WORKFLOW

Този workflow се следва при ВСЕКИ модул (mk1 → mk8).

Няма прескачане.
Няма частични commits.
Няма импровизация.

---

# PRINCIPLE

1) Първо се създава MODULE INDEX (core.md).
2) После се създава структурата на папката.
3) После се изпълнява модулът стъпка по стъпка.
4) Накрая се валидира.
5) Само при PASS се прави commit.

Без core.md няма модул.

---

# PHASE 1 — MODULE INDEX CREATION

1. Подготвя се пълният core.md, който съдържа:
   - INDEX
   - THEORY
   - INSTRUCTIONS
   - TO COMPLETE
   - U (Study Test + Setup)
   - X (Commands Test + Practical Task)
   - FINAL

2. core.md се преглежда.
3. Ясно е каква е целта и изходът на модула.

---

# PHASE 2 — STRUCTURE CREATION

В директория vk-7x:

Създава се папката:
- mkX-xxxx/

Вътре се създават:
- core.md
- U/
  - study-test.md
  - setup-task.md
- X/
  - commands-test.md
  - practical-task.md
- FINAL.md

Структурата трябва да е идентична за всички модули.

---

# PHASE 3 — ENVIRONMENT CHECK (ВСЕКИ ПЪТ)

## 3.1 Проверка Git

```bash
git status

Трябва да няма незавършени промени от предишен модул.

3.2 Проверка директория
pwd

Трябва да си в vk-7x/ или правилната папка.

3.3 Ако модулът е mk2 → mk8

Влез във VM:

vagrant ssh

Провери:

whoami
pwd

User трябва да е vagrant.

PHASE 4 — THEORY PHASE

Прочети THEORY в core.md.

Увери се, че разбираш:

основните концепции

разликите

защо са важни за DevOps

Без разбиране → не преминаваш към теста.

PHASE 5 — U (UNDERSTANDING)
5.1 STUDY TEST

A/B/C формат

PASS ≥ 70%

Ако FAIL → връщане към THEORY

5.2 SETUP TASK

Инсталиране/конфигуриране на новите инструменти

Проверка на версии

Потвърждение, че работят

Ако има грешка → STOP.

PHASE 6 — X (EXECUTION)
6.1 LEARN COMMANDS

Разбираш всяка команда

Тренираш я

6.2 COMMANDS TEST

Изпълняваш без подсказване

PASS ≥ 70%

6.3 PRACTICAL TASK

Изпълняваш от край до край

Валидираш резултатите

Няма runtime грешки

PHASE 7 — VALIDATION

Преди commit:

Проверка структура:

tree -L 3

Проверка git статус:

git status

Увери се:

всички файлове са на място

няма липсващи секции

няма излишни файлове

PHASE 8 — FINAL COMMIT

Commit се прави само ако:

U ≥ 70%

X ≥ 70%

Практическата задача е PASS

Структурата е правилна

Модулът е напълно завършен

git add mkX-xxxx
git commit -m "mkX-xxxx: module complete"

Няма commit по време на работа.
Няма частичен commit.
Няма WIP.

GLOBAL RULES

mk1 се изпълнява на Host + VM setup.

mk2 → mk8 се изпълняват във VM.

Не инсталирай инструменти от бъдещи модули.

Не работи извън структурата.

Не продължавай при грешка.

GOLDEN RULE

Първо INDEX.
После THEORY.
После U.
После X.
После VALIDATION.
После COMMIT.

Редът не се променя.


---

Това вече е стабилен оперативен стандарт.

Оттук нататък можем да започнем mk2-scm по абсолютно същия шаблон.
