# Diagrama de definição de blocos 
> Um Diagrama de Definição de Bloco é um diagrama estrutural estático que mostra os componentes do sistema, seus conteúdos (propriedades, comportamentos, restrições), interfaces e relacionamentos.

No alarme inteligente o diagrama de definição de blocos foi utilizado para representar quais as partes constituintes do sistema. O diagrama descreve os principais componentes do alarme inteligente e as relações presentes entre eles. 

<img width="1180" height="430" alt="Block Definition Diagram1" src="https://github.com/user-attachments/assets/c8d4d714-29aa-4755-998f-618b9bfb4cf2" />

A figura acima mostra os 6 blocos presentes no sistema que são: AlarmSoC, ControlProcessor, ConfigurationMemory, AlarmController, StatusInterface e o SensorInterface. Cinco dos seis blocos estão ligados ao AlarmSoC por meio de uma relação de composição, em que os blocos inferiores não existem independentemente do bloco AlarmSoC. Assim, se o bloco AlarmSoC for destruído, todas as suas partes também são excluídas em cascata.

