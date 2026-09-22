# Сушильная Камера

Проект сушильной камеры для ковекционной сушки овощей и фруктов.

- ПЛК - Coolmay L02
- HMI - Coolmay TK8150

## Библиотеки

### AlarmManager (V213+)

Управление авариями (15 ошибок ПЧ).

- Хранилище объявлено в `ПО/GVL.csv`:
  - `AM_ALARMS : ARRAY [0..14] OF ST_AM_ALARM`
  - `AM_EVENTS : ARRAY [0..0] OF ST_AM_EVENT`
  - `c_AM_ALARMS_NUM = 14`, `c_AM_EVENTS_NUM = 0`
- Инициализация — `PRG_INIT` (`FB_AM_INIT`), регистрация — `PRG_PROCESS`
  (`FB_AM_SET`), сброс — `FB_AM_RESET`, блокировка — `FB_AM_IS_BLOCK` (`PRG_MAIN`).
- Упаковка состояний аварий в M-область: `fbAMPack(DNUM := 2000, PD := c_AM_PACK_M)`
  → авария N в `M2000+N` (совместимо с прежней развёрткой `BMOV D3280 → K4M2000`).
