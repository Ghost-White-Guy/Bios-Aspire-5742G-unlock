<div id="n"></div>

# 🛠️ Acer Aspire 5742G BIOS Unlock (Advanced & Power Menus) + Custom Logo

[ 🇷🇺 Русский ](#ru) | [ 🇬🇧 English ](#en)

---
![Platform](https://img.shields.io/badge/Platform-Acer_5742G-lightgrey)
![Tools](https://img.shields.io/badge/Tools-UEFITool_%7C_HxD-orange)

<h2 id="ru">🇷🇺 Русский (Описание)</h2>
В данном репозитории находятся дампы BIOS для ноутбука Acer Aspire 5742G, а также подробная пошаговая инструкция по самостоятельной разблокировке скрытых инженерных меню (Advanced и Power), замене загрузочного логотипа и глубокой низкоуровневой оптимизации. Данная модификация (Acer PEW71 bios modification) позволяет получить полный контроль над системой, решить проблемы с перегревом (Acer 5742G thermal throttling fix) и навсегда отключить встроенные системы слежения (InsydeH2O Computrace disable). Идеально подходит для тех, кто ищет чистый LA-5894P dump.

**🔍 Ключевые слова для поиска:** LA-5894P dump, Acer 5742G thermal throttling fix, InsydeH2O Computrace disable, Acer PEW71 bios modification.

> [!CAUTION]
> ### ⚠️ КРИТИЧЕСКИЕ ПРЕДУПРЕЖДЕНИЯ (ЧИТАТЬ ОБЯЗАТЕЛЬНО!)
> 1. **ТОЛЬКО ПРОГРАММАТОР:** Прошивка модифицированного BIOS должна производиться **СТРОГО** через аппаратный программатор (например, CH341A) с прищепкой или через выпаивание чипа памяти. 
> 2. **НЕТ ПРОШИВКЕ ИЗ WINDOWS:** Попытка прошить этот мод через штатные утилиты (InsydeFlash и др.) из-под ОС приведет к ошибке контрольных сумм / проверке цифровой подписи и гарантированному **«окирпичиванию»** ноутбука.
> 3. **ОБЕСТОЧЬТЕ ПЛАТУ:** Перед подключением прищепки программатора к чипу **ОБЯЗАТЕЛЬНО** отключите блок питания и снимите аккумуляторную батарею с ноутбука. 
> 4. **СДЕЛАЙТЕ БЭКАП:** Прежде чем что-то зашивать, считайте свой оригинальный BIOS через программатор минимум 2-3 раза. Сохраните эти файлы и проверьте, чтобы они были абсолютно идентичны (совпадали хэш-суммы). Если файлы разные — прищепка установлена криво, считывать и шить так нельзя!
> 5. **ЗАПАСНОЙ ПК:** Не приступайте к прошивке модифицированного BIOS, если у вас нет под рукой второго рабочего компьютера/ноутбука. В случае ошибки вам понадобится второе устройство, чтобы прошить оригинальный дамп обратно.

> [!WARNING]
> **ВСЕ ДЕЙСТВИЯ ВЫ ВЫПОЛНЯЕТЕ ИСКЛЮЧИТЕЛЬНО НА СВОЙ СТРАХ И РИСК!** Автор репозитория не несет ответственности за вышедшее из строя оборудование.

---

## 💻 Тест проводился исключительно на данных комплектующих:
* **Процессор:** Intel Core i5 580M
* **Видеокарта:** NVIDIA GeForce 610M
* **Оперативная память:** 6 GB RAM DDR3
* **Накопитель:** HDD 256 GB
* **Модель ноутбука:** Acer Aspire 5742G
* **Платформа (Материнская плата):** Compal PEW71 / LA-5894P
* **Ревизия платы (Rev):** 1.0

*(Внимание: я не могу гарантировать 100% работоспособность данной прошивки на вашем ноутбуке, так как ревизии плат и комплектующие могут отличаться. ОБЯЗАТЕЛЬНО СОХРАНИТЕ ВАШ ИСХОДНЫЙ ДАМП перед прошивкой моего варианта!)*

---

## 🔥 PRO-модификация: Обновление микрокодов, AHCI и тотальная очистка

В модифицированном дампе `Acer Aspire 5742G-unlock.bin` не только разблокированы инженерные меню, но и проведена глубокая низкоуровневая оптимизация DXE-драйверов. Чтобы освободить место в чипе памяти для новых модулей, была произведена зачистка «мусора» и аппаратных трекеров.

### 🗑️ Что было удалено (Освобождение места и безопасность):
* **Аппаратные трекеры и телеметрия:** Полностью вырезаны модули `ComputraceSMI`, `Computrace`, а также `Tdt`, `TdtUsbWdm` и `Tdt3g` (Intel Anti-Theft Technology). В BIOS больше нет встроенных закладок для отслеживания ноутбука.
* **Лишние локализации и устаревший код:** Удален `Chinese` (китайский язык) и модуль `Ebc`.
* **Лишние модули:** Вырезан `57780M`.

### 🚀 Что было добавлено и обновлено:
* **Поддержка процессора:** Добавлен модуль `MicrocodeUpdate`. Интегрированы свежие микрокоды для повышения стабильности работы процессора (в т.ч. Intel Core i5).
* **Новые полезные DXE-модули:**
  * `MeFwDowngrade` — разблокирует возможность программного понижения версии прошивки Intel Management Engine (Intel ME).
  * `TgaDecoder` и `PrePostHotkey`.

### 🚀 PRO-Тюнинг (Максимальная производительность процессора):
В базовом `mod_bios.rom` установлены консервативные настройки. Для раскрытия полного потенциала процессоров i5/i7 (работа Turbo Boost) настоятельно рекомендуются следующие ручные настройки:
* **Шаг 1:** В `Power & CPU -> Security CPU Control` ОБЯЗАТЕЛЬНО включите C-States (`[Enabled]`). Без этого Turbo Boost не сможет поднимать частоты!
* **Шаг 2:** В `Advanced -> Chipset Configuration` установите QPI Frequency на максимальные `[6.400 GT]`.
* **Шаг 3:** Power Limit уже изменён на 800 (80 ВАТТ) по умолчанию для предотвращения сброса частот под высокой нагрузкой. Следите за температурами!

---

## 📁 Содержимое репозитория

### Готовые дампы прошивок и модули:
* `Acer Aspire 5742G.bin` — Оригинальный (чистый) дамп BIOS, считанный программатором. Используйте для отката в случае проблем.
* `Acer Aspire 5742G-unlock.bin` — Модифицированный дамп с разблокированными меню `Advanced` (вместо `Security`) и `Power & CPU` (вместо `Information`), а также всеми встроенными оптимизациями (PRO-мод).
* **`DXE_Modules_Pack.7z`** — Пакет чистых, извлеченных `.ffs` модулей (AHCI, Microcodes, Xhci и др.) для тех, кто хочет интегрировать их в свой BIOS вручную.

### 🧰 Необходимый инструментарий (Уже в репозитории)
Для вашего удобства все нужные программы упакованы в `.7z` архивы. Вам не нужно искать их в интернете — просто скачайте и распакуйте:
1. **`AsProgrammer.7z`** — программа для считывания и записи прошивки (CH341A).
2. **`UEFITool.7z`** — утилита для распаковки дампа BIOS и интеграции модулей логики.
3. **`IRFExtractor.7z`** — конвертер логики IFR.
4. **`HxD.7z`** — Hex-редактор.
5. **`H2OEZE.7z`** — утилита для замены загрузочного Logo.

---

## ⚙️ ИНСТРУКЦИЯ 1: Самостоятельная разблокировка меню (Подмена масок)

*(Если вы хотите понять, как это работает, и сделать разблокировку скрытых меню своими руками).*

#### Шаг 1: Извлечение модуля логики
1. Запустите **UEFITool** и откройте оригинальный дамп BIOS.
2. Нажмите `Ctrl+F`, перейдите во вкладку *Text* и введите в поиск `SetupUtility`.
3. В найденном модуле (обычно раздел *PE32 image section*) кликните правой кнопкой мыши -> **Extract body**. 
4. Сохраните файл как `SetupUtility.bin`.

#### Шаг 2: Анализ IFR (Поиск масок меню)
1. Запустите **IRFExtractor** и прогоните через него `SetupUtility.bin`.
2. В полученном `.txt` файле найдите секции `Offset`. 
   * *Для Compal LA-5894P ID выглядят так:*
     * `Information` = Offset: `0x7F400`
     * `Main` = Offset: `0x7EE10`
     * `Security` = Offset: `0x7FAD0`
     * `Exit` = Offset: `0x7F1F0`
     * `Boot` = Offset: `0x7F280`
     * `Advanced` (Скрыта) = Offset: `0x7F970`
     * `Power` (Скрыта) = Offset: `0x83CB0`

#### Шаг 3: Подмена логики (Редактирование в HxD)
Цель — заставить BIOS загружать `Advanced` вместо `Security`, и `Power & CPU` вместо `Information`.
1. Откройте `SetupUtility.bin` в **HxD**.
2. **Подмена Security:** Замените байты вызова Security (`0E 24 F4 27 4A A0 00 DF 42 4D B5 52 39 51 13 02 11 3D 47 02 37 00 00 00 00 00 00 00 00 00 01 00 00 00 21 03`) на маску Advanced (`0E 24 F4 27 4A A0 00 DF 42 4D B5 52 39 51 13 02 11 3D 67 00 37 00 00 00 00 00 00 00 00 00 01 00 05 00 21 03`). 
3. **Подмена Information:** Замените байты вызова Information (`0E 24 F4 27 4A A0 00 DF 42 4D B5 52 39 51 13 02 11 3D 03 00 37 00 00 00 00 00 00 00 00 00 01 00 00 00 21 03`) на маску Power (`0E 24 F4 27 4A A0 00 DF 42 4D B5 52 39 51 13 02 11 3D 83 02 37 00 00 00 00 00 00 00 00 00 01 00 05 00 21 03`).
4. **ОБЯЗАТЕЛЬНАЯ ОБРАТНАЯ ПОДМЕНА:** Таким же образом, только в обратном порядке, измените байты Advanced на Security и Power на Information. Иначе BIOS зависнет, увидев ссылки на один раздел дважды!

> 🛑 **ВАЖНО:** Размер `SetupUtility.bin` не должен измениться ни на байт! Используйте только замену с перезаписью (Overwrite). Вставка со сдвигом (Insert) сломает модуль!

HEX-коды меню из SetupUtility
 * Main `0E 24 F4 27 4A A0 00 DF 42 4D B5 52 39 51 13 02 11 3D 50 00 37 00 00 00 00 00 00 00 00 00 01 00 00 00 21 03`
 * Exit `0E 24 F4 27 4A A0 00 DF 42 4D B5 52 39 51 13 02 11 3D FE 02 37 00 00 00 00 00 00 00 00 00 01 00 00 00 21 03`
 * Boot `0E 24 F4 27 4A A0 00 DF 42 4D B5 52 39 51 13 02 11 3D E4 02 37 00 00 00 00 00 00 00 00 00 01 00 00 00 21 03`
 * Information `0E 24 F4 27 4A A0 00 DF 42 4D B5 52 39 51 13 02 11 3D 03 00 37 00 00 00 00 00 00 00 00 00 01 00 00 00 21 03`
 * Advanced `0E 24 F4 27 4A A0 00 DF 42 4D B5 52 39 51 13 02 11 3D 67 00 37 00 00 00 00 00 00 00 00 00 01 00 05 00 21 03`
 * Security `0E 24 F4 27 4A A0 00 DF 42 4D B5 52 39 51 13 02 11 3D 47 02 37 00 00 00 00 00 00 00 00 00 01 00 00 00 21 03`
 * Power `0E 24 F4 27 4A A0 00 DF 42 4D B5 52 39 51 13 02 11 3D 83 02 37 00 00 00 00 00 00 00 00 00 01 00 05 00 21 03`

#### Шаг 4: Косметическое переименование вкладок (Опционально)
1. В HxD нажмите `Ctrl+F` -> **Hex-values**.
2. **Меняем Security на Advanced:**
   * Ищем: `53 00 65 00 63 00 75 00 72 00 69 00 74 00 79 00` (*S.e.c.u.r.i.t.y*).
   * Заменяем на: `41 00 64 00 76 00 61 00 6E 00 63 00 65 00 64 00` (*A.d.v.a.n.c.e.d*).
3. **Меняем Information на Power & CPU:**
   * Ищем: `49 00 6E 00 66 00 6F 00 72 00 6D 00 61 00 74 00 69 00 6F 00 6E 00` (*I.n.f.o.r.m.a.t.i.o.n*).
   * Заменяем на: `50 00 6F 00 77 00 65 00 72 00 20 00 26 00 20 00 43 00 50 00 55 00` (*Power & CPU*). Внимание: Пробелы (`20 00`) строго обязательны для сохранения длины!

> *(🛑 ВНИМАНИЕ: Косметическое переименование может не сработать из-за внутренних особенностей BIOS. Вы можете использовать автозамену по всему файлу (Replace All) для всех значений, КРОМЕ `Power`! Если вы глобально замените слово Power, то это затронет не только визуальные тексты, но и множество скрытых системных переменных. В результате BIOS просто «ослепнет» — при попытке загрузить меню он не сможет прочитать нарушенную структуру ссылок, и вы получите намертво зависший экран или битые пиксели)*

#### Шаг 5: Сборка BIOS (UEFITool)
1. В **UEFITool** найдите секцию `SetupUtility`, кликните правой кнопкой по *PE32 image section* внутри `SetupUtility` -> **Replace body** и выберите измененный `SetupUtility.bin`.
2. Сохраните образ: `File` -> `Save image file` (назовите `mod_bios.rom`).

---

## 🧩 ИНСТРУКЦИЯ 2: Ручная интеграция DXE-модулей (.ffs)

Для тех, кто скачал `DXE_Modules_Pack.7z` и хочет вшить драйверы (AHCI, Microcodes) в свой дамп вручную через **UEFITool**.

1. **Проверка на дубликаты (Важно!):** Перед вставкой обязательно воспользуйтесь поиском в UEFITool, чтобы проверить, нет ли уже такого модуля в вашем BIOS.
2. **ЕСЛИ МОДУЛЬ УЖЕ ЕСТЬ (Замена):** * Нажмите на него правой кнопкой мыши и выберите **`Replace`** (Заменить), выбрав файл из архива. 
   * *Примечание: Заменяйте файл целиком (0h выравнивание). Не пугайтесь, если увидите системные ссылки или предупреждения о смещениях — UEFITool всё пересчитает корректно. Главное — не дублировать модули!*
3. **ЕСЛИ МОДУЛЯ НЕТ (Вставка нового):**
   * Разверните основной том с драйверами DXE.
   * Пролистайте список в самый низ тома. Найдите **САМЫЙ ПОСЛЕДНИЙ файл** прямо перед строкой `Volume free space` (Свободное место).
   * Кликните по этому последнему файлу правой кнопкой мыши и выберите строго **`Insert after`** (Вставить после). 
   * Выберите ваш `.ffs` файл. Он встанет ровно перед `Volume free space`. 
   * *🛑 Строго запрещено использовать `Insert before` или пытаться вставить файл напрямую внутрь `Free space`!*
4. Сохраните готовый дамп: `File` -> `Save image file`.

---

## 🖼️ ИНСТРУКЦИЯ 3: Замена логотипа (H2OEZE)

1. Откройте ваш `mod_bios.rom` в **H2OEZE** (`File` -> `Load ROM`).
2. Перейдите в `Components` -> `Logo`.
3. Нажмите `Browse` и выберите изображение (**1024x768**, формат **только BMP (16-цветный рисунок)**, вес **менее 900 КБ**).
4. Нажмите `Apply`. В окне конвертации/сжатия обязательно нажмите **`Yes`**.
5. Сохраните прошивку: `File` -> `Save`.

---

## 🔌 ИНСТРУКЦИЯ 4: Финальная прошивка

1. Откройте **AsProgrammer**.
2. Очистите чип памяти на материнской плате ноутбука.
3. Откройте финальный `mod_bios.rom` и запишите его на чип. 
4. Дождитесь окончания верификации.
5. Проверьте свой ноутбук на включение и вход в BIOS и Систему перед сборкой.
6. Если всё хорошо, то смело собирайте ноутбук. Готово!

---

*(Если возникнут проблемы — пишите на почту byteghosthelper@gmail.com, попытаюсь помочь всем, чем смогу. Также для более быстрого ответа вы можете скинуть ссылку на мой репозиторий любому искусственному интеллекту (с доступом к интернету, например, Gemini, Qwen или DeepSeek) с просьбой объяснить всё более подробно и чётко, если моих инструкций окажется недостаточно).*

[ ⬆️ Вернуться к началу ](#n)
<br><br>

---

<h2 id="en">🇬🇧 English (Description)</h2>
This repository contains BIOS dumps for the Acer Aspire 5742G laptop, along with a detailed step-by-step guide for manually unlocking hidden engineering menus (Advanced and Power), replacing the boot logo, and performing low-level optimizations. This modification (Acer PEW71 bios modification) gives you full control over your system, helps resolve overheating issues (Acer 5742G thermal throttling fix), and permanently removes built-in tracking systems (InsydeH2O Computrace disable). Perfect for those looking for a clean LA-5894P dump.

**🔍 Search Keywords:** LA-5894P dump, Acer 5742G thermal throttling fix, InsydeH2O Computrace disable, Acer PEW71 bios modification.

> [!CAUTION]
> ### ⚠️ CRITICAL WARNINGS (MUST READ!)
> 1. **PROGRAMMER ONLY:** Flashing the modified BIOS must be done **STRICTLY** via a hardware programmer (e.g., CH341A) with a clip or by desoldering the memory chip.
> 2. **NO WINDOWS FLASHING:** Attempting to flash this mod using standard utilities (InsydeFlash, etc.) from the OS will result in a checksum/digital signature verification error and will guarantee a **"bricked"** laptop.
> 3. **DE-ENERGIZE THE BOARD:** Before connecting the programmer clip to the chip, you **MUST** disconnect the power supply and remove the battery from the laptop.
> 4. **MAKE A BACKUP:** Before flashing anything, read your original BIOS via the programmer at least 2-3 times. Save these files and check that they are absolutely identical (hash sums match). If the files are different, the clip is seated crookedly; do not read or flash like this!
> 5. **SPARE PC:** Do not start flashing the modified BIOS if you do not have a second working PC/laptop at hand. In case of an error, you will need a second device to flash the original dump back.

> [!WARNING]
> **ALL ACTIONS ARE PERFORMED ENTIRELY AT YOUR OWN RISK!** The author of the repository is not responsible for any damaged equipment.

---

## 💻 Tested exclusively on the following hardware:
* **Processor:** Intel Core i5 580M
* **Graphics Card:** NVIDIA GeForce 610M
* **RAM:** 6 GB RAM DDR3
* **Storage:** HDD 256 GB
* **Laptop Model:** Acer Aspire 5742G
* **Platform (Motherboard):** Compal PEW71 / LA-5894P
* **Board Revision (Rev):** 1.0

*(Attention: I cannot guarantee 100% functionality of this firmware on your laptop, as board revisions and components may differ. ALWAYS SAVE YOUR ORIGINAL DUMP before flashing my version!)*

---

## 🔥 PRO-modification: Microcode updates, AHCI, and total cleanup

In the modified dump `Acer Aspire 5742G-unlock.bin`, not only are the engineering menus unlocked, but deep low-level optimization of DXE drivers has also been performed. To free up space in the memory chip for new modules, "garbage" and hardware trackers were cleaned out.

### 🗑️ What was removed (Freeing space and security):
* **Hardware trackers and telemetry:** `ComputraceSMI`, `Computrace`, as well as `Tdt`, `TdtUsbWdm`, and `Tdt3g` (Intel Anti-Theft Technology) modules were completely cut out. The BIOS no longer has built-in backdoors for tracking the laptop.
* **Extra localizations and outdated code:** `Chinese` language and the `Ebc` module were removed.
* **Extra modules:** `57780M` was cut out.

### 🚀 What was added and updated:
* **Processor support:** Added `MicrocodeUpdate` module. Integrated fresh microcodes to improve processor stability (including Intel Core i5).
* **New useful DXE modules:**
  * `MeFwDowngrade` — unlocks the ability to software-downgrade the Intel Management Engine (Intel ME) firmware version.
  * `TgaDecoder` and `PrePostHotkey`.

### 🚀 PRO-Tuning (Maximum processor performance):
Conservative settings are set in the base `mod_bios.rom`. To unlock the full potential of i5/i7 processors (Turbo Boost operation), the following manual settings are highly recommended:
* **Step 1:** In `Power & CPU -> Security CPU Control`, you MUST enable C-States (`[Enabled]`). Without this, Turbo Boost will not be able to raise frequencies!
* **Step 2:** In `Advanced -> Chipset Configuration`, set QPI Frequency to the maximum `[6.400 GT]`.
* **Step 3:** Power Limit is already changed to 800 (80 WATTS) by default to prevent throttling under high load. Monitor your temperatures!

---

## 📁 Repository Contents

### Ready-made firmware dumps and modules:
* `Acer Aspire 5742G.bin` — Original (clean) BIOS dump, read by a programmer. Use to roll back in case of problems.
* `Acer Aspire 5742G-unlock.bin` — Modified dump with unlocked `Advanced` (instead of `Security`) and `Power & CPU` (instead of `Information`) menus, as well as all built-in optimizations (PRO-mod).
* **`DXE_Modules_Pack.7z`** — A pack of clean, extracted `.ffs` modules (AHCI, Microcodes, Xhci, etc.) for those who want to integrate them into their BIOS manually.

### 🧰 Required Tools (Already in the repository)
For your convenience, all necessary programs are packed into `.7z` archives. You don't need to search for them on the internet — just download and extract:
1. **`AsProgrammer.7z`** — software for reading and writing firmware (CH341A).
2. **`UEFITool.7z`** — utility for unpacking the BIOS dump and integrating logic modules.
3. **`IRFExtractor.7z`** — IFR logic converter.
4. **`HxD.7z`** — Hex editor.
5. **`H2OEZE.7z`** — utility for replacing the boot Logo.

---

## ⚙️ INSTRUCTION 1: Manual menu unlocking (Mask substitution)

*(If you want to understand how it works and do the hidden menu unlocking yourself).*

#### Step 1: Extracting the logic module
1. Run **UEFITool** and open the original BIOS dump.
2. Press `Ctrl+F`, go to the *Text* tab, and search for `SetupUtility`.
3. In the found module (usually the *PE32 image section*), right-click -> **Extract body**. 
4. Save the file as `SetupUtility.bin`.

#### Step 2: IFR Analysis (Searching for menu masks)
1. Run **IRFExtractor** and process `SetupUtility.bin` through it.
2. In the resulting `.txt` file, find the `Offset` sections. 
   * *For Compal LA-5894P, the IDs look like this:*
     * `Information` = Offset: `0x7F400`
     * `Main` = Offset: `0x7EE10`
     * `Security` = Offset: `0x7FAD0`
     * `Exit` = Offset: `0x7F1F0`
     * `Boot` = Offset: `0x7F280`
     * `Advanced` (Hidden) = Offset: `0x7F970`
     * `Power` (Hidden) = Offset: `0x83CB0`

#### Step 3: Logic substitution (Editing in HxD)
The goal is to force the BIOS to load `Advanced` instead of `Security`, and `Power & CPU` instead of `Information`.
1. Open `SetupUtility.bin` in **HxD**.
2. **Security Substitution:** Replace the Security call bytes (`0E 24 F4 27 4A A0 00 DF 42 4D B5 52 39 51 13 02 11 3D 47 02 37 00 00 00 00 00 00 00 00 00 01 00 00 00 21 03`) with the Advanced mask (`0E 24 F4 27 4A A0 00 DF 42 4D B5 52 39 51 13 02 11 3D 67 00 37 00 00 00 00 00 00 00 00 00 01 00 05 00 21 03`). 
3. **Information Substitution:** Replace the Information call bytes (`0E 24 F4 27 4A A0 00 DF 42 4D B5 52 39 51 13 02 11 3D 03 00 37 00 00 00 00 00 00 00 00 00 01 00 00 00 21 03`) with the Power mask (`0E 24 F4 27 4A A0 00 DF 42 4D B5 52 39 51 13 02 11 3D 83 02 37 00 00 00 00 00 00 00 00 00 01 00 05 00 21 03`).
4. **MANDATORY REVERSE SUBSTITUTION:** In the same way, only in reverse order, change the Advanced bytes to Security and Power to Information. Otherwise, the BIOS will freeze upon seeing links to the same section twice!

> 🛑 **IMPORTANT:** The size of `SetupUtility.bin` must not change by a single byte! Use only Paste Write (Overwrite). Insert pasting will break the module!

HEX-codes of menus from SetupUtility
 * Main `0E 24 F4 27 4A A0 00 DF 42 4D B5 52 39 51 13 02 11 3D 50 00 37 00 00 00 00 00 00 00 00 00 01 00 00 00 21 03`
 * Exit `0E 24 F4 27 4A A0 00 DF 42 4D B5 52 39 51 13 02 11 3D FE 02 37 00 00 00 00 00 00 00 00 00 01 00 00 00 21 03`
 * Boot `0E 24 F4 27 4A A0 00 DF 42 4D B5 52 39 51 13 02 11 3D E4 02 37 00 00 00 00 00 00 00 00 00 01 00 00 00 21 03`
 * Information `0E 24 F4 27 4A A0 00 DF 42 4D B5 52 39 51 13 02 11 3D 03 00 37 00 00 00 00 00 00 00 00 00 01 00 00 00 21 03`
 * Advanced `0E 24 F4 27 4A A0 00 DF 42 4D B5 52 39 51 13 02 11 3D 67 00 37 00 00 00 00 00 00 00 00 00 01 00 05 00 21 03`
 * Security `0E 24 F4 27 4A A0 00 DF 42 4D B5 52 39 51 13 02 11 3D 47 02 37 00 00 00 00 00 00 00 00 00 01 00 00 00 21 03`
 * Power `0E 24 F4 27 4A A0 00 DF 42 4D B5 52 39 51 13 02 11 3D 83 02 37 00 00 00 00 00 00 00 00 00 01 00 05 00 21 03`

#### Step 4: Cosmetic tab renaming (Optional)
1. In HxD, press `Ctrl+F` -> **Hex-values**.
2. **Change Security to Advanced:**
   * Find: `53 00 65 00 63 00 75 00 72 00 69 00 74 00 79 00` (*S.e.c.u.r.i.t.y*).
   * Replace with: `41 00 64 00 76 00 61 00 6E 00 63 00 65 00 64 00` (*A.d.v.a.n.c.e.d*).
3. **Change Information to Power & CPU:**
   * Find: `49 00 6E 00 66 00 6F 00 72 00 6D 00 61 00 74 00 69 00 6F 00 6E 00` (*I.n.f.o.r.m.a.t.i.o.n*).
   * Replace with: `50 00 6F 00 77 00 65 00 72 00 20 00 26 00 20 00 43 00 50 00 55 00` (*Power & CPU*). Attention: Spaces (`20 00`) are strictly mandatory to preserve the length!

> *(🛑 ATTENTION: Cosmetic renaming might not work due to internal BIOS peculiarities. You can use global replace (Replace All) for all values EXCEPT `Power`! If you globally replace the word Power, it will affect not only visual texts but also many hidden system variables. As a result, the BIOS will simply go "blind" — when trying to load the menu, it won't be able to read the broken link structure, and you will get a dead frozen screen or dead pixels)*

#### Step 5: BIOS Assembly (UEFITool)
1. In **UEFITool** find the `SetupUtility` section, right-click on the *PE32 image section* inside `SetupUtility` -> **Replace body** and select the modified `SetupUtility.bin`.
2. Save the image: `File` -> `Save image file` (name it `mod_bios.rom`).

---

## 🧩 INSTRUCTION 2: Manual integration of DXE modules (.ffs)

For those who downloaded `DXE_Modules_Pack.7z` and want to flash drivers (AHCI, Microcodes) into their dump manually via **UEFITool**.

1. **Check for duplicates (Important!):** Before inserting, make sure to use the search in UEFITool to check if such a module already exists in your BIOS.
2. **IF THE MODULE ALREADY EXISTS (Replacement):** * Right-click on it and select **`Replace`**, choosing the file from the archive. 
   * *Note: Replace the file entirely (0h alignment). Do not be alarmed if you see system links or offset warnings — UEFITool will recalculate everything correctly. The main thing is not to duplicate modules!*
3. **IF THE MODULE IS MISSING (Inserting a new one):**
   * Expand the main volume with DXE drivers.
   * Scroll the list to the very bottom of the volume. Find the **VERY LAST file** right before the `Volume free space` line.
   * Right-click on this last file and strictly select **`Insert after`**. 
   * Choose your `.ffs` file. It will stand exactly before `Volume free space`. 
   * *🛑 It is strictly forbidden to use `Insert before` or try to insert the file directly into `Free space`!*
4. Save the ready dump: `File` -> `Save image file`.

---

## 🖼️ INSTRUCTION 3: Logo Replacement (H2OEZE)

1. Open your `mod_bios.rom` in **H2OEZE** (`File` -> `Load ROM`).
2. Go to `Components` -> `Logo`.
3. Click `Browse` and select an image (**1024x768**, format **only BMP (16-color image)**, size **less than 900 KB**).
4. Click `Apply`. In the conversion/compression window, be sure to click **`Yes`**.
5. Save the firmware: `File` -> `Save`.

---

## 🔌 INSTRUCTION 4: Final Flashing

1. Open **AsProgrammer**.
2. Erase the memory chip on the laptop motherboard.
3. Open the final `mod_bios.rom` and write it to the chip. 
4. Wait for the verification to finish.
5. Check your laptop for turning on and entering the BIOS and System before reassembling.
6. If everything is fine, then safely assemble the laptop. Done!

---

*(If you have any problems — write to byteghosthelper@gmail.com, I will try to help with whatever I can. Also, for a faster response, you can drop a link to my repository to any artificial intelligence (with internet access, for example, Gemini, Qwen, or DeepSeek) asking to explain everything more in detail and clearly, if my instructions turn out to be insufficient).*

[ ⬆️ Back to the top ](#n)
