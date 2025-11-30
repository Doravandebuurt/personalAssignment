# 1. Proces Flowchart

The Twincat plc bakcup is in a seperate repository:

https://github.com/Doravandebuurt/personalassignmentPLC

The proces that my virtual PLC program describes, is the automation of handeling of water in an aquarium. the Flowchart of the process can be find below.

```plantuml
@startuml AquariumFilter

title Aquarium Filter Automation

start
:Idle;

if ("Start pressed?") then (yes)
  :Start 30s timer;
  fork
    
    :Filter water pump on 30s;
  fork again
    :Wait 5 seconds;
    :CO2 ON;
    :Wait until 20 seconds;
    :CO2 OFF;
  fork again
    :Wait 10 seconds;
    :Lights ON;
    :Wait untill 25 seconds;
    :Lights OFF;
  fork again
    :Temperature sensor reads water temp continuously;
    if (Temp < Setpoint?) then (yes)
        :Heater ON;
    else (no)
        :Heater OFF;
    endif
    :Repeat temperature loop 30s;
  end fork

  :End of 30s cycle;
  :Return to Idle;

else (no)
  :Remain Idle;
endif

stop

@enduml
```

