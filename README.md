# -
Краткое описание назначения и применения продукта


Продукт - автономный автобус с бесконтактной оплатой проезда на основе биометрии
Автобус сканирует лицо пассажира на входе и проводит оплату после идентификации.

  ![image](https://github.com/user-attachments/assets/a9ed372a-a1fa-486d-8511-f23937d3a2d5)

**Преимущества:**

✔ Снижение затрат на обслуживание (нет кассиров и валидаторов).

✔ Ускорение посадки за счет автоматизированного процесса.

✔ Гигиеничность (минимум касаний поверхностей).

✔ Интеграция с мобильными приложениями и банковскими системами

**Роли пользователей**

Оператор системы - вводит информацию о маршрутах

Сотрудник депо - проверяет системы автобуса перед выходом на маршрут

Пассажиры - перемещаются в автобусе согласно маршруту

Ключевые ценности, ущербы, неприемлемые события


### Ключевые ценности, риски и неприемлемые события для автономного автобуса с биометрической оплатой

| Ценность                | Негативное событие                                                                 | Уровень ущерба | Комментарий                                                                 |
|-------------------------|-----------------------------------------------------------------------------------|----------------|-----------------------------------------------------------------------------|
| **Безопасность**        | Ложное срабатывание биометрии (пропуск постороннего/отказ законному пассажиру)    | Высокий        | Риск конфликтов, задержек, подрыв доверия к системе                        |
| **Конфиденциальность**  | Утечка биометрических данных (лиц, платежной информации)                          | Критический    | Юридические последствия, репутационный ущерб, штрафы по GDPR/152-ФЗ        |
| **Надежность системы**  | Сбой оплаты (ошибка сканера/транзакции)                                           | Средний        | Прерывание работы → бесплатный проезд или остановка транспорта             |
| **Скорость посадки**    | Задержки из-за медленного распознавания                                           | Средний        | Образование очередей, недовольство пассажиров                             |
| **Автономность**        | Отказ системы навигации (ошибки маршрута/распознавания препятствий)               | Высокий        | Риск ДТП, необходимость ручного вмешательства                              |


**Контекст**

фото

**Основные функциональные сценарии**

![image](https://github.com/user-attachments/assets/d48b4842-3e52-4429-8137-b96aa53c401d)


**Высокоуровневая архитектура**

![image](https://github.com/user-attachments/assets/5ec76da5-0311-46b0-8c01-d9e7cd111656)

## Подсистемы

| Подсистема   | Назначение                                                                 | Компоненты/Функции                                                                 |
|--------------|----------------------------------------------------------------------------|-----------------------------------------------------------------------------------|
| **Пассажир** | Инициатор процесса: использует сервис для входа в автобус                  | • Сканирование лица через терминал<br>• Взаимодействие с системой доступа         |
| **Биометрия** | Идентификация пользователя по лицу                                         | • HD-камеры с ИК-подсветкой<br>• FaceNet для распознавания<br>• Liveness Check    |
| **Платежи**  | Проведение транзакции и управление доступом                                | • Проверка баланса в реальном времени<br>• Оффлайн-кеш на 100 транзакций          |
| **Банк**     | Подтверждение платежей и обработка финансовых операций                     | • REST API с PSD2-совместимостью<br>• Система анализа мошенничества               |
| **Управление** | Контроль физических систем автобуса                                       | • CAN-шина для управления дверьми<br>• Датчики безопасности (закрытие при движении)|
| **Двери**    | Механизм предоставления доступа                                            | • Электропривод 24V<br>• Аварийный ручной размыкатель                            |
| **Сеть**     | Передача данных между компонентами                                         | • 5G/LTE модем с dual-SIM<br>• Локальное хранилище логов (SQLite)                 |


**Расширенные диаграммы функциональных сценариев**
иллюстрация взаимодействия подсистем, указанных в высокоуровневой архитектуре

![image](https://github.com/user-attachments/assets/8c413de1-7dc2-4e6a-91a6-3ab52eaf8e54)

**Цели и предположения безопасности**

**Цели безопасности**
1. Конфиденциальность данных - Шифрование данных на всех этапах передачи и хранения;
2. Целостность операций - Предотвращение подмены биометрических идентификаторо  и Гарантия неизменности транзакций и логируемых событий;
3. Доступность системы - Резервирование критических компонентов работа в оффлайн-режиме;
4. Аутентичность пользователей - Защита от поддельных биометрических данных;
   
**Предположения безопасности**
1. Шифрование данных - Используемые алгоритмы (AES-256, ГОСТ Р 34.12-2015) соответствуют стандартам;
2. Сетевая инфраструктура - защиту каналов связи;
3. Регулярное обслуживание ПО
4. Физическая защита - банка и оборудования

**Таблица соотнесения ценностей, неприемлемых событий и целей безопасности**

| Ценность                      | Неприемлемое событие                     | Оценка ущерба | Цель безопасности                          |
|-------------------------------|------------------------------------------|---------------|--------------------------------------------|
| **Биометрические данные**     | Утечка/кража биометрических шаблонов     | Высокий       | Конфиденциальность, Аутентичность          |
| **Платежные транзакции**      | Подмена/отмена транзакций                | Высокий       | Целостность, Неотказуемость               |
| **Доступность автобуса**      | DDoS-атака на сетевой модуль             | Средний       | Доступность, Резервирование               |
| **Физические механизмы**      | Несанкционированное открытие/блокировка  | Критический   | Контроль доступа, Аутентичность           |
| **Логи операций**             | Фальсификация/удаление записей           | Средний       | Целостность, Неотказуемость               |
| **Пользовательский интерфейс**| Фишинг/ввод ложных данных                | Низкий        | -  |


**Негативные сценарии**

фото

**Политика архитектуры**
