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


Value                  | Negative Event                                                                 | Damage Level | Comment                                                                 |
|------------------------|-------------------------------------------------------------------------------|--------------|-------------------------------------------------------------------------|
| **Passenger Safety**   | False biometric match (unauthorized access or denial of legitimate passenger) | High         | Risk of conflicts, delays, and loss of trust in the system.            |
| **Data Privacy**       | Biometric data leak (facial/payment info)                                     | Critical     | Legal consequences, reputation loss, GDPR/FZ-152 fines.                |
| **System Reliability** | Payment system failure (scanner/transaction error)                            | Medium       | Service disruption → free rides or halted operations.                  |
| **Boarding Speed**     | Delays due to slow/erratic facial recognition                                | Medium       | Passenger queues, dissatisfaction.                                     |
| **Autonomy**           | Navigation system failure (route/obstacle misdetection)                      | High         | Accident risk, need for manual override (if available).                |

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
