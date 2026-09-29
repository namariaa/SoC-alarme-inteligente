# Documento de Visão

## Histórico de Revisões

|    Data    | Versão | Descrição                            | Autores           |
| :--------: | :----: | :----------------------------------- | :---------------- |
| 28/09/2026 |  1.0   | Versão inicial do documento de visão | Ana Maria e Lívia |

---

## 1. Objetivo do projeto

O projeto tem como objetivo especificar e arquitetar um **System-on-Chip (SoC) para monitoramento ambiental e alarme inteligente**, utilizando **SysML** para a modelagem do sistema em alto nível e **AADL** para a descrição de sua arquitetura embarcada.

O sistema será destinado ao monitoramento de ambientes que necessitam de acompanhamento de condições ambientais, como salas técnicas, laboratórios, mini-datacenters ou ambientes industriais.

O SoC deverá receber leituras de **temperatura** e **fumaça**, processar essas informações de acordo com limites configuráveis e identificar condições normais, de alerta ou de emergência. Quando uma condição crítica for identificada, o sistema deverá acionar mecanismos de alarme e registrar o evento.

O projeto terá como foco a **especificação, modelagem e arquitetura do sistema**, não sendo necessária a implementação física do SoC, síntese, prototipação em FPGA ou medição real de desempenho.

---

## 2. Descrição do problema

|              |                                                                                                                                                                                                                      |
| ------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Problema** | A necessidade de monitorar continuamente condições ambientais, como temperatura e presença de fumaça, e identificar situações anormais de forma estruturada e automática.                                            |
| **Afeta**    | Ambientes que necessitam de monitoramento ambiental, como salas técnicas, laboratórios, mini-datacenters e ambientes industriais.                                                                                    |
| **Impacta**  | A capacidade de identificar condições de alerta ou emergência e acionar os mecanismos de sinalização apropriados.                                                                                                    |
| **Solução**  | Especificação e arquitetura de um SoC capaz de receber dados de sensores ambientais, validar as leituras, compará-las com limites configuráveis, atualizar seu modo de operação e acionar alarmes quando necessário. |

---

## 3. Descrição dos usuários

| Nome                              | Descrição                                                                                                                               | Responsabilidade                                                                                       |
| :-------------------------------- | :-------------------------------------------------------------------------------------------------------------------------------------- | :----------------------------------------------------------------------------------------------------- |
| **Operador**                      | Pessoa responsável por acompanhar o funcionamento do sistema e realizar operações de configuração ou reinicialização quando necessário. | Configurar limites, acompanhar o estado do sistema e realizar o reset após uma situação de emergência. |
| **Sensor de temperatura**         | Componente responsável por fornecer ao sistema as leituras periódicas de temperatura do ambiente monitorado.                            | Fornecer leituras de temperatura ao sistema.                                                           |
| **Sensor de fumaça**              | Componente responsável por fornecer informações relacionadas à presença de fumaça no ambiente.                                          | Fornecer leituras de fumaça ao sistema.                                                                |
| **Sistema externo de supervisão** | Sistema externo que pode receber informações referentes ao estado ou aos eventos identificados pelo SoC.                                | Receber informações e sinais relacionados ao funcionamento e às condições de alarme do sistema.        |

---

## 4. Descrição do ambiente dos usuários

O sistema será destinado a ambientes que necessitem de **monitoramento contínuo de condições ambientais**, podendo ser aplicado, por exemplo, em laboratórios, salas técnicas, mini-datacenters ou ambientes industriais.

O SoC será considerado um sistema embarcado composto por sensores, unidade de processamento, memória de configuração, temporização, atuadores e uma interface de comunicação externa.

O sistema deverá operar de forma contínua, recebendo leituras periódicas dos sensores e atualizando seu estado de acordo com os valores observados.

A interação do operador ocorrerá principalmente em situações de configuração e recuperação do sistema, enquanto os sensores fornecerão dados automaticamente durante a operação normal.

O projeto não considera restrições relacionadas à implementação física ou a uma plataforma de hardware específica, uma vez que o objetivo é a **modelagem e especificação da arquitetura do sistema**.

---

## 5. Principais necessidades dos usuários

### 1º — Monitoramento ambiental

**Causas:**

A necessidade de identificar alterações nas condições ambientais do local monitorado, principalmente relacionadas à temperatura e à presença de fumaça.

**Solução:**

O sistema realizará leituras periódicas dos sensores de temperatura e fumaça e processará os valores recebidos.

**Necessidades dos usuários:**

- Monitorar continuamente as condições ambientais;
- Receber informações atualizadas dos sensores;
- Identificar valores fora dos limites configurados.

---

### 2º — Identificação de situações anormais

**Causas:**

Valores ambientais podem ultrapassar limites considerados seguros, exigindo que o sistema diferencie situações normais, de alerta e de emergência.

**Solução:**

O sistema deverá comparar as leituras recebidas com limites configuráveis e atualizar seu modo de operação de acordo com os valores identificados.

**Necessidades dos usuários:**

- Identificar situações de alerta;
- Identificar situações de emergência;
- Evitar que leituras inválidas provoquem uma emergência indevidamente.

---

### 3º — Sinalização e resposta a emergências

**Causas:**

Uma situação crítica precisa ser sinalizada para permitir que o operador ou sistemas externos tomem conhecimento do evento.

**Solução:**

Em uma situação de emergência, o SoC deverá acionar o **alarme sonoro**, o **sinal visual** e registrar o evento.

**Necessidades dos usuários:**

- Ser informado sobre situações críticas;
- Identificar que o sistema entrou em emergência;
- Consultar o registro do último evento de emergência;
- Realizar a reinicialização do sistema após uma emergência.

---

## 6. Visão geral do projeto

O **SoC para Alarme Inteligente** será responsável por monitorar as condições ambientais de um determinado local por meio de sensores de temperatura e fumaça.

As leituras serão recebidas periodicamente e passarão por uma etapa de validação antes de serem comparadas com os limites configurados.

A partir dessa comparação, o sistema poderá permanecer em **Normal**, entrar em **Alert** ou entrar em **Emergency**.

Em uma situação de emergência, o sistema deverá acionar o alarme sonoro e o sinal visual, além de registrar o evento. Após uma emergência, o operador poderá solicitar a reinicialização do sistema, levando-o ao estado de `Resetting` e, após a validação necessária, novamente ao estado `Normal`.

A especificação será representada por meio de modelos SysML, enquanto a arquitetura embarcada será refinada utilizando AADL.

O fluxo principal do sistema pode ser resumido como:

```text
Leitura dos sensores
        ↓
Validação das leituras
        ↓
Comparação com limites
        ↓
Atualização do modo
        ↓
Acionamento das saídas
```

## 7. Requisitos funcionais

| Código   | Nome                    | Descrição                                                                                     |
| :------- | :---------------------- | :-------------------------------------------------------------------------------------------- |
| **RF01** | Leitura de temperatura  | O sistema deve receber leituras periódicas de temperatura.                                    |
| **RF02** | Leitura de fumaça       | O sistema deve receber leituras periódicas de fumaça.                                         |
| **RF03** | Configuração de limites | O sistema deve permitir a configuração dos limites de temperatura e fumaça.                   |
| **RF04** | Detecção de alerta      | O sistema deve entrar em modo de alerta quando detectar um valor acima do limite de alerta.   |
| **RF05** | Detecção de emergência  | O sistema deve entrar em modo de emergência quando detectar um valor acima do limite crítico. |
| **RF06** | Acionamento do alarme   | Em emergência, o sistema deve acionar um alarme sonoro e um sinal visual.                     |
| **RF07** | Registro de emergência  | O sistema deve registrar o último evento de emergência.                                       |
| **RF08** | Reinicialização         | O sistema deve permitir a reinicialização manual após uma emergência.                         |
| **RF09** | Validação de leituras   | O sistema deve ignorar leituras inválidas ou ausentes.                                        |
| **RF10** | Atualização do estado   | O sistema deve atualizar seu estado ao menos uma vez a cada período de amostragem.            |

## 8. Requisitos não funcionais

| Código    | Nome                        | Descrição                                                                                                | Categoria      | Classificação |
| :-------- | :-------------------------- | :------------------------------------------------------------------------------------------------------- | :------------- | :------------ |
| **RNF01** | Periodicidade               | O sistema deve realizar a atualização de seu estado respeitando o período de amostragem definido.        | Desempenho     | Obrigatório   |
| **RNF02** | Confiabilidade das leituras | O sistema não deve entrar indevidamente em estado de emergência devido a leituras inválidas ou ausentes. | Confiabilidade | Obrigatório   |
| **RNF03** | Tempo de resposta           | O sistema deve processar as leituras e atualizar seu estado dentro do período de amostragem definido.    | Desempenho     | Obrigatório   |
| **RNF04** | Configurabilidade           | Os limites utilizados para classificação das condições ambientais devem poder ser configurados.          | Flexibilidade  | Desejável     |
