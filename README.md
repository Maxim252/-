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


| Уровень урона | Комментарий |
|------------------------|-------------------------------------------------------------------------------|--------------|-------------------------------------------------------------------------|
| **Безопасность пассажиров ** | Ложное совпадение биометрических данных (несанкционированный доступ или отказ в регистрации законного пассажира) | Высокий | Риск конфликтов, задержек и потери доверия к системе.            |
| ** Конфиденциальность данных ** | Утечка биометрических данных (лица/ платежной информации) | Критическая ситуация | Юридические последствия, потеря репутации, штрафы по GDPR/FZ-152.                |
| **Надежность системы** | Сбой платежной системы (ошибка сканера/транзакции) | Среда | Сбой в обслуживании → бесплатные поездки или приостановленные операции.                  |
| ** Скорость посадки ** | Задержки из-за медленного / неустойчивого распознавания лиц | Средней скорости | Очередей пассажиров, неудовлетворенности.                                     |
| **Автономность** | Сбой навигационной системы (неправильное определение маршрута/препятствия) | Высокий риск | аварии, необходимость ручного управления (при наличии).                |

#### Дополнительные риски:
- **Кибератака** на системы управления автобусом или биометрическую базу данных
- ** Вандализм** (повреждение сканеров/камер)
- **Сбой инфраструктуры** (отсутствие подключения к банку для осуществления платежей)

#### Стратегии смягчения последствий:
- Избыточность системы (резервные сканеры, автономные платежи)
- Шифрование/анонимизация биометрических данных
- Регулярные ложноположительные/отрицательные тесты

**Контекст**

фото

**Основные функциональные сценарии**

фото

**Высокоуровневая архитектура**

фото

**Расширенные диаграммы функциональных сценариев** + фото

**Цели и предположения безопасности**

**Цели безопасности**

**При любых обстоятельствах загораются только незапрещенные сочетания
Предположения безопасности**

**физическая безопасность светофора обеспечена**

**Негативные сценарии**

фото

**Политика архитектуры**
