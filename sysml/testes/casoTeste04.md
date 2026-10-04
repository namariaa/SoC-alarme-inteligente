# Caso de teste 04: Tratamento de leitura de sensor ausente

O principal objetivo é validar o comportamento do sistema quando uma leitura de sensor não está disponível. O teste verifica se o sistema identifica a ausência da leitura como uma condição inválida, registra essa ocorrência e evita que a ausência do dado provoque indevidamente uma situação de emergência. Esse cenário corresponde ao TC04 definido no documento do projeto.

### Pré-condições

- SoC para Alarme Inteligente configurado e inicializado.
- Sistema inicializado e em funcionamento.
- Sensor de temperatura disponível e funcionando corretamente.
- Sensor de fumaça disponível e funcionando corretamente.
- Limites de alerta e emergência configurados.
- Sistema inicialmente no estado Normal.
- Um dos sensores deve estar indisponível ou não fornecer uma leitura durante o ciclo de monitoramento.
- Alarme sonoro desativado.
- Sinal visual desativado.

### Dados de teste

| Parâmetro              | Valor                      |
| :--------------------- | :------------------------- |
| Estado inicial         | Normal                     |
| Leitura de temperatura | Ausente                     |
| Leitura de fumaça      | Válida                     |
| Validade da leitura ausente | Ausente |
| Alarme sonoro          | Desativado                 |
| Sinal visual           | Desativado                 |

### Passo a Passo para a realização do teste

1. Inicializar o sistema.
2. Garantir que o sistema esteja no estado Normal.
3. Configurar os limites de alerta e emergência.
4. Iniciar um novo ciclo de monitoramento.
5. Solicitar a leitura do sensor de temperatura.
6. Simular a ausência da resposta do sensor de temperatura.
7. Realizar a leitura do sensor de fumaça.
8. Verificar que a leitura de temperatura não foi recebida.
9. Classificar a leitura de temperatura ausente como inválida.
10. Registrar a ocorrência da leitura inválida ou ausente.
11. Evitar que o valor ausente seja utilizado diretamente na comparação com os limites ambientais.
12. Processar a leitura válida do sensor de fumaça normalmente.
13. Atualizar o estado do sistema sem considerar a leitura ausente como uma condição crítica.
14. Verificar o estado final do sistema.
15. Verificar se algum mecanismo de emergência foi acionado indevidamente.

### Resultado esperado

O sistema deve identificar que a leitura de temperatura está ausente e classificá-la como inválida.
A ocorrência deve ser registrada e a leitura ausente não deve ser utilizada para gerar uma condição de emergência.
O sistema deve continuar seu funcionamento sem realizar uma transição indevida para Emergency.
O resultado esperado é:

```text
Leitura de temperatura: ausente
Validade: inválida
Leitura de fumaça: válida
Ocorrência: leitura inválida registrada
Estado: não entra em Emergency
Alarme sonoro: desativado
Sinal visual: desativado
```

### Critério de aprovação

O teste será considerado **Aprovado** caso:

- a ausência da leitura seja identificada;
- a leitura seja classificada como inválida;
- a ocorrência seja registrada;
- a leitura ausente não seja utilizada para gerar uma emergência;
- o sistema não entre indevidamente no estado Emergency;
- o alarme sonoro permaneça desativado;
- o sistema continue realizando o monitoramento.

### Critério de reprovação

O teste será considerado **Reprovado** caso:

- a ausência da leitura não seja identificada;
- a leitura ausente seja tratada como válida;
- o sistema utilize a ausência da leitura para gerar uma condição de alerta ou emergência;
- o sistema entre no estado Emergency sem uma leitura válida que justifique essa transição;
- o sistema acione o alarme sonoro indevidamente;
- o sistema acione o sinal visual de emergência indevidamente;
- a ocorrência da leitura inválida não seja registrada;
- o sistema interrompa permanentemente o monitoramento após a ausência da leitura.