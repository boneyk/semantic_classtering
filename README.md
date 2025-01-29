# semantic_classtering

В данной работе была произведена кластеризация по запросам с сервиса по поиску работы Фарпост. 

Поисковые запросы пользователей часто включают в себя определённые слова, позволяющие отнести запрос к некоторой категории. В частности, запросы о поиске работы часто содержат в явном или неявном виде профессию, условия работы, форму занятости и т.д. Учёт семантики пользовательских запросов позволит повысить релевантность поисковой выдачи, проводить более глубокую аналитику.

### Проблема:
Повышение релевантности поисковой выдачи

### Целевая аудитория
Компания Farpost. В пределе - Пользователи, Администраторы сайтов объявлений, маркетплейсов и т.д.

### Основной функционал
В минимальном варианте для решения кейса необходимо сделать алгоритм, который кластеризует запросы, выделить с помощью него семантические группы. В итоге по входному списку поисковых запросов должен выдаваться список запросов с кластерами для них по разным семантическим признакам.
Кластеризацию сделать по следующим признакам (https://www.farpost.ru/rabota/vacansii/):

●       по занятости (Фильтр Занятость: подработка, ночная, вечерняя, посменная, вахта и тд.)

●       по должности-лемме (повар, строитель, водитель и тд.)

●       по дополнительному признаку: для инвалидов, для студентов, для школьников, для пенсионеров, для мужчин, для женщин

●       по условиям: с ежедневной оплатой, с проживанием

●       общие фразы про работу (не содержит других признаков)

Одна и та же фраза может попасть в разные кластеры (например "сторож вахтер пенсионер вакансии")

### Реализация задачи
Данная задача была решена в три этапа:

1. [Очистка данных и Лемматизация](Очистка%20данных%20и%20Лемматизация.ipynb/)

В данном разделе проводилась очистка данных от лишних предлогов и перевод фраз в начальную форму для дальнейшей класстеризации.

2. [Обучение модели кластеризации](Обучение%20модели%20кластеризации.ipynb/) 

В данном разделе проходило обучение модели кластеризации с помощью метода KMeans, разделение запросов на кластеры и задание определенного наименования каждому кластеру по самым частым фразам для данного кластера.

Данный шаг может быть полезен для сервиса по поиску работы, так как кластеризация запросов позволит:

- Группировать похожие вакансии и запросы — пользователи смогут быстрее находить релевантные предложения.
- Определять популярные направления и тренды — анализируя кластеры, можно выявлять востребованные навыки и профессии.
- Улучшать рекомендации — сервис сможет предлагать пользователям вакансии, которые соответствуют их интересам и предыдущим поисковым запросам.
- Автоматически подбирать категории — формирование удобных тематических подборок вакансий на основе ключевых слов в запросах.
- Оптимизировать работу поиска — за счет понимания структуры запросов можно улучшать релевантность выдачи.

3. [Обработка категориальных признаков](Обработка%20категориальных%20признаков.ipynb/)

В данном разделе проходила обработка категориальных признаков для каждого запроса, были определены разные семантические признаки для каждого запроса.
