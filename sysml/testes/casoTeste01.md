# Caso de teste 01: Monitoramento em condições normais

O principal objetivo é validar o funcionamento do sistema em uma situação normal, verificando se as leituras de temperatura e fumaça permanecem dentro dos limites configurados e se o sistema mantém o estado **Normal** sem acionar os mecanismos de alarme.

### Pré-condições

- SoC para Alarme Inteligente configurado e inicializado.
- Sensor de temperatura disponível e funcionando corretamente.
- Sensor de fumaça disponível e funcionando corretamente.
- Limites de alerta e emergência configurados.
- Leituras dos sensores disponíveis e válidas.
- Sistema inicialmente no estado **Normal**.

### Dados de teste

| Parâmetro          | Valor                      |
| :----------------- | :------------------------- |
| Temperatura medida | Dentro do limite de alerta |
| Fumaça medida      | Dentro do limite de alerta |
| Estado inicial     | Normal                     |
| Alarme sonoro      | Desativado                 |
| Sinal visual       | Desativado                 |

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

### Resultado obtido

**Aprovado.**
