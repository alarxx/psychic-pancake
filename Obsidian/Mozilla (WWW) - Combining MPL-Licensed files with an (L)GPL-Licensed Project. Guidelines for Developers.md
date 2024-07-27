---
creation_time: 2024-07-25 02:16
bib_type: "[[Web Article]]"
bib_author:
  - "[[Mozilla Foundation]]"
  - "[[Mozilla]]"
bib_date: 
bib_title: "Combining MPL-Licensed files with an (L)GPL-Licensed Project: Guidelines for Developers"
bib_link: https://www.mozilla.org/en-US/MPL/2.0/combining-mpl-and-gpl/
topics:
  - "[[Mozilla Public License (MPL)]]"
---
# Combining MPL-Licensed files with an (L)GPL-Licensed Project: Guidelines for Developers

## Introduction

When someone combines a file or files licensed under the [Mozilla Public License, version 2.0 ("MPL")](https://www.mozilla.org/en-US/MPL/2.0/) with a project licensed under the GNU General Public License or Lesser General Public Licenses ("(L)GPL"), the MPL's [Section 3.3](https://www.mozilla.org/en-US/MPL/2.0/#distribution-of-a-larger-work) allows distribution of the combined work (the "Larger Work") subject to the terms of both licenses, as long as certain conditions are met.

This document is intended to help developers take advantage of this provision, while still complying with the MPL and (L)GPL and respecting the intent of upstream developers.

## Initial Distribution of MPL-licensed Files As Part Of an (L)GPL-licensed Project

When a developer combines MPL-licensed files into an (L)GPL-licensed project for initial distribution under both MPL and (L)GPL, the MPL-licensed files may be redistributed under one of three different circumstances: 
1. they may be unmodified; 
2. they may be unmodified, but policy requires or the developer prefers to add an (L)GPL header; 
3. or they may be modified.

### Unmodified MPL-licensed Files - MPL-only

In the simplest case, the developer combines unmodified MPL-licensed files into a project with (L)GPL-licensed files to create a Larger Work, and seeks to distribute the resulting combination under the terms of the (L)GPL.

In this case, Section 3.3 of the MPL permits the individual files to be distributed as part of the Larger Work, with no further changes required. The developer may simply leave the file untouched, with all notices intact. The top of the incorporated file would continue to look like [Exhibit A](https://www.mozilla.org/en-US/MPL/2.0/#exhibit-a---source-code-form-license-notice) of the MPL:

```python
"""
This Source Code Form is subject to the terms of the Mozilla Public
License, v. 2.0. If a copy of the MPL was not distributed with this file,
You can obtain one at https://mozilla.org/MPL/2.0/.

Copyright (c) 20xx, MPL Contributor1 contrib1@example.net
"""
```

This is the preferred mechanism, since it makes it easiest to reuse the file in other MPL-licensed projects, as intended by the original author, without prohibiting use in (L)GPL projects.

==Можно использовать MPLed файлы в (L)GPLed проекте. Оставляем все MPLed файлы нетронутыми, сохраняем уведомления.==

### Unmodified MPL-licensed Files - Adding an (L)GPL notice

If a developer combines unmodified MPL-licensed files into a project with (L)GPL-licensed files, and is required by project policy to use an (L)GPL header, or otherwise wants to do so, the developer may add an (L)GPL notice prior to distribution. It is very important that the developer preserve all other copyright and permission notices as they appeared in the original code, as required by the MPL. In this case, the header should look like this:
```python
"""
This Source Code Form is subject to the terms of the Mozilla Public
License, v. 2.0. If a copy of the MPL was not distributed with this file,
You can obtain one at https://mozilla.org/MPL/2.0/.

Copyright (c) 20xx, MPL Contributor1 contrib1@example.net

===
Alternatively, the contents of this file may be used under the terms
of the GNU General Public License Version XX, as described below:

This file is free software: you may copy, redistribute and/or modify
it under the terms of the GNU General Public License as published by the
Free Software Foundation, either version XX of the License, or (at your
option) any later version.

This file is distributed in the hope that it will be useful, but
WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General
Public License for more details.

You should have received a copy of the GNU General Public License
along with this program. If not, see http://www.gnu.org/licenses/.
"""
```


==MPLed файлы можно использовать сразу, но если хотим можем добавить заголовки своих лицензий, дописав после заголовка MPL:==
```
Alternatively, the contents of this file may be used under the terms
of the GNU General Public License Version XX, as described below:
```
==Думаю, добавлять заголовок своей лицензии имеет смысл, только если мы изменяем файл и вступает в силу обязательства MPL.==

  ==copyright добавляется только, когда внесены изменения подлежащие авторским правам==

Note that:

- the MPL header has not been _removed_: Section 3.3 requires that the initial distribution of the MPL-licensed materials, in combination with the (L)GPL-licensed materials, be made under the terms of both licenses.
    
- no new copyright statements ("Copyright (c) 20xx, The New Distributor") have been added, because no copyrightable changes have been made.

    
- adding the additional header has no practical effect, because the file was already usable in combination with (L)GPL code whether or not the header was added.
    

### Modified MPL-licensed Files

A more complicated case occurs when a developer receives a file solely under the terms of the MPL, makes copyrightable changes to that file, and then combines the file with other (L)GPL-licensed files to form a Larger Work. In this situation, the developer may distribute the Larger Work, including the file, under the terms of both the MPL and the (L)GPL, as long as the developer complies with MPL's conditions on distribution, _including the file-level copyleft_.

==Если мы меняем MPLed файлы, то объединенную Larger Work можно распространять под своей лицензией, при условии что соблюдаются условия распространения ПО под MPL - disclose source code of MPLed files==

In order to comply with these terms, great care should be taken to ensure that the new additions made to the MPL-licensed file can be licensed under the MPL, not just the (L)GPL. Additions licensed solely under the (L)GPL would conflict with the terms of the MPL and deprive the upstream MPL project of the ability to reincorporate changes made to the file. For example, copying and pasting content from an (L)GPL-only file into the MPL+(L)GPL file would create a problem. A project may wish to consult with a lawyer to ensure that the terms of the licenses are not violated when new patches are made.

==Убеждайтесь, что дополнения внесенные в MPL-licensed файлы, могут быть лицензированны под MPL, а не только под своей лицензией!==

Once the modifications are made, the top of the file should appear as in the previous Section "[Unmodified MPL-licensed Files - Adding an (L)GPL notice](https://www.mozilla.org/en-US/MPL/2.0/combining-mpl-and-gpl/#unmodified-mpl-licensed-files-adding-an-lgpl-notice)", indicating to recipients that the file is distributed under the terms of both licenses. To the extent new, copyrightable material has been added, and the authors wish to add individual copyright notices, those may be done above the (L)GPL header, alongside the MPL notices (reflecting the fact that such modifications must be under both MPL and (L)GPL).

==Выше рассматривается как сделать Dual Licensing. По желанию в случае изменения MPL-licensed файла можно добавить свой copyright notice рядом с copyright notice-ами MPL, показывая, что copyright действует на две лицензии, а не на одну конкретную, как будет рассматриваться ниже.==

## Modifying and Distributing Files Licensed Under Both the MPL and (L)GPL

Once an MPL-licensed file has been distributed as part of a larger (L)GPL-licensed work, third parties who receive the file may use and redistribute the file under the terms of either license. As a result, new modifications can be provided to recipients under the terms of both licenses, or solely under the terms of the (L)GPL.

==Производный проект производного проекта MPL+(L)GPL может использовать условия двух лицензий сразу и каждой по отдельности.== 

The preferred way to make modifications is to provide them under the terms of both licenses. This mechanism best respects the intentions of the original MPL licensors.

==Рекомендуется добавленные изменения лицензировать под обоими лицензиями.==

### Adding Modifications Under Both Licenses

If a developer wishes to make modifications to a file, and distribute those modifications under the terms of both licenses, they can use the header notice from "[Unmodified MPL-licensed Files - Adding an (L)GPL notice](https://www.mozilla.org/en-US/MPL/2.0/combining-mpl-and-gpl/#unmodified-mpl-licensed-files-adding-an-lgpl-notice)". This preserves the flexibility of other parties to use the file under either MPL or (L)GPL, which can be important when integrating changes back into the original MPL-licensed project.

Note, again, that great care should be taken to ensure that the new additions made to the file can be licensed under both the MPL and (L)GPL; e.g., by making sure that code is not copied and pasted from (L)GPL-only files into MPL+(L)GPL-licensed files.
==Тут проблема может быть получается в том, что если мы закопипастим код из (L)GPL в MPL+(L)GPL, то мы нарушаем условия (L)GPL! ==
### Adding Modifications Under the (L)GPL

A developer who makes copyrightable modifications to a file distributed to them under both licenses, but desires to make the modifications available only under the terms of the (L)GPL, should add the (L)GPL license notice, and any copyright information specific to the (L)GPL-only modifications, _above_ the MPL notice, as follows:
```python
"""
This file is free software: you may copy, redistribute and/or modify
it under the terms of the GNU General Public License as published by the
Free Software Foundation, either version XX of the License, or (at your
option) any later version.

This file is distributed in the hope that it will be useful, but
WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General
Public License for more details.

You should have received a copy of the GNU General Public License
along with this program. If not, see http://www.gnu.org/licenses/.

Copyright (c) 20XX (L)GPL-only Contributor1 gpl@example.org

===
This file incorporates work covered by the following copyright and
permission notice:
===

This Source Code Form is subject to the terms of the Mozilla Public
License, v. 2.0. If a copy of the MPL was not distributed with this
file, You can obtain one at https://mozilla.org/MPL/2.0/.

Copyright (c) 20XX, MPL Contributor1 contrib1@example.net
Copyright (c) 20XX, MPL and (L)GPL Contributor2 contrib2@example.net
"""
```

==Стоит уточнить, что мы говорим о второй производной MPL-licensed проекта, в ней тупо сверху добавляем copyright и мы этим показываем, что добавляемые изменения лицензируем под своей лицензией, а не MPL. MPL в этом случае не имеет право пользоваться изменненой версией. Я считаю этот метод замудренным. По сути со второй производной можно отбросить MPL полностью, поэтому лучшим вариантом будет либо продолжать тащить 2 лицензии, либо отбросить MPL и полностью перелицензировать своей лицензией.==

It is very important that the developer preserve the copyright and permission notices as they appeared in the original code, as required by the MPL. We recommend making a clear separation and using indentation, as in the example above.

This manner of organizing the notices in the file makes it convenient for developers to choose whether to contribute under the MPL and (L)GPL, or under the (L)GPL alone. If they wish to make their contributions available under the MPL and (L)GPL, they can add their copyright notices to the lower group. If they wish to contribute under the (L)GPL alone, they can add their copyright notices at the top.

Note, however, that in a single source file it is typically very difficult, and often completely infeasible, to determine which parts of such a file are covered by permissive terms, so if possible, a project should attempt to maintain both licenses, as described in previous sections.

## Distributing Solely Under the (L)GPL

Once a file has been distributed under both the (L)GPL and the MPL, recipients of that file can later distribute it solely under the terms of the (L)GPL, in accordance with the terms of that license. If a project wishes to do this, and not to allow others to use their version of this file under the MPL, the project can indicate its decision by deleting the MPL headers described in Exhibit A of the license and replacing them with the standard notice recommended by the (L)GPL. Copyright notices indicating authorship of the file should be retained.

==Если проект во второй производной от MPL решает отбросить лицензирование MPL, то нужно удалить MPL заголовки описанные в Exhibit A, заменив заголовками своих лицензий. Copyright notices нужно оставить. ==
## A Note On the LGPL

Note that, while this article uses (L)GPL throughout, no special license changes are necessary when an MPL-licensed application links against an LGPL-licensed library. In the case of the LGPL, the licensing and notice requirements discussed above apply only when MPL-licensed files are to be included directly in the library itself.

This work is based on "[Maintaining Permissive-Licensed Files in a GPL-Licensed Project: Guidelines for Developers](https://www.softwarefreedom.org/resources/2007/gpl-non-gpl-collaboration.html)", authored by the SFLC, to whom we are very grateful. Both that work and this work are available under [CC-BY-SA](http://creativecommons.org/licenses/by-sa/3.0/)


==Размышления==
**Что мы используем и когда нас используют**
Лицензия GPL требует, чтобы производные были под GPL, но сама может использовать любые permissive лицензии.
С LGPL можно динамически линковаться, особенности описываются в [[How to Apply Software Licenses?]].

**MPL добрый**
По сути под двойное лицензирование подпадают только измененные файлы, а не весь (L)GPL проект? Вот что имели ввиду под "combination". 
Есть 2 варианта:
1. Двойное лицензирование комбинации (L)GPL + MPL - Зачем?
2. Contribution to MPL проект и простое его использование!

https://www.mozilla.org/en-US/MPL/2.0/
>3.3. Distribution of a Larger Work
>
>You may create and distribute a Larger Work ==under terms of Your choice==, provided that You also ==comply with the requirements of this License== for the Covered Software. 
>If the Larger Work is a ==combination== of Covered Software with a work governed by one or more Secondary Licenses, and the Covered Software is not Incompatible With Secondary Licenses, this ==License permits You to additionally distribute such Covered Software under the terms of such Secondary License(s)==, so that the recipient of the Larger Work may, at their option, further distribute the Covered Software under the terms of either this License or such Secondary License(s).

Производные (Larger Work) можно лицензировать как хочешь, но нужно соблюдать file-based copyleft и оставлять copyright.
Комбинации можно dual лицензировать с совместимыми Secondary лицензиями.


**Я не понимаю зачем нужно двойное лицензирование!?** 
**Мне кажется здесь есть что-то хитрое, что стимулирует GPL подкоситься?**
Хотя нет, MPL думает только о своих ветках, которые свободно могут использовать другие, но если нужно улучшить ветку, то contribute в Open Source.  

**зачем нужно двойное лицензирование!?**
Просто для удобства разработки видимо, когда ты пишешь combination GPL-проект с MPL кодом.