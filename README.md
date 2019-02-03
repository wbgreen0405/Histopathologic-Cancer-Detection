
![alt text](http://www.innovationandtech.ae/wp-content/uploads/2018/01/Cancer-Prognosis-Prediction-using-AI-810x324.jpg)

***Рак молочной железы занимает второе место по уровню смертности среди женщин*** после рака легких. Согласно клинической статистике, у 1 из каждых 8 женщин в течение жизни диагностируется рак молочной железы. Тем не менее, периодические клинические осмотры и самопроверки помогают в раннем его выявлении, и таким образом значительно увеличивают шансы на выживание. [Инвазивные методы](https://ru.wikipedia.org/wiki/%D0%98%D0%BD%D0%B2%D0%B0%D0%B7%D0%B8%D0%B2%D0%BD%D0%B0%D1%8F_%D0%BF%D1%80%D0%BE%D1%86%D0%B5%D0%B4%D1%83%D1%80%D0%B0) обнаружения вызывают разрыв опухоли, ускоряя распространение рака в прилегающие районы. Следовательно, возникает необходимость в более надежной, быстрой, точной и эффективной неинвазивной системе обнаружения рака (Selvathi, D&Aarthy Poornila, A.(2018). Методы глубокого обучения для обнаружения рака молочной железы с использованием анализа медицинских изображений).

Раннее выявление может дать пациентам больше вариантов лечения. Чтобы обнаружить признаки рака, ткани молочной железы от биопсии окрашивают, чтобы улучшить ядра и цитоплазму для микроскопического исследования. Затем патологи оценивают степень любого ненормального структурного изменения, чтобы определить, есть ли опухоли.

Архитектурное искажение является очень тонким уплотнением ткани молочной железы и может представлять самый ранний признак рака. Поскольку радиологи скорее всего этого не заметят,за эти годы было предложено несколько подходов для раннего обнаружения,но ни один из них не использует методы глубокого обучения.

В своей "Эпохи Возрождения" Deep Learning стал лидирующим ветлением машинного обучения которое более 10 лет используеться во многих отраслях жизни человека,в том числе и в здравоохранении, ключевым требованием методов глубокого обучения являеться данные,которые в данном слусае предаставляет платформа Kaggle в [соревновании](https://www.kaggle.com/c/histopathologic-cancer-detection) для решения гистопатологической диагностики рака.

---
### Понимание Задачи

***В чем заключается задача ?***

****Задача классификации двумерных изображений****. Необходимо определить наличие метастазов по цифровым гистопатологическим изображениям размером 96x96 пикселей. Одна из ключевых проблем заключается в том, что метастазы могут быть такими же маленькими, как отдельные клетки в большой области ткани.

#### Что известно о данных?
****Гистопатологические изображения представляют собой микроскопические изображения стекловидных слайдов лимфатических узлов, окрашенных гематоксилином и эозином (H&E)****. Этот метод окрашивания является одним из наиболее широко используемых в медицинской диагностике,он окрашивает в синий, фиолетовый и красный цвет.Темно-синий - гематоксилин связывается с отрицательно заряженными веществами, такими как нуклеиновые кислоты,Розовый - эозин, с положительно заряженными веществами, такими как боковые цепи аминокислот (большинство белков). Обычно ядра окрашиваются в синий цвет, тогда как цитоплазма и внеклеточные части имеют различные оттенки розового.

**Низкое разрешение**             | **Среднее разрешение**            | **Высокое разрешение** 
:-------------------------:|:-------------------------:|:-------------------------:
![](https://camelyon17.grand-challenge.org/site/CAMELYON17/serve/public_html/example_low_resolution.png) | ![Example of a metastatic region](https://camelyon17.grand-challenge.org/site/CAMELYON17/serve/public_html/example_mid_resolution.png) | ![Example of a metastatic region](https://camelyon17.grand-challenge.org/site/CAMELYON17/serve/public_html/example_high_resolution.png)


***[Пример метастатической области в лимфатических узлах, CHAMELYON17](https://camelyon17.grand-challenge.org/Background/
)***



Лимфатические узлы - это маленькие железы, которые фильтруют жидкость в лимфатической системе, и они являются первым местом распространения рака молочной железы. Гистологическая оценка метастазов в лимфатических узлах является частью определения стадии рака молочной железы в классификации [TNM](http://www.lood.ru/diagnostics/tnm.html), которая является общепризнанным стандартом для классификации степени распространения рака. Диагностическая процедура для патологов утомительна и отнимает много времени, поскольку необходимо исследовать большую площадь ткани легко пропустить мелкие метастазы.

***Полезные ссылки для базовых знаний:***

+ [Набор данных Camelyon (PCam)](https://github.com/basveeling/pcam)
+ [Окрашивание гематоксилином и эозином срезов тканей и клеток](https://www.ncbi.nlm.nih.gov/pubmed/21356829)
+ [H&E-окрашенные участки дозорных лимфатических узлов у пациентов с раком молочной железы: набор данных CAMELYON](https://academic.oup.com/gigascience/article/7/6/giy065/5026175)
+ [CAMELYON16](https://camelyon16.grand-challenge.org/Background/)
+ [CAMELYON17](https://camelyon17.grand-challenge.org/Background/)
+ [TNM Классификация](https://ru.wikipedia.org/wiki/TNM)

---

### Понимание данных

#### Какие предоставляються данные для решения задачи ?

****220тыс. Тренировочных и 57тыс. Оценочных изображений****. Набор данных является подмножеством набора данных [PCam](https://github.com/basveeling/pcam), и единственное различие между ними состоит в том, что в предоставленных нам данных  все повторяющиеся изображения были удалены. Набор данных PCam получен из набора данных [Camelyon16 Challenge](https://camelyon16.grand-challenge.org/Data/), который содержит 400 H&E-окрашенных полных изображений слайдов дозорных срезов лимфатических узлов, которые были получены и оцифрованы в 2 разных центрах с использованием объектива 40x. Набор данных PCam, включая этот, использует 10-кратную пониженную дискретизацию для увеличения поля зрения, что дает результирующее разрешение пикселей 2,43 микрона.

Сторожевым лимфоузлом называется лимфоузел, в который первым осуществляется отток лимфы от опухоли, следовательно, он в первую очередь оказывается пораженным. В литературе можно встретить две особенности, характеризующие СЛУ. Первая - это ближайший к опухоли лимфатический узел и вторая - этот узел поражается метастазами в первую очередь.


Согласно описанию [данных](https://www.kaggle.com/c/histopathologic-cancer-detection), между положительными и отрицательными примерами ****в обучающем и тестовом подмножестве существует баланс 50/50***. Тем не менее, распределение обучения составляет 60/40 (негативы/позитивы). Положительная метка означает, что в центральной области (32 x 32 пикселя) изображения имеется как минимум один пиксель опухолевой ткани.***Опухолевая ткань в отдаленный от центра области слайда не влияет на метку****. Это означает, что отрицательно помеченное изображение может содержать метастазы в центральной  области.Таким образом,обрезав изображения в центральной области,информация не потеряется.

**Описание предоставленных снимков**
Формат: TIF
Разрешение: 96x96
Каналы: 3
Глубина цвета: 8
Тип данных: Unsigned char
Тип сжатия: Jpeg

---
### Насколько качественные данные ?
Этот набор данных представляет собой комбинацию двух независимых наборов данных, собранных в Университетском медицинском центре Radboud (Nijmegen, the Netherlands) и Университетском медицинском центре Utrecht (Utrecht, the Netherlands).Слайды производятся в соответствии с обычной клинической практикой, и обученный патологоанатом должен изучить подобные изображения для выявления метастазов. Тем не менее, с этими образцами изображений небольшого размера,некоторая важная информация могла быть утерена.


Согласно описанию данных, набор данных лишен дубликатов. Однако это не было подтверждено тестированием.

Для всего набора данных, когда метка уровня слайда была неясной во время проверки окрашенного H&E стекловидного стекла, для подтверждения классификации использовался дополнительный слой пленки WSI с последовательным срезом ткани, иммуногистохимически окрашенный на цитокератин.
+ https://academic.oup.com/gigascience/article/7/6/giy065/5026175

Все стекловидные слайды включенные в набор данных CAMELYON, были частью обычным клиническим диагностированием,это означает что данные имеют диагностическое качество. Однако во время процесса сканирования, сканирование может завершиться сбоем или привести к получению не в фокусе изображений. В качестве меры контроля качества, все слайды проверялись вручную после сканирования. Проверка проводилась опытным техником (Q.M. и N.S. для UMCU, M.H. или R.vd.L. для других центров) для оценки качества сканирования.

---
***Углубленное понимание:***

+ [О технике детектирования с использованием пленки wsi](https://ilt.kharkov.ua/bvi/structure/d16/ru/nonequil_eff.html)
+ [Иммуногистохимические маркеры в диагностике, стадирование и прогнозе различных форм уротелиальной карциномы](https://www.science-education.ru/ru/article/view?id=4962)
+ [Боковые цепи](http://chem21.info/info/1304270/)
+ [Биопсия](https://megabook.ru/article/%D0%91%D0%B8%D0%BE%D0%BF%D1%81%D0%B8%D1%8F%20(%D0%BC%D0%B5%D0%B4%D0%B8%D1%86%D0%B8%D0%BD%D0%B0))
+ [Видео с комментариями гистологического среза почки в световом микроскопе](https://www.youtube.com/watch?v=Po5J67mW1JM)
