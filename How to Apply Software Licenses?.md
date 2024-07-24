---
creation_time: 2024-07-24 16:45
parents:
  - "[[Software License]]"
---

**Notice:**
Unlicense
BSD-3, BSD-2, BSD-0
MIT
[[Apache License, Version 2.0|Apache]]
**Weak-Copyleft:**
[[Mozilla Public License (MPL)|MPL]] - file-based copyleft, среднее между Apache-2.0 и LGPL, GPL.
LGPL there are v1,v2,v3; restricted-if-statically-linked.
**Copyleft:**
(GPLv1 FOSS
GPLv2 используй, меняй, либо делись, либо только у себя используй
GPLv3 - internationalization, tivo, patents - cool)
**Copyleft with a patched Internet Services gap:**
AGPL - strong copyleft, софт основной
SSPL - софт всех программ

### Licenses Example

Apache:
- Apache Spark: https://github.com/apache/spark
- Tensorflow: https://github.com/tensorflow/tensorflow
MIT:
- NodeJS: https://github.com/nodejs/node
- Nest: https://github.com/nestjs/nest
- PyTorch: https://github.com/pytorch/pytorch

MPL:
- LibreOffice: https://github.com/LibreOffice/libcdr
- RabbitMQ: https://github.com/rabbitmq/rabbitmq-server?tab=MPL-2.0-3-ov-file

---

Я не рассматриваю здесь особо GPL-family и Proprietary.

SSPL очень похоже на AGPL, но требует раскрытия всего софта? даже проприетарного (?):
- MongoDB
- Redis
- ElasticSearch

Proprietary License:
- Google Chrome (freeware)
- Windows

---
**Apache License 2.0**

[[Apache Software Foundation (ASF)]]


Я сейчас меняю лицензию с MIT на Apache-2.0, но на самом деле для смены лицензии нужно согласие всех contributor-ов. 

Как лицензировать программу под Apache-2.0? 

Как назвать файл с лицензией? 
LICENSE vs. COPYING

Нужно ли указывать в каждом файле какой-нибудь header? 
Желательно.

Что за NOTICE?

---
https://github.com/apache/spark
Apache Spark имеет:
- LICENSE (we can name it COPYING.SPDX)
- LICENSE-binary
- NOTICE
- NOTICE-binary
- 
- CONTRIBUTING
- README

https://github.com/nodejs/node
а у NodeJS ещё есть:
- CODE_OF_CONDUCT
- GOVERNANCE
- SECURITY
- CHANGELOG

---

**About Mozilla Public License (MPL-2.0)**

https://www.mozilla.org/en-US/MPL/2.0/FAQ/
>Q1: The MPL is a simple [copyleft](http://en.wikipedia.org/wiki/Copyleft) license. The MPL's "file-level" copyleft is designed to encourage contributors to share modifications they make to your code, while still allowing them to combine your code with code under other licenses (open or proprietary) with minimal restrictions.

https://www.tldrlegal.com/license/mozilla-public-license-2-0-mpl-2
>MPL is a copyleft license that is easy to comply with. You must make the source code for any of your changes available under MPL, but you can combine the MPL software with proprietary code, as long as you keep the MPL code in separate files. Version 2.0 is, by default, compatible with LGPL and GPL version 2 or greater. You can distribute binaries under a proprietary license, as long as you make the source available under MPL.

По-моему, MPL-2.0 классная лицензия. Она "заражает" файл, а не проект, как GPL, AGPL, SSPL, и не библиотеку, как LGPL. 

Google вносит MPL в категорию ['reciprocal'](https://opensource.google/documentation/reference/thirdparty/licenses#reciprocal), то есть взаимные лицензии. Если ты используешь код под MPL, то изменения внесенные в проект под MPL должны быть отданы обратно, но твой проект, пожалуйста, лицензируй как вздумается.
Концепция weak file-based copyleft порождает **dual licensing**. Когда мы лицензируем MPL-проект под лицензию GPL. GPL требует, чтобы весь софт был под GPL. MPL не запрещает использовать и лицензировать MPL-проект по своему, но изменения внесенные в MPL-проект должны быть доступны и они обязаны быть под MPL из-за file-based copyleft-а, то есть получается двойное лицензирование. 

В MPL-2.0, есть Prohibit B, который не стоит использовать, он сделан для обратной совместимости с MPL-1.1. Это добавление запретит **dual licensing**, то есть нельзя будет использовать с GPL, но не запретит использовать MPL-проект и лицензировать свой проект по своему. 
https://github.com/penpot/penpot/discussions/813

Похоже, что MPL true-шная Open Source лицензия, без радикальных наклонностей "свободы". MPL ловит баланс. GPL - Free and Open Source License, круто, но не во всех ситуациях подходит, обязуя тебя отдавать исходный код. Например, если бы из-за лицензионных прав все исходники Google были бы открыты, то достаточно просто было бы их клонировать, и эти клоны не дали бы зарабатывать людям придумавшим поисковик и благодаря чему развивать технологии дальше. GPL с одной стороны и стимулирует развитие своей открытостью, с другой стороны без коммерческой части она не дает разгореться развитию. 


https://opensource.com/law/11/8/mozilla-public-license-almost-20-part-1
https://opensource.com/law/11/9/mpl-20-copyleft-and-license-compatibility

- https://www.mozilla.org/en-US/MPL/2.0/FAQ/
- https://www.mozilla.org/en-US/MPL/2.0/combining-mpl-and-gpl/
	-> [[Mozilla (WWW) - Combining MPL-Licensed files with an (L)GPL-Licensed Project. Guidelines for Developers]]
- https://softwarefreedom.org/resources/2007/gpl-non-gpl-collaboration.html




---

https://www.youtube.com/watch?app=desktop&v=PaKIZ7gJlRU
Linus Torvalds объясняет свое понимание FOSS.

---

**Dual Licensing** - you can choose from provided licenses.

https://opensource.stackexchange.com/questions/14199/agpl3-and-commercial-use
>if your software is to be licensed under a GPLv3-compatible license, then you can use min.io under AGPLv3.
>However, if you intend to make your software proprietary and closed source, then you need to buy min.io's commercial license.

Почему-то мне напомнил freemium, но это не совсем правильно, freemium это proprietary, просто распространяют бесплатно и использование тоже бесплатное, как Google Chrome.

---

**LGPL**

https://www.tutorchase.com/answers/a-level/computer-science/what-are-the-different-types-of-linking-and-loading
Static
Dynamic:
- On-Load
- Run-Time

>Static linking is a process in which the linker combines all the relevant code from libraries directly into the executable file. This happens at the time of compilation. The advantage of static linking is that the executable file can run independently, without needing any additional libraries at run-time. However, it can lead to larger executable files and potential wastage of memory, as all the library code is included, whether it's used or not.  
> 
>Dynamic linking, on the other hand, does not include the library code in the executable file. Instead, references to the library functions are included. The actual linking with the library code happens at run-time, when the application is executed. This results in smaller executable files and efficient memory usage, as only the required library code is loaded. However, the necessary libraries must be available on the system at run-time.  
>
>Load-time dynamic linking is a variant of dynamic linking. In this case, the linking still happens at run-time, but it is done when the program is loaded into memory, before execution begins. This means that the necessary libraries must be available at load-time. If a library is not available, the program will not run.  
>
>Run-time dynamic linking is another variant of dynamic linking. In this case, the linking happens during the execution of the program. This allows a program to decide when and if a certain library is needed, and to load it only when necessary. This can provide additional flexibility, but it also requires more complex programming, as the program must handle the loading and linking of libraries itself.


----

Говорит, что если используешь БД под AGPL, то необязательно свой софт лицензировать под AGPL.
То есть AGPL можно использовать в проприетарном софте? Вроде так нельзя же... 
Ситуация похожа на исполнение своего софта на Linux (GPLv2) и компиляции с GCC (GPLv3), но твой софт не является производной операционной системы или компилятора.
https://medium.com/swlh/understanding-the-agpl-the-most-misunderstood-license-86fd1fe91275

Но, гугл не использует софт под AGPL, потому что все что линкуется с AGPL copylefted. Все взаимодействует друг с другом, и для компании рисков больше чем пользы.
https://opensource.google/documentation/reference/using/agpl-policy

- https://opensource.google/documentation/reference/thirdparty/licenses#LinkingRequirements
- https://opensource.google/documentation/reference/thirdparty/licenses#restricted

---

Тут говорится, что использовать LGPL лучше когда библиотеку легко переписать. У GNU-FSF прямо стратегия по тому, как именно сделать больше софта свободным.

Например, GNU C - glibc, под LGPL, чтобы ею могли пользоваться, дорабатывать и это принесло пользу всем, и компаниям и GNU.

Популярность необязательна?

https://www.gnu.org/licenses/why-not-lgpl.html

Для библиотек LGPLv3 неплох.

LGPLv3 позволяет его законно использовать компаниям и не заботиться о copyleft, если они не меняют саму библиотеку и линкуют её со своим ПО динамично. 
1. Распространение должно предоставлять доступ пользователям менять версию библиотеки под LPGL либо исполняющийся файл библиотеки, либо просто предоставить весь исходный код.
2. Если предоставляют услугу через интернет, то ты вообще свободен. Кажется, можно даже менять код библиотеки локально и всё будет ок?

---

Можно ли менять код под LGPL локально и предоставлять SaaS, чтобы мой софт не был обязан быть под LGPL, это не отразилось Copyleft-ом LGPL и не предоставляя исходного кода нашего ПО?

Точнее, если я меняю LGPL и использую в своем SaaS, то нужно обязан ли я лицензировать свое SaaS ПО под LGPL?

Ответ, нет. Я могу линковать SaaS с LGPL библиотеками и даже менять эти библиотеки, но SaaS ПО я могу держать проприетарным и лицензировать по своему. 

Но, конечно, как обычно, если я распространяю ПО, то мне нужно дать возможность менять версии LGPL через динамическую линковку или исходный код.

---


# File.py

It is safest to attach notices to the start of each source file to most effectively state the exclusion of warranty; and each file should have at least the “copyright” line and a pointer to where the full notice is found.
1. <Одна строка, дающая название программы и краткое представление о том, что она делает>
2. Copyright date name <некоторый добавляют email в copyright notice (?)>
3. license/link


```python
"""
   This file is part of the SampleProgram - A simple example program

   Copyright 2024 Alar Akilbekov 

   Licensed under the Apache License, Version 2.0 (the "License");
   you may not use this file except in compliance with the License.
   You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

   Unless required by applicable law or agreed to in writing, software
   distributed under the License is distributed on an "AS IS" BASIS,
   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
   See the License for the specific language governing permissions and
   limitations under the License.

   Contact: alar.akilbekov@gmail.com
"""


print("Hello, World!")

```


From GPL-3 "How to apply":
```
If the program does terminal interaction, make it output a short notice when it starts in an interactive mode.

For a GUI interface, you would use an “about box”.

You should also get your employer (if you work as a programmer) or school, if any, to sign a “copyright disclaimer” for the program, if necessary.
```


GPL is copyleft, a.k.a. "viral", то есть производные должны так же быть под GPL, что значит её нельзя использовать с несвободными программами.

Если нужно разрешить связывать библиотеку, то можно использовать LGPL.

AGPL ещё строже, чем GPL, в плане использования на стороне сервера и предоставления услуг через интернет.

SSPL ещё строже AGPL.

---

Если нужно разрешить связывать файл, то можно использовать MPL.

 Boilerplate:
```python
"""
This Source Code Form is subject to the terms of the Mozilla Public License, v. 2.0. If a copy of the MPL was not distributed with this file, You can obtain one at https://mozilla.org/MPL/2.0/.

Copyright 2024 Alar Akilbekov alar.akilbekov@gmail.com
"""
```

Можно добавить ещё "All Rights Reserved":
```
Copyright 2024 Alar Akilbekov alar.akilbekov@gmail.com. 

All Rights Reserved.
```
Это необязательно в случае и в случае FOSS и OSS лицензии, и в случае Proprietary License тоже необязательно. По-умолчанию у автора появляется авторское право. "Все права защищенны" означает, что использовать ИС без разрешения автора запрещено, что и без этого верно. 

Кажется, вместо boilerplate-а можно указать только machine-readable header - SPDX:
```python
"""
SPDX-License-Identifier: MPL-2.0
"""
```

Можно объединить так?
```python
"""
This file is part of the SampleProgram - A simple example program

Copyright (C)© 2024 Alar Akilbekov alar.akilbekov@gmail.com. 

All Rights Reserved.

SPDX-License-Identifier: MPL-2.0
--------------------------------
This Source Code Form is subject to the terms of the Mozilla Public License, v. 2.0. If a copy of the MPL was not distributed with this file, You can obtain one at https://mozilla.org/MPL/2.0/.
"""
```
Мне нравится.

Кажется, если есть LICENSE файл, то header-ы в каждый файл вообще можно не добавлять.

 ---

# Modifications to copyrighted files

 Если изменения добавляются в файл можно написать так:
```python
"""
File
Copyright year name
https://link/license/

Modifications made by Alar Akilbekov on 2024-07-24:
- Description of modifications
"""
```

Я не думаю что хорошая идея добавлять второй copyright в измененные файлы под MPL. Лучше добавить типа "изменения добавил Алар в 2024 году: изменения включают...", как показано выше.
Но, в принципе добавляют несколько copyright-ов подряд:
```
Copyright
Copyright
Copyright
```
Check PyTorch: https://github.com/pytorch/pytorch?tab=License-1-ov-file.
Кажется, так можно делать, если fork-аешь проект.


---

# Third-Party Software Licenses

В Readme (или в LICENSE) файле нужно написать лицензию самого проекта, потом лицензии зависимостей и описание что ты изменил (в случае изменений отдельных файлов). Хороший пример как описывать лицензии зависимостей - это лицензия NodeJS.

При лицензировании нужно ещё указывать THIRD-PARTY LICENSES:
```
The Node.js license applies to all parts of Node.js that are not externally maintained libraries.

The externally maintained libraries used by Node.js are:
- Acorn, located at deps/acorn, is licensed as follows: "LICENSE..."

...
```

Там ещё в лицензии какой-то софт такой разделитель имеет:
```
----------------------------------------------------------------------

Third-Party Software Licenses

This section contains third-party software notices and/or additional
terms for licensed third-party software components included within ICU
libraries.

----------------------------------------------------------------------

...
```




Apache Spark License 3rd party licenses:
```
------------------------------------------------------------------------------------
This product bundles various third-party components under other open source licenses.
This section summarizes those components and their licenses. See licenses/
for text of these licenses.


Apache Software Foundation License 2.0
--------------------------------------

common/network-common/src/main/java/org/apache/spark/network/util/LimitedInputStream.java
core/src/main/java/org/apache/spark/util/collection/TimSort.java
core/src/main/resources/org/apache/spark/ui/static/bootstrap*
core/src/main/resources/org/apache/spark/ui/static/vis*
docs/js/vendor/bootstrap.js
connector/spark-ganglia-lgpl/src/main/java/com/codahale/metrics/ganglia/GangliaReporter.java
core/src/main/resources/org/apache/spark/ui/static/d3-flamegraph.min.js
core/src/main/resources/org/apache/spark/ui/static/d3-flamegraph.css

...
```

Вообще у Apache Spark сложное лицензирование у них разные лицензии для LICENSE-binary и NOTICE, NOTICE-binary у них дополнительно есть, я не знаю зачем эти NOTICE файлы, почему нельзя было всё уместить в LICENSE.

---

# NOTICE

Я не знаю зачем нужен NOTICE файл о котором говорят в Apache License 2.0. Чем NOTICE отличается от просто LICENSE?

---

