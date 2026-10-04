# Caso de teste 01: Monitoramento em condições normais

O principal objetivo é validar o funcionamento do sistema em uma situação normal, verificando se as leituras de temperatura e fumaça permanecem dentro dos limites configurados e se o sistema mantém o estado Normal, sem acionar os mecanismos de alarme. Esse cenário corresponde ao TC01 definido para o projeto, cujo resultado esperado é a permanência no estado Normal com os alarmes desligados.

### Pré-condições

- SoC para Alarme Inteligente configurado e inicializado.
- Sensor de temperatura disponível e funcionando corretamente.
- Sensor de fumaça disponível e funcionando corretamente.
- Limites de alerta e emergência configurados.
- Leituras dos sensores disponíveis e válidas.
- Sistema inicialmente no estado Normal.
- Alarme sonoro desativado.
- Sinal visual desativado.

### Dados de teste

| Parâmetro              | Valor                      |
| :--------------------- | :------------------------- |
| Temperatura medida     | Dentro do limite de alerta |
| Fumaça medida          | Dentro do limite de alerta |
| Estado inicial         | Normal                     |
| Leitura de temperatura | Válida                     |
| Leitura de fumaça      | Válida                     |
| Alarme sonoro          | Desativado                 |
| Sinal visual           | Desativado                 |

### Passo a Passo para a realização do teste

1. Inicializar o sistema.
2. Garantir que o sistema esteja no estado **Normal**.
3. Configurar os limites de alerta e emergência para temperatura e fumaça.
4. Realizar a leitura do sensor de temperatura.
5. Realizar a leitura do sensor de fumaça.
6. Verificar se as leituras foram recebidas corretamente.
7. Validar as leituras obtidas pelos sensores.
8. Comparar o valor de temperatura com os limites configurados.
9. Comparar o valor de fumaça com os limites configurados.
10. Verificar que nenhum dos valores ultrapassou o limite de alerta.
11. Atualizar o estado do sistema.
12. Verificar o estado atual do sistema.
13. Verificar o estado do alarme sonoro.
14. Verificar o estado do sinal visual.
15. Realizar um novo ciclo de leitura para verificar se o sistema continua operando normalmente.

### Resultado esperado

O sistema deve receber e processar corretamente as leituras de temperatura e fumaça.

As duas leituras devem ser consideradas válidas e seus valores devem permanecer dentro dos limites configurados. Como nenhuma condição de alerta ou emergência foi identificada, o sistema deve permanecer no estado **Normal**.

O alarme sonoro e o sinal visual devem permanecer desativados.

```text
Leitura de temperatura: válida
Leitura de fumaça: válida
Temperatura: dentro do limite
Fumaça: dentro do limite
Estado: Normal
Alarme sonoro: desativado
Sinal visual: desativado
```

### Critério de aprovação

O teste será considerado **Aprovado** caso:

- as leituras de temperatura e fumaça sejam realizadas corretamente;
- ambas as leituras sejam consideradas válidas;
- os valores permaneçam dentro dos limites configurados;
- o sistema permaneça no estado Normal;
- o alarme sonoro permaneça desativado;
- o sinal visual permaneça desativado;
- nenhum estado de alerta ou emergência seja acionado indevidamente.

### Critério de reprovação

O teste será considerado **Reprovado** caso:

- uma leitura válida não ser recebida pelo sistema;
- uma leitura válida ser considerada inválida;
- o sistema classificar incorretamente uma leitura dentro dos limites como alerta;
- o sistema entrar indevidamente no estado Alert;
- o sistema entrar indevidamente no estado Emergency;
- o alarme sonoro ser acionado sem que exista uma condição de emergência;
- o sinal visual ser acionado indevidamente;
- o sistema deixar de atualizar seu estado durante o ciclo de monitoramento.
