# Описание проекта. 
Главные задачи проекта это построение модели машинного обучения, которая предскажет вероятность снижения покупательской активности клиента, и разработка на основе данных моделирования и прибыльности клиентов персонализированных предложений для повышения покупательской активности для определенного сегмента покупателей.

В датафреймах market_file, market_time и money в процессе исследования выбросов не обнаружено. При этом в датафрейме в гистограмме распределения market_money показало явный выброс. Таблица результатов расчета по методу describe в текущем месяце показало максимальную выручку - 106862.2, что является явной аномалией при ожидаемых показателях 5000-6000.

Анализ матрицы корреляции показал, что признаки мультиколлинеарности в составе анализируемых данных не обнаружены, при этом между наблюдениями по признакам текущий_месяц_выручка и разница_предыдущий_препредыдущий_месяц_выручка показывают высокую корреляционную сходимость (0.81), что говорит о близости данных признаков по природе своего происхождения.

Для поиска лучшей модели был применен инструмент GridSearchCV и перебор гиперпараметров для четырех моделей:

- DecisionTreeClassifier()
- KNeighborsClassifier()
- LogisticRegression()
- SVC()
Лучшая модель отбиралась по метрике RECALL. Лучшей моделью оказалась LogisticRegression() с L1-регуляризацией. Для отбора признаков был использован инструмент SelectKBest.

Метрика RECALL на кросс-валидации: 0.8
Метрика RECALL на тестовой выборке: 0.83
Снижение предела отнесения наблюдения к классу 1 несет большие издержки в общей точности модели.
