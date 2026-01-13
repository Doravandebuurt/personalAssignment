# 1. Machine SEQ diagram between 3 tasks
sequence diagram:<br>

```plantuml
@startuml

@startuml
MAIN -> TEMPERATURE_MONITOR : doorgeven temp setpoint
MAIN <-> TEMPERATURE_MONITOR : instellen en lezen temp
MAIN -> HEATING : instellen temp setpoint
MAIN -> HEATING : resetten temp setpoint
HEATING -> TEMPERATURE_MONITOR : doorgeven heater aan/uit
@enduml

@enduml
```plantuml

## TASK MAIN
task Main geeft een temperatuur setpoint door aan task temp monitor en aan task heater.<br>

task Main bevat een resetknop. Deze kan de temperatuursensor van task temp_monitor resetten naar 30 graden. Met functie om een de watertemperatuur naar 30 graden te resetten.<br>

task Main bevat een cooldown knop. Deze kan de GVL temperatuursensor omlaag brengen met -5 graden per klik. Die GVL wordt ook gebruikt door de task Temp monitor.<br>


## TASK HEATER
task Heater leest de GVL temp sensor, en aan de hand daarvan geeft hij aan temp monitor door of de heater aan of uit staat met GVL heater. <br>

## TASK TEMP MONITOR
task Temp monitor schrijft naar en leest van GVL temp sensor. Deze task ontvangt of GVL heater aan of uit staat en leest wat GVL temp setpoint is. <br>



