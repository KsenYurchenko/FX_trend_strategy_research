# FX_trend_strategy_research
Тест трендовой стратегии на рынке FOREX EURUSD
 
!  ЗДЕСЬ НЕТ И НЕ ПРЕДПОЛАГАЕТСЯ ML-модели.

!  Это незаконченный ресерч с визуализацией на рынке Forex. 

ОТЛИЧИЕ ОТ TSLAB и прочих конструкторов и тестеров стратегий в том, что можно

- написать кастомизированные индикаторы

- более полная картина с распределением по прибылям/убыткам.

* Код плохо закомментирован и структурирован, потому что необходимости в его доработке не было.

 ______________________________

Принципы, лежащие в основе технического анализа:

1. Начавшаяся тенденция, по всей вероятности, будет стремиться развиваться и далее, а не обращаться в собственную противоположность. 

2. Действующая тенденция будет развиваться до тех пор, пока не появятся фундаментальные факторы способные повлиять на направление движения цены.

Таким образом, наиболее оптимальное соотношение риск/доходность можно получить при работе по тренду (а не против него).
_____________

Основа тестируемой стратегии: 

1. определение начала тренда

2. открытие сделки в направлении тренда

3. определение окончания тренда и закрытие сделки.
______________________________

Одним из способов определить начало новой тенденции может быть индикатор RSI.

`RSI (Relative strength index, индекс относительной силы)` — индикатор технического анализа, показывающий соотношение положительных и отрицательных изменений цены финансового инструмента.

Индекс относительной силы может давать сигнал к покупке или продаже несколькими способами:

- пересечение 50 

- дивергенция 

- перекупленность и перепроданность 

- линии тренда.
 
Пересечение индикатором уровня 50 означает, что преобладающим становится усредненное движение либо вверх, либо вниз. Такое пересечение может свидетельствовать о начале тренда. 
______________________

Для следования за тенденцией часто используется `Скользящее среднее` : в данном случае было выбрано экспоненциально-сглаженное скользящее среднее(EMA), т к оно учитывает всю прошлую ценовую истрию, больше веса придает последним значениям, менее чувствительно к волатильности (относительно линейно-взвешенного ск.ср.).

Осциллятор MACD - производная от EMA, может помочь определить разворот тренда.

`Момент (Momentum)` – индикатор, отслеживающий рост или снижение скорости движения тренда. Он обычно достигает экстремальных значений раньше цен и может использоваться как сигнал для закрытия сделки. 

Цель: протестировать стратегию торговли по тренду с помощью индикаторов RSI, EMA, МАCD и Momentum с различными настройками.

Определить, возможно ли только с помощью этих индикаторов (не учитывая обемы и пр) определять начало тенденции и точку входа? (начало тенденции - да, точку входа - скорее нет, нужны уровни).

Рассчитать потенциальную прибыль от следования такой стратегии.

Задачи:

1. Рассчитать индикаторы RSI, EMA, МАCD и Momentum

2. Проанализировать значения индикаторов и их взаимосвязь

3. Смоделировать работу по стратегии на исторических данных

4. Оценить потенциальный и фактический апсайд/даунсайд

5. Оценить вероятность получения прибыли при работе по данной стратегии с учетом комиссий и спредов.

Данные: https://drive.google.com/drive/folders/1ebtuAIzz9Z3yRZFfHBxTHJTjgIgXrMeb

Импорт торговой истории валютной пары EURUSD рынка FOREX брокера GrandCapital за период 01.01.2021г-01.04.2024г. Таймфрейм: 5 минут.


Выводы:

В целом, направление тренда помогают определить EMA с различными периродами (быстрым и медленным).
 
При входе в сделку на восходящих EMA и через 4 свечи после пересечения RSI 50% апсайды в среднем будут больше даунсайдов, т е такой подход имеет смысл и удачнее "случайного" входа в сделку. При "случайном" входе распределение апсайдов/даунсайдов было бы симметричным, а итоговый фин рез нулевым, без учета комиссий и спредов.

Если выходить из сделки только при обратном пересечении RSI, то с учетом спредов и комиссии, стратегия получает чистый убыток.

Стратегия имеет смысл, если скорректировать точки входа и выхода по уровням поддержки-сопротивления, при этом ориентируясь на скользящие средние и RSI.
