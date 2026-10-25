# humanizer-ru

Общая база humanizer-скиллов для русских постов сети Telegram-каналов. Скиллы лежат как пришли из своих источников: этот репозиторий их собирает и говорит, в каком порядке открывать перед постом. Правила редактуры здесь не придуманы заново.

## Как пользоваться

Перед постом открой корневой [SKILL.md](SKILL.md) и пройди пайплайн:

1. Формат сети: [workflows/tg-post-human/SKILL.md](workflows/tg-post-human/SKILL.md) и [network/post_format_network.md](network/post_format_network.md).
2. Хук, тело, финал: [skills/post/SKILL.md](skills/post/SKILL.md).
3. Чистка: [skills/humanizer-ru/SKILL.md](skills/humanizer-ru/SKILL.md). При необходимости рядом [anti-ai-slop-writing](skills/anti-ai-slop-writing/SKILL.md) и [redaktura](skills/redaktura/SKILL.md).
4. Чеклист: [network/anti_ai_checklist_network.md](network/anti_ai_checklist_network.md).

Узкую задачу можно отдать одному скиллу из карты. Тонкие оркестраторы тех же развилок лежат в [workflows/](workflows/).

Сканер ядра, если нужен балл (для новостей и научпопа сети жанр `news`):

```bash
python3 skills/humanizer-ru/scripts/scan.py файл.txt --genre news
```

Ему нужны `razdel` и `pymorphy3`. Если их нет, `scan.py` сам печатает запасной путь (`uvx ru-humanizer` или отдельное окружение). Балл на глаз не ставить: это правила сканера, не вердикт об авторстве. Пока зависимостей нет, редактура идёт по SKILL.md вручную.

## Карта скиллов

| Путь | Зачем |
|---|---|
| [skills/humanizer-ru](skills/humanizer-ru/SKILL.md) | Ядро редактуры русского текста: канцелярит, кальки, нейроследы, факт-замок, сканер. Версия в файле: v3.32.0. |
| [skills/humanizer-ru-tg](skills/humanizer-ru-tg/SKILL.md) | Вариант под Telegram: русский и английский набор, первая строка в превью. Upstream v1.6.0, [thevseprod/humanizer-ru](https://github.com/thevseprod/humanizer-ru). |
| [skills/anti-ai-slop-writing](skills/anti-ai-slop-writing/SKILL.md) | Проза RU/EN/UK без выдуманного голоса. Языковые правила в `references/<lang>/`. |
| [skills/redaktura](skills/redaktura/SKILL.md) | Редактура от смысла к словам (Люда Сарычева, Никита Архипов). Каталог нейротекста: `references/neirotekst.md`. |
| [skills/post](skills/post/SKILL.md) | Короткий пост: одна мысль, хук, тело, финал. Те же авторы. |
| [skills/voice-dna-builder](skills/voice-dna-builder/SKILL.md) | Персональный voice-скилл из реальных образцов и экспорта Telegram. |
| [skills/blog-post-writer](skills/blog-post-writer/SKILL.md) | Пост в голосе автора. Без архива постов не запускать. |
| [network/post_format_network.md](network/post_format_network.md) | HTML-формат сети, хештеги каналов, фишка своего канала. |
| [network/anti_ai_checklist_network.md](network/anti_ai_checklist_network.md) | Чеклист перед публикацией. |

Откуда каждый кусок и что пока дублируется: [docs/MERGE_NOTES.md](docs/MERGE_NOTES.md).

## Лицензия

Сборка репозитория — [MIT](LICENSE). У вложенных скиллов свои уведомления, они остаются на месте: [skills/humanizer-ru-tg/LICENSE](skills/humanizer-ru-tg/LICENSE), [skills/voice-dna-builder/LICENSE](skills/voice-dna-builder/LICENSE).
