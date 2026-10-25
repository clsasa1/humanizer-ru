# Что откуда взято

Сборка из архива источников сети. Файлы в `skills/` скопированы как есть.
Правки только в `workflows/`: абсолютные пути `/workspace/media_network/...`
заменены на пути от корня этого репозитория. Пустые каталоги архива
`docs/` и `references/` в корне ничего не содержали; `references/` в сборку
не вошёл.

Новых редакционных правил эта сборка не добавляет. Корневые `README.md` и
`SKILL.md` только маршрутизируют к уже существующим файлам.

## Источники

| Каталог | Что это | Лицензия и автор в архиве |
|---|---|---|
| `skills/humanizer-ru` | Ядро v3.32.0: SKILL, каталог на 67 паттернов, сканер `scripts/scan.py`, пустой `edit-log.md`. Во frontmatter `license: MIT`, отдельного файла LICENSE нет. | MIT, правообладатель в архиве не назван |
| `skills/humanizer-ru-tg` | Публичный humanizer-ru v1.6.0: один SKILL с русскими и английскими правилами, `humanizer.ru.md` / `humanizer.en.md`, `build_single.py`, команды `audit` и `humanize`. | MIT, Copyright (c) 2026 thevseprod. Репозиторий: https://github.com/thevseprod/humanizer-ru |
| `skills/anti-ai-slop-writing` | Natural writing v3.0.0, модули `references/en`, `ru`, `uk` и `references/core/craft.md`. | Файла LICENSE в архиве нет |
| `skills/redaktura` | Редактура v0.4.1, проходы от смысла к нейротексту. | Авторы во frontmatter: Люда Сарычева, Никита Архипов. Файла LICENSE нет |
| `skills/post` | Короткий пост v0.1.4. Шаг 5а уже ссылается на `../redaktura/references/neirotekst.md`. | Те же авторы. Файла LICENSE нет |
| `skills/voice-dna-builder` | Мастер voice-скилла, скрипты корпуса и Telegram-экспорта, `references/universal-anti-slop.md`. | MIT, Copyright (c) 2026 Alexey Ponomar. README указывает https://github.com/ponomr/voice-dna-builder |
| `skills/blog-post-writer` | Пост в голосе по CSV/архиву. Рядом пример `examples/style-guide.kgrbnv.md`. | Файла LICENSE нет |
| `network/` | Формат постов сети (эталон @horoshnews) и анти-ИИ чеклист. Чеклист называет источники: Wikipedia:Signs of AI writing, vc.ru, Т-Ж, fillikam.com, Pressfeed; ориентир стиля t.me/s/rozetked, t.me/s/exploitex. | Часть архива сети, отдельной лицензии нет |
| `workflows/` | Короткие оркестраторы sand: tg-post-human, humanizer-ru, redaktura-post, anti-ai-slop-writing, blog-post-writer, voice-dna-builder. Ссылка `sand-workflow:tg-post-human` оставлена как есть. | Часть архива сети |

Корневой `LICENSE` — MIT на сборку (README, корневой SKILL, workflows, network, docs). Вложенные LICENSE не заменяют его и не заменяются им. У `post`, `redaktura`, `anti-ai-slop-writing` и `blog-post-writer` в архиве лицензии не было: прежде чем выносить их отдельно, лицензию стоит подтвердить у авторов.

## Дубли

Один и тот же приём описан в нескольких местах. Сборка их не сливала.

**Два humanizer с одним `name: humanizer-ru`.**

- `skills/humanizer-ru` — редактура русского текста, «удаляй, не дописывай», матрица жанров, факт-замок, сканер. Для жанра `news` часть жёстких запретов, включая длинное тире, сканер глушит.
- `skills/humanizer-ru-tg` — переписывание RU/EN по быстрому списку. Длинное тире названо главным маркером и в постах заменяется. Первая строка обязана работать в превью Telegram.

Оркестратор `workflows/humanizer-ru` уже выбирает ядро основным, tg-вариант дополнительным, жанр сети — `news`, типографику сети — важнее дефолтов ядра.

**Тире.** Три уже записанные позиции расходятся, и сеть это не сглаживает:

- чеклист `network/anti_ai_checklist_network.md`, правило 0: в постах нет «ёлочек», длинного и среднего тире, символа `…`, неразрывных пробелов;
- `skills/redaktura/SKILL.md` и `skills/redaktura/references/neirotekst.md`: тире и ёлочки — грамотная типографика, не признак ИИ, не трогать;
- `skills/anti-ai-slop-writing/references/ru/rules.md`: грамматическое тире нормально, одно слово или один список не банить.

Для caption сети уже заданный приоритет такой: типографика из `workflows/humanizer-ru` и правило 0 чеклиста. В статью или юридический текст этот приоритет оркестраторы не переносят.

**Стоп-фразы и «не X, а Y».** Параллельные списки, пороги разные:

- жёсткие запреты `skills/humanizer-ru/SKILL.md` и каталог `references/catalog.md`;
- быстрый список `skills/humanizer-ru-tg/SKILL.md`;
- `skills/anti-ai-slop-writing/references/ru/rules.md`, плюс `banned.md` и `patterns.md` (скилл просит не грузить их по умолчанию);
- `skills/redaktura/references/neirotekst.md` (лимит антитез по объёму), `shtampy.md`, `slovo.md`;
- шаг 5а в `skills/post/SKILL.md` (для поста до 1000 слов максимум одна антитеза);
- `skills/voice-dna-builder/references/universal-anti-slop.md` (общий слой для сгенерированных voice-скиллов; тире не банить, если ими полон корпус автора);
- пункты 1–8 `network/anti_ai_checklist_network.md`.

**«Напиши пост».** `skills/post` собирает хук, тело и финал для соцсети. `skills/blog-post-writer` пишет в голос по архиву и без архива работать отказывается. Корневой SKILL разводит их так, как уже написано в этих двух файлах и в `workflows/blog-post-writer`.

**Куда класть голос сети.** `workflows/voice-dna-builder` просит сохранить Voice DNA Exploit / Droidder / Хорош в `skills/voice-network/`. Каталога в архиве не было, здесь он не создавался.

## Чего в архиве не было, хотя скиллы на это ссылаются

Ядро humanizer-ru упоминает файлы, которых в архиве нет. Сборка их не восстанавливала:

- `eval/LOCAL_EDIT_CHECK.md` — из `skills/humanizer-ru/SKILL.md`;
- `eval/run_eval.py`, `scripts/lint_skill.py`, `scripts/bump_release.py` — из `scripts/humanizer_metrics/__init__.py` и шапки `references/catalog.md`;
- раздел README про зависимости сканера, на который ссылаются `scripts/scan.py` и `references/scan.md`. Команды, которые сканер печатает сам (`uvx ru-humanizer`, `pipx install ru-humanizer`, venv с `razdel` и `pymorphy3`), перенесены в корневой README.

`skills/post` и `skills/redaktura` зовут скиллы `redpolitika`, `statya`, `promo`, `ux-copy` и файл `.agents/redpolitika.md`. В архиве их нет. Пока файла редполитики нет, оба скилла и так умеют работать без него.

## Что можно слить дальше

Не сделано в этой сборке, чтобы не смешать расходящиеся правила.

1. Оставить один вход `humanizer-ru`: ядро v3 со сканером, а из tg-варианта забрать только то, чего в ядре нет (английские правила, превью первой строки, чтение вслух для видео). Пока оба `name: humanizer-ru`, установщик скиллов их не различит.
2. Свести стоп-фразы сети в один список и явно пометить, какой порог для caption (чеклист), какой для длинного текста (redaktura / anti-ai-slop). Сейчас порог антитезы в `post` («максимум одна на пост до 1000 слов») мягче, чем чеклист (конструкция без настоящего противопоставления не используется).
3. Зафиксировать типографику одним абзацем для постов сети и не тащить её в `redaktura`, где тире считается нормой грамотности.
4. Положить 20–30 эталонных постов Exploit, Droidder и Хороша через `voice-dna-builder` в `skills/voice-network/`, когда корпус будет под рукой. Чужие посты в репозиторий заранее не клались.
5. Добрать лицензии `post`, `redaktura`, `anti-ai-slop-writing` и `blog-post-writer`.
6. Вернуть в ядро недостающие `eval/` и `lint_skill.py`, если они ещё живут в исходном дереве humanizer-ru: без них каталог ссылается на гейты, которых здесь нет.
