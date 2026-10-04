# Diagrama de Requisitos

> Um diagrama de requisitos da SysML é um diagrama estrutural estático que mostra as relações entre constructos de requisito («requirement»), elementos de modelo que os satisfazem (dependência «satisfy») e casos de teste que os verificam (dependência «verify»). O objetivo dos diagramas de requisitos é especificar os requisitos funcionais e não funcionais dentro do modelo, de forma que possam ser rastreados até outros elementos do modelo que os satisfaçam e casos de teste que os verifiquem.
 
## Elementos que podem aparecer em um diagrama de requisitos SysML
- **Requirement**: Representa uma exigência que o sistema deve atender.
- **DeriveReqt**: Simboliza que um requisito é derivado de outro requisito.
- **Satisfy**: Significa que um elemento do sistema é responsável por satisfazer determinado requisito.
- **Verify**: Essa relação mostra qual elemento verifica se um requisito foi atendido.
- **Refine**: Indica que algum elemento fornece uma descrição mais detalhada de um requisito.
- **Trace**: Representa se existe alguma correspondência ou relação entre dois elementos do modelo.
- **Copy**: Permite indicar que um requisito é uma cópia de outro requisito, mantendo a mesma definição.
- **TestCase**: Representa um caso de teste.

## Diagrama para o alarme inteligente
<img width="1717" height="1276" alt="diagrama de requisitos" src="https://github.com/user-attachments/assets/cec6e3a5-db9d-4ad9-801d-94e87d4eaaca" />

O Diagrama de Requisitos foi elaborado para representar a rastreabilidade entre os requisitos do SoC para alarme inteligente, os componentes responsáveis por seu atendimento e os casos de teste utilizados para sua verificação. Para isso, foram utilizadas as relações satisfy, verify e deriveReqt. 

A relação satisfy é utilizada para indicar quais blocos do sistema são responsáveis por atender determinados requisitos. Nesse sentido, o bloco SensorInterface está relacionado aos requisitos RF01 – Leitura de temperatura e RF02 – Leitura de fumaça, representando sua responsabilidade pelo recebimento das leituras dos sensores. O bloco ControlProcessor está relacionado aos requisitos RF08 – Validação de leituras e RF09 – Atualização do estado, sendo responsável pelo processamento das leituras, pela identificação de valores inválidos ou ausentes e pela atualização do estado do sistema. O bloco AlarmController satisfaz o RF05 – Acionamento do alarme, relacionado à entrada no modo de emergência e ao acionamento dos sinais de alarme. Por sua vez, o bloco ConfigurationMemory está relacionado aos requisitos RF03 – Configuração de limites e RF06 – Registro de emergência, representando o armazenamento dos limites configurados e do último evento de emergência.

A relação verify foi utilizada para representar a associação entre os requisitos e os casos de teste responsáveis por verificar seu atendimento. O TC01 – Temperatura e fumaça dentro dos limites, o TC02 – Temperatura acima do limite de alerta e o TC03 – Fumaça acima do limite crítico estão associados ao RF05 – Acionamento do alarme, permitindo verificar o comportamento do sistema diante de diferentes condições ambientais. O TC04 – Leitura de sensor ausente está relacionado ao RNF01 – Confiabilidade das leituras, verificando que uma leitura ausente não provoque indevidamente uma condição de emergência. Por fim, o TC05 – Comando de reset após emergência verifica o RF07 – Reinicialização, avaliando a possibilidade de reinicialização manual do sistema após uma situação de emergência.

A relação deriveReqt foi utilizada para representar requisitos derivados a partir de outros requisitos. O RNF02 – Tempo de resposta é derivado dos requisitos RF01 – Leitura de temperatura e RF02 – Leitura de fumaça, uma vez que a realização de leituras periódicas implica a necessidade de que o processamento dessas informações e a atualização do estado ocorram dentro do período de amostragem definido. O RNF03 – Configurabilidade é derivado do RF03 – Configuração de limites, estabelecendo que os limites utilizados na classificação das condições ambientais devem poder ser configurados. Já o RNF01 – Confiabilidade das leituras é derivado do RF08 – Validação de leituras, relacionando a validação de valores inválidos ou ausentes à necessidade de evitar que essas leituras provoquem uma condição de emergência indevida. Dessa forma, o diagrama estabelece a rastreabilidade entre os requisitos, os componentes responsáveis por atendê-los e os testes utilizados para verificar seu comportamento.

