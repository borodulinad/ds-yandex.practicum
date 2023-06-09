# Определение стоимости автомобилей
Сервис по продаже автомобилей с пробегом «Не бит, не крашен» разрабатывает приложение для привлечения новых клиентов. В нём можно быстро узнать рыночную стоимость своего автомобиля. В нашем распоряжении исторические данные: технические характеристики, комплектации и цены автомобилей.

Цель: построить модель для определения стоимости автомобиля.

Ключевые моменты:
- качество предсказания;
- скорость предсказания;
- время обучения;
- RMSE < 2500.

# Итоги 
За основу были взяты модели линейной регрессии, дерева решений, CatBoost и LightGBM.

Линейная регрессия показала плохие результаты (RMSE около 3000), поэтому на тестовой выборке ее не прогоняли.
Дерево решений на обучающей выборке показало результат лучше, чем у линейной регрессии. RMSE около 2000.
Но, конечно, надежды возлагались на модели градиентного бустинга. Они показали хорошие результаты на обучающей выборке, однако временные затраты очень большие, особенно у CatBoost. У LGBM метрика RMSE оказалась меньше всех, а также время поиска наилучших параметров меньше, чем у catboost.
На тестовой выборке прогонялись модели дерева решений, а также обе модели градиентного бустинга. Наилучший результат, как количественный, так и временной, показала модель LGBM. CatBoost долго обучается, зато делает быстрее предсказания, чем lgbm.

Таким образом, цель и условия заказчика были выполнены. В рамках этого проекта наилучшей оказалась модель LightGBM.

На тестовой выборке RMSE составило 1654.4783143353518.

# Стек
Pandas, matplotlib, numpy, scikit-learn, seaborn, ydata_profiling, phik, category_encoders, CatBoost, XGBoost, LightGBM. 
