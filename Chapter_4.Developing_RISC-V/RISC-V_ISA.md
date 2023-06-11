# Руководство по архитектуре набора команд RISC-V
## Определение архитектуры набора инструкций (ISA)
Архитектура набора команд (ISA) - это абстрактная модель компьютера. 
Ее также называют архитектурой или архитектурой компьютера. Реализация ISA, например, центральный процессор (CPU), называется реализацией. 
Некоторые ISA, о которых вы могли слышать, включают x86, ARM, MIPS, PowerPC или SPARC. Все эти ISA требуют лицензии для их реализации. 
С другой стороны, RISC-V ISA предоставляется под лицензией с открытым исходным кодом, которая не требует платы за использование.

## Чем отличается ISA RISC-V
Наиболее заметным отличием RISC-V от других ISA является то, что RISC-V разрабатывается организацией-членом, 
в которую можно вступить совершенно бесплатно, и лицензирует свои ISA на основе разрешительных лицензий с открытым исходным кодом. 
Это означает, что любой может внести свой вклад в спецификации, и ни одна компания или группа компаний не может определять направление развития стандартов.

RISC-V International управляется Советом директоров. Совет состоит из членов, избранных для представления всех классов членства, 
чтобы обеспечить стратегический голос на всех уровнях. Кроме того, Технический руководящий комитет (TSC) обеспечивает руководство 
нашими техническими инициативами в определении долгосрочной стратегии, формировании тактических комитетов и рабочих групп, 
а также утверждении технических результатов для ратификации или выпуска.

## Модель совместного развития
Спецификация RISC-V начинает свою жизнь как целевая группа, утвержденная Техническим руководящим комитетом (TSC). 
После того, как целевая группа получила утвержденный устав, она начинает публичную работу на GitHub, 
записывая свои документы в формате AsciiDoc. Эти репозитории на GitHub могут получать запросы на исправление только от членов RISC-V International, 
однако работа ведется публично и прозрачно. Для групп, решивших вести протоколы, протоколы заседаний целевых групп также публикуются в открытом доступе. 
Общественность может свободно отправлять вопросы в репозиторий GitHub, чтобы дать раннюю обратную связь по любой спецификации. 
Спецификации и стандарты, не относящиеся к ISA (например, трассировка процессора, архитектурные тесты, наложение программного обеспечения), 
разрабатываются аналогичным образом.

![image](https://github.com/mt-omarov/Intro-to-RISC-V/assets/95280619/38a4fee2-4292-4ee4-bbc5-feae46c47870)

Спецификации RISC-V размещены на GitHub и находятся рядом с десятками программных проектов. 
Смотрите [список ратифицированных спецификаций](https://riscv.org/technical/specifications/) и ссылки на их репозитории на GitHub.

## Создание и курирование открытых спецификаций
Процесс написания спецификаций обычно возглавляет архитектор аппаратного обеспечения в одной из организаций-членов RISC-V International. 
Они могут не писать фактический текст, но они выступают в качестве председателя целевой группы, контролирующей разработку спецификации. 
Для завершения разработки спецификации группе может потребоваться от нескольких месяцев до более года. 
О жизненном цикле расширения мы поговорим позже в этой главе.

То, что делает этот процесс разработки открытым, зависит от трех ключевых фактов:
1. Список рассылки целевой группы является общедоступным.
2. Документ спецификации находится в открытом доступе, и к нему можно оставлять комментарии.
3. Существует публичный список рассылки, в котором любой желающий может отправить электронное письмо. (isa-dev@groups.riscv.org)

Используя эту методологию, даже не являющиеся членами организации, могут участвовать в разработке любой спецификации или стандарта, задавая вопросы, 
внося предложения или просто следя за ходом работы. Более того, в процессе ратификации существует 45-дневное окно, когда вся работа над спецификацией 
должна быть заморожена, а спецификация опубликована публично для ознакомления. В это время все желающие могут высказать свои замечания, 
и все вопросы будут решены до голосования за ратификацию.

Хотя стать членом RISC-V International - самый простой способ внести свой вклад в открытые спецификации, это не единственный способ. 
Любой может внести свой вклад, взаимодействуя с целевыми группами на публичных форумах, таких как список рассылки и GitHub.

## Жизненный цикл расширений RISC-V
Каждое расширение RISC-V проходит несколько этапов на пути к ратификации. В этом разделе мы кратко рассмотрим каждый этап, известный как "веха".

1. План \
   Целевая группа разрабатывает окончательный устав и устанавливает некоторые временные рамки.
2. Разработка \
   Группа выпускает несколько версий, которые считаются нестабильными.
3. Заморозка \
   Группа выпускает полный окончательный проект спецификации, в котором нет основных неизвестных и ожидаемых изменений (только исправление проблем, но без новых возможностей).
4. Готовность к ратификации \
   Проект спецификации рассылается для публичного рассмотрения, любые комментарии или вопросы общественности рассматриваются, и Технический руководящий комитет ставится в известность о необходимости голосования.
5. Развитие экосистемы \
   Расширение ратифицировано и поддерживается как часть RISC-V ISA. Сообществу еще предстоит решить множество задач. Например, спецификация Vector была ратифицирована, однако добавление автовекторизации в компиляторы является частью списка задач по развитию экосистемы этой спецификации.
   
![image](https://github.com/mt-omarov/Intro-to-RISC-V/assets/95280619/ec6046be-1532-4e01-9f32-aa8924586807)

После ратификации расширения оно добавляется либо в непривилегированную, либо в привилегированную спецификацию. 
Иногда спецификация создается как часть отдельного документа, наиболее распространенным примером является спецификация отладки. 
Однако это редкий случай и обычно указывает на то, что расширение не является частью ISA, а скорее "стандартной" или "не-ISA спецификацией". 
Теперь мы рассмотрим непривилегированную и привилегированную спецификации более подробно.