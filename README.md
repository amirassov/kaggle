# kaggle
Генерация признаков
1. Вещественные признаки:
  a) Для каждого героя извлекаем следующие признаки:
    [r/d]i_xp: максимальный полученный опыт
    [r/d]i_gold: достигнутая ценность героя
    [r/d]i_lh: число убитых юнитов
    [r/d]i_kills: число убитых игроков
    [r/d]i_deaths: число смертей героя
    [r/d]i_items: число купленных предметов
  b) Сортируем эти признаки по каждой команде и берем разность данных признаков. В итоге получим 5х6 = 30 признаков

2. Уровни героев:
  а) Генерим мешок слов над уровнями героев в диапазоне [0, 7]
  
3. Тип лобби:
  a) OneHotEncoding
  
4. Первая кровь:
  а) 0, если radiant
     1, если dire
     0.5, иначе.
     
5. Герои:
  а) Мешок слов
  b) Синергия и антисинергия с 7 фолдами

Объединяем и стандартизуем все признаки и получим матрицы X_train и X_test

6. Метапризнаки:
  a) Градиентный бустинг над X_train c 10 фолдами

Объединяем c X_train и X_test и получим матрицы DATA и TDATA

Обучение:
Над X_train обучим XGBoost, а над DATA LogisticRegression

Контрольная модель:
0.72*LogisticRegression + 0.28*XGBoost
