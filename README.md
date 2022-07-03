# 
Для работы лично для меня удобно, когда классы лежат в разных папках, поэтому первым делом пересортирую фото. (0_Sort.ipynb)

Потом беру исходный датасет и просто обучаю EfficientnetB7 в колабе про с earlyStopping, reduce_lr_loss и сохранением лучшей модели на гугл дист, на случай если колаб отвалиться. Когда отваливаеться по earlyStopping, беру предпоследнюю модель и еще раз прогоняю. чтобы исключить попадание в локальный минимум.
(1_preTrain_EfficientnetB7.ipynb)

Следующим этапом аугментирую имеющийся датасет. Логика следующая: 0 и 2 класс можно кропать без ограничения, т.к. любая часть фото будет попадать в свой же класс. Для 1 класс важно попал ли бачок в кропнутую фото, поэтому я проверяю это обученной моделью на предедущем этапе. (2_aug.ipynb)

По такой же логике аугментирую фото из янкекса, которые выпали на заппрос "мусорный контейнер" и подобные запросы. (3_aug_pars.ipynb)

Таким образом появляеться датасет в примерно 7500 изображенй. 
На котором уже и обучаюсь. (4_Train_EfficientnetB7.ipynb)

Обучался несколько дней c откатом и эксперементами с Learning Rate на nVidia Tesla P40, т.к. батч можно сделать больше чем на колабе про и не отваливается по времени. 
