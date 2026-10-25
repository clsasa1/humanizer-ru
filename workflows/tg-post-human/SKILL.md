---
name: tg-post-human
description: >-
  Use before every Russian Telegram caption/card in the channel network:
  Exploit/Droidder voice, unique channel hook, HTML rich links, no calques.
---
# TG post human (обязательный прогон сети)

Перед caption и карточкой:

1. Одна мысль. Хук первой строкой.
2. **Rich HTML** (`parse_mode=HTML`): жирный хук/ключевые цифры; все ссылки только `<a href="URL">источник</a>` или имя издания — **запрещены** голые URL и doi.org в тексте.
3. Кальки и телеграф — перепиши. Аббревиатуры расшифруй.
4. Фишка только своего канала.
5. Типографика сети: `""` и `-` (в HTML-тексте тоже).
6. Чистка: `skills/humanizer-ru/SKILL.md` + `skills/post/SKILL.md`.
