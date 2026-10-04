# Caso de teste 05: Reinicialização após uma emergência

O principal objetivo é validar a capacidade do sistema de realizar uma reinicialização manual após uma condição de emergência. O teste verifica a transição do sistema para o estado Resetting após o comando de reinicialização e seu posterior retorno ao estado Normal após a validação das condições necessárias. Esse cenário corresponde ao TC05 definido no documento do projeto, que especifica a transição para Resetting e, após a validação, para Normal.

### Pré-condições

- SoC para Alarme Inteligente configurado e inicializado.
- Sistema em funcionamento.
- Sensores disponíveis e funcionando corretamente.
- Limites de alerta e emergência configurados.
- Sistema previamente colocado no estado Emergency.
- Condição que provocou a emergência não está mais presente.
- Alarme sonoro inicialmente ativado devido à condição de emergência.
- Sinal visual inicialmente ativado devido à condição de emergência.
- Comando manual de reinicialização disponível.

### Dados de teste

| Parâmetro              | Valor                      |
| :--------------------- | :------------------------- |
| Condição crítica     | Resolvida |
| Comando de reset        | Acionado manualmente |
| Estado intermediário esperado     |  Resetting    |
| Estado inicial | Emergency |
| Estado final esperado | Normal                     |
| Alarme sonoro inicial     | Ativado                     |
| Sinal visual inicial       | Ativado                 |

### Passo a Passo para a realização do teste

1. Inicializar o sistema.
2. Colocar o sistema em uma condição de Emergency, conforme o cenário de emergência.
3. Verificar que o sistema está no estado Emergency.
4. Verificar que o alarme sonoro está ativo.
5. Verificar que o sinal visual está ativo.
6. Remover ou considerar resolvida a condição que provocou a emergência.
7. Verificar as leituras atuais dos sensores.
8. Confirmar que não existe uma nova condição que exija a permanência no estado Emergency.
9. Enviar manualmente o comando de reinicialização.
10. Verificar a transição do sistema para o estado Resetting.
11. Durante o estado Resetting, validar novamente as condições ambientais.
12. Verificar se as leituras dos sensores são válidas.
13. Verificar se os valores estão dentro das condições necessárias para retorno à operação normal.
14. Após a validação, verificar a transição de Resetting para Normal.
15. Verificar o estado do alarme sonoro.
16. Verificar o estado do sinal visual.
17. Iniciar um novo ciclo de monitoramento para verificar que o sistema voltou à operação normal.

### Resultado esperado

Após a ocorrência de uma emergência, o comando manual de reset deve fazer com que o sistema entre no estado Resetting.
Durante esse estado, o sistema deve validar novamente as condições ambientais. Caso as leituras sejam válidas e não exista mais uma condição de emergência, o sistema deve retornar ao estado Normal.
Após o retorno ao estado normal, os mecanismos de alarme relacionados à emergência anterior devem deixar de estar ativos.
O resultado esperado é:

```text
Estado inicial: Emergency
Comando de reset:
    ↓
Estado: Resetting

Validação das condições:
    ↓
Condições normais
    ↓
Estado: Normal

Alarme sonoro: desativado
Sinal visual: desativado
```
O sistema deve então retomar normalmente o ciclo de monitoramento.

### Critério de aprovação

O teste será considerado **Aprovado** caso:

- o sistema esteja inicialmente no estado Emergency;
- o comando manual de reset seja reconhecido;
- o sistema entre no estado Resetting;
- as condições ambientais sejam novamente verificadas;
- as leituras sejam consideradas válidas;
- a ausência de uma condição crítica seja confirmada;
- o sistema realize a transição de Resetting para Normal;
- o alarme sonoro seja desativado;
- o sinal visual seja desativado;
- o sistema retome o ciclo normal de monitoramento.

### Critério de reprovação

O teste será considerado **Reprovado** caso:

- o comando de reset não seja reconhecido;
- o sistema não entre no estado Resetting;
- o sistema retorne diretamente para Normal sem realizar a validação;
- o sistema retorne para Normal enquanto ainda existir uma condição crítica;
- o sistema permaneça indefinidamente em Resetting mesmo após condições normais serem confirmadas;
- o sistema retorne para Normal, mas mantenha o alarme sonoro indevidamente ativado;
- o sistema retorne para Normal, mas mantenha o sinal visual de emergência ativado;
- o sistema entre novamente em Emergency sem que uma condição crítica esteja presente.