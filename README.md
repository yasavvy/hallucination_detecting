##### Изменение решения

Обратите внимание, система настроена таким образом, что тестовый датасет должен иметь название и располагаться строго
в `data/test.csv`.
Результат работы (предсказание) тоже должно иметь строгое название и путь: `data/subsmission.csv`.

##### Обучение модели

**Обратите внимание: обучение модели проходит на Ваших локальных устройствах, так как моя сохранённая модель слишком велика для загрузки (значительно превышает ограничение в 25 Мб). Возьмите код "model", сохраните модель в папку saved_models (всё настроено таким образом, что Ваша сохранённая модель должна находится по пути saved_models/"model name"). Назовите сохранённую модель, как желаете, и убедитесь, что во всех релевантных файлах скорректировали название сохранённой модели.** Также, для примера, вы можете использовать скрипт `train_baseline.py` и самостоятельно разбить `train.csv` на обучающие и тестовые выборки для локальных тестов

После работы, обучите модель на полном наборе `train.csv`.

##### Сборка решения
```shell
docker build . -t x5_halluc
```

##### сделайте git push с весами

```shell
git add .
git commit -a -m"my solution"
git push
```

##### Запустите инференс make submission py

```shell
docker run -it --network none --shm-size 2G --name x5_halluc -v ./data:/app/data x5_halluc python make_prediction.py
```

По итогу выполнения команды, файл с решением `submission.csv` появится в папке `data`. Проверьте его на правильность структуры. При желании, можете запустить расчет метрики на нём. Пример файла с расчетом метрики вы можете найти в корне репозитория.
