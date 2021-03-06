# Правила работы

*Версия 1.0*

Все основные правила работы организации закреплены в наборе видений и резолюций, которые отражают точку зрения организации и принятые решения по всем аспектам ее работы.

## Порядок изменения правил

  1. Формируется "Запрос на изменение" (Request for change, RFC), в котором формулируется проблема и предлагаемое решение.
  2. Запрос обсуждается, в процессе чего в него вносятся исправления или он отменяется.
  3. Формируется итоговое решение в виде новой "Резолюции" (Resolution, RES), нового "Видения" (Vision, VIS) или предложения изменений в существующие.
  4. Проводится процедура принятия или отклонения итогового решения.


## Резолюции

Резолюции являются единственным источником правил работы организации. Прочие программные документы могут обобщать решения, отраженные в резолюциях, упрощать поиск и работу с сопутствующей информацией, но устанавливать иные правила работы они не могут.

Все резолюции размещаются в директории `resolutions` репозитория `rules`. Каждая резолюция имеет номер версии (указывается в самом тексте резолюции), которая увеличивается всякий раз после внесения изменений в данную резолюцию.


## Видения

Видения являются официальной точкой зрения организации по тому или иному вопросу.

Все видения размещаются в директории `visions` репозитория `rules`. Каждое видение имеет номер версии (указывается в самом тексте видения), которая увеличивается всякий раз после внесения изменений в данное видение.


## Запросы на изменение

Запросы на изменение отражают процесс принятия изменений в резолюции и видения. Каждый запрос имеет один из трех возможных статусов: активный (`Active`), принятый (`Accepted`) и отклоненный (`Rejected`).

Все активные запросы на изменение размещаются в директории `rfcs` репозитория `rules`, а принятые и отклоненные в соответствующих поддиректориях: `rfcs/accepted` и `rfcs/rejected`. Текущий статус запроса на изменение также указывается в самом тексте запроса.


## Правила именования файлов

Все резолюции, видения и запросы на изменение представлены в виде отдельного текстового файла (могут быть несколько файлов с текстами на разных языках) или файла и каталога с дополнительными файловыми ресурсами, на которые есть ссылки в основном тексте, с именем вида `<code>-<number>-<title>[.<lang>][.<extension>]`:

  - Код (`<code>`) - это либо `res` для резолюции, `vis` для видения или `rfc` для запроса на изменение.
  - Номер (`<number>`) - это десятичное число с лидирующими нулями (для облегченя сортировки). В рамках одного кода нумерация сквозная.
  - Заголовок (`<title>`) - текст основного заголовка на английском языке без знаков препинания, в котором пробелы заменены на `-`.
  - Код языка (`<lang>`) - двухбуквенный код языка, по стандарту ISO 639, соответствующий основному языку текста файла. Может не указываться только для каталога с общими для всех языков ресурсами.
  - Расширение (`<extension>`) - может указываться для файлов в соответствии с их форматом.

Код и номер совместно формируют уникальный идентификатор любого правила.
