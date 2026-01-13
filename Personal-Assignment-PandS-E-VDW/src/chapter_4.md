# 1. Machine SEQ diagram between 3 tasks

## TASK MAIN
task Main geeft een temperatuur setpoint door aan task temp monitor en aan task heater.<br>

task Main bevat een resetknop. Deze kan de temperatuursensor van task temp_monitor resetten naar 30 graden. Met functie om een de watertemperatuur naar 30 graden te resetten.<br>

task Main bevat een cooldown knop. Deze kan de GVL temperatuursensor omlaag brengen met -5 graden per klik. Die GVL wordt ook gebruikt door de task Temp monitor.<br>


## TASK HEATER
task Heater leest de GVL temp sensor, en aan de hand daarvan geeft hij aan temp monitor door of de heater aan of uit staat met GVL heater. <br>

## TASK TEMP MONITOR
task Temp monitor schrijft naar en leest van GVL temp sensor. Deze task ontvangt of GVL heater aan of uit staat en leest wat GVL temp setpoint is. <br>

```plantuml
@startuml

@startuml
MAIN -> TEMPERATURE_MONITOR : GVL_TEMP_SETPOINT
MAIN <-> TEMPERATURE_MONITOR : GVL_TEMP_SENSOR
MAIN -> HEATING : GVL_TEMP_SETPOINT
MAIN -> HEATING : GVL_TEMP_SENSOR
HEATING -> TEMPERATURE_MONITOR : GVL_HEATER
@enduml

@enduml
```plantuml

