---
name: humanizer-ru
description: >-
  Use when editing Russian LLM text to remove канцелярит, calques, AI tells;
  preserve facts. Especially before publishing Telegram channel posts.
---
# Humanizer-RU (сеть каналов)

Полный скилл лежит здесь — читай и следуй ему целиком:
`skills/humanizer-ru/SKILL.md`

Сканер (если нужен балл):
`python3 skills/humanizer-ru/scripts/scan.py файл.txt --genre news`

Для новостных/научпоп постов сети всегда жанр `news`. Типографика сети важнее дефолтов: только `""` и дефис `-`.

Доп. вариант с Telegram-ориентиром: `skills/humanizer-ru-tg/SKILL.md`.
