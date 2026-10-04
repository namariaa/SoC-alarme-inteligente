# Caso de teste 02: Detecção de condição de alerta

O principal objetivo é validar o comportamento do sistema quando uma leitura de temperatura ultrapassa o limite de alerta, mas não atinge o limite crítico de emergência. O teste verifica se o sistema identifica corretamente a condição de alerta, altera seu estado para Alert e ativa o sinal visual. Esse cenário corresponde ao TC02 definido no documento do projeto.

### Pré-condições

- SoC para Alarme Inteligente configurado e inicializado.
- Sensor de temperatura disponível e funcionando corretamente.
- Sensor de fumaça disponível e funcionando corretamente.
- Limites de alerta e emergência configurados.
- Limite de alerta de temperatura definido.
- Limite crítico de temperatura definido.
- Sistema inicialmente no estado Normal.
- Leitura do sensor de temperatura disponível e válida.
- Alarme sonoro inicialmente desativado.
- Sinal visual inicialmente desativado.

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
2. Configurar os limites de temperatura e fumaça.
3. Realizar a leitura do sensor de temperatura.
4. Realizar a leitura do sensor de fumaça.
5. Verificar se as leituras são válidas.
6. Comparar os valores obtidos com os limites configurados.
7. Atualizar o estado do sistema.
8. Verificar o estado dos mecanismos de alarme.

### Resultado esperado

O sistema deve processar as leituras sem erros e permanecer no estado **Normal**.

O alarme sonoro e o sinal visual devem permanecer desativados.

```text
Temperatura: dentro do limite
Fumaça: dentro do limite
Estado: Normal
Alarme sonoro: desativado
Sinal visual: desativado
```

### Critério de aprovação

O teste será considerado **Aprovado** caso:

- as leituras de temperatura e fumaça sejam realizadas corretamente;
- as leituras sejam consideradas válidas;
- os valores sejam identificados como estando dentro dos limites configurados;
- o sistema permaneça no estado Normal;
- o alarme sonoro permaneça desativado;
- o sinal visual permaneça desativado.

### Critério de reprovação

O teste será considerado **Reprovado** caso:

- a temperatura acima do limite de alerta não seja detectada;
- o sistema permaneça no estado Normal;
- o sistema entre diretamente no estado Emergency sem que o limite crítico tenha sido ultrapassado;
- o sinal visual permaneça desativado;
- o alarme sonoro seja acionado indevidamente;
- uma leitura válida seja considerada inválida;
- o sistema não atualize seu estado após a leitura.