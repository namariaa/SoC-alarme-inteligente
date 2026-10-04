# Caso de teste 03: Detecção de condição de emergência e acionamento do alarme

O principal objetivo é validar o comportamento do sistema diante de uma condição crítica, representada por uma leitura de fumaça acima do limite crítico. O teste verifica se o sistema reconhece a situação de emergência, realiza a transição para o estado Emergency e aciona simultaneamente os mecanismos de alarme sonoro e visual. Esse cenário corresponde ao TC03 definido no documento do projeto.

### Pré-condições

- SoC para Alarme Inteligente configurado e inicializado.
- Sensor de fumaça disponível e funcionando corretamente.
- Sensor de temperatura disponível e funcionando corretamente.
- Limites de alerta e emergência configurados.
- Limite crítico de fumaça configurado.
- Sistema inicialmente no estado Normal.
- Leitura do sensor de fumaça disponível e válida.
- Alarme sonoro desativado.
- Sinal visual desativado.

### Dados de teste

| Parâmetro              | Valor                      |
| :--------------------- | :------------------------- |
| Temperatura medida     | Acima do limite crítico|
| Fumaça medida          | Dentro do limite |
| Estado inicial         | Normal                     |
| Leitura de temperatura | Válida                     |
| Leitura de fumaça      | Válida                     |
| Alarme sonoro          | Desativado                 |
| Sinal visual           | Desativado                 |

### Passo a Passo para a realização do teste

1. Inicializar o sistema.
2. Garantir que o sistema esteja no estado Normal.
3. Configurar os limites de alerta e emergência.
4. Realizar a leitura do sensor de fumaça.
5. Realizar a leitura do sensor de temperatura.
6. Validar as leituras recebidas.
7. Verificar que a leitura de fumaça é válida.
8. Comparar o valor de fumaça com o limite de alerta.
9. Comparar o valor de fumaça com o limite crítico.
10. Verificar que o valor de fumaça ultrapassou o limite crítico.
11. Atualizar o estado do sistema.
12. Verificar a transição do estado Normal para Emergency.
13. Acionar o mecanismo de alarme sonoro.
14. Acionar o sinal visual.
15. Verificar se os dois mecanismos permanecem ativos enquanto a condição de emergência estiver presente.

### Resultado esperado

O sistema deve identificar que a leitura de fumaça ultrapassou o limite crítico.
Como consequência, o sistema deve entrar no estado Emergency e acionar os mecanismos de alerta previstos para essa condição.
O alarme sonoro e o sinal visual devem ser ativados.
O resultado esperado é:

```text
Fumaça: acima do limite crítico
Leitura: válida
Estado inicial: Normal
Estado final: Emergency
Alarme sonoro: ativado
Sinal visual: ativado
```

### Critério de aprovação

O teste será considerado **Aprovado** caso:

- a leitura de fumaça seja recebida corretamente;
- a leitura seja considerada válida;
- o valor seja identificado como superior ao limite crítico;
- o sistema entre no estado Emergency;
- o alarme sonoro seja ativado;
- o sinal visual seja ativado;
- os mecanismos de alarme permaneçam ativos enquanto a condição de emergência estiver presente.

### Critério de reprovação

O teste será considerado **Reprovado** caso:

- a leitura de fumaça acima do limite crítico não seja detectada;
- o sistema permaneça no estado Normal;
- o sistema entre apenas no estado Alert;
- o sistema entre em Emergency, mas não acione o alarme sonoro;
- o sistema entre em Emergency, mas não acione o sinal visual;
- apenas um dos mecanismos de alarme seja ativado;
- a leitura válida seja considerada inválida;
- o sistema não atualize o estado após detectar a condição crítica.
