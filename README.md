# Вики Гранита

Вики сервера Гранит — она же раздел `/wiki` на сайте. Устроена как у PlasmoRP ([Plasmo-RP/wiki](https://github.com/Plasmo-RP/wiki)):
страницы — файлы `.mdx` (Markdown + вставки), сайт собирает из них меню, оглавление «На этой странице», «Назад / Далее»,
ссылку «Редактировать на GitHub» и дату последнего обновления (по последнему коммиту файла).

Нашли ошибку или хотите дополнить — откройте пулл-реквест. После слияния правки появятся на сайте.

## Структура

```
pages/
  index.mdx                     → /wiki (главная вики)
  100-getting-started/
    index.mdx                   → /wiki/getting-started (страница раздела)
    100-bedrock.mdx             → /wiki/getting-started/bedrock
  300-features/
    275-worlds/                 → подраздел (вложенность любая)
      index.mdx
      100-art.mdx               → /wiki/features/worlds/art
assets/
  rules/grief.png               → /assets/rules/grief.png
```

- Число в начале имени — порядок в меню (100, 200, 300 — чтобы было куда вставить новое), в адрес не попадает.
- В начале файла — заголовок для меню:

  ```
  ---
  title: "Начать игру"
  ---
  ```

- `group: true` во frontmatter `index.mdx` — раздел-группа: в меню жирный заголовок, страницы под ним видны всегда.
  Папка без `index.mdx` — тоже группа.
- Картинки и файлы — в `assets/`, в тексте: `![](/assets/rules/grief.png)` (png, jpg, gif, webp, mp4, webm, zip).

## Вставки

Те же имена, что у PlasmoRP:

```mdx
<FatLink href="/profile">Получить проходку</FatLink>          крупная ссылка со стрелкой

<CustomBlock type="danger">**3 красных варна = бан**</CustomBlock>
                                                               цветная плашка: danger, warn, info, success

<Note type="warning" title="Важно">Текст</Note>                заметка с заголовком: note, tip, warning

<CollapseBlock>
<Collapse summary="Короткое правило">Подробная версия</Collapse>
<Collapse summary="Ещё правило">…</Collapse>
</CollapseBlock>                                               раскрывающиеся пункты через линии (как правила)

Нажмите :kbd[V]                                                клавиша
```

Таблицы, списки, `код`, ссылки — обычный Markdown (GFM). Между вставкой и текстом внутри неё оставляйте пустую строку.
