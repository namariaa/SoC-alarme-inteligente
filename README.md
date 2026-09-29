# SoC para Alarme Inteligente

Projeto desenvolvido para a disciplina de **projeto de sistemas em chip**, com foco na aplicação do **SysML** edo  **AADL** na modelagem e especificação de um sistema embarcado.

## Nosso tema
Nosso projeto consiste na modelagem de um **SoC de monitoramento ambiental e alarme inteligente**, destinado a ambientes como salas técnicas, laboratórios, mini-datacenters ou ambientes industriais.
O sistema recebe leituras de **temperatura** e **fumaça**, processa essas informações de acordo com limites configuráveis e, ao identificar condições anormais, aciona um **alarme local** e uma **interface de comunicação**.

O sistema possui três modos principais de operação:
- **Normal**
- **Alerta**
- **Emergência**

A modelagem considera elementos como sensores, unidade de processamento, memória de configuração, temporização, atuadores e comunicação externa.

## Objetivo

Especificar e arquitetar um SoC capaz de:

- Monitorar temperatura e fumaça;
- Validar as leituras dos sensores;
- Comparar os valores com limites configuráveis;
- Identificar condições de alerta e emergência;
- Acionar alarmes sonoros e visuais;
- Registrar eventos de emergência;
- Permitir a reinicialização do sistema após uma emergência.

O trabalho será desenvolvido por meio de **modelos SysML e AADL**, sem necessidade de implementação física do SoC.

---

## 👥 Equipe

<table>
  <tr>
    <td align="center">
      <a href="https://github.com/SEU-USUARIO">
        <img src="https://github.com/SEU-USUARIO.png" width="100px;" alt="Ana Maria"/><br/>
        <strong>Ana Maria</strong>
      </a>
    </td>
    <td align="center">
      <a href="https://github.com/USUARIO-LIVIA">
        <img src="https://github.com/USUARIO-LIVIA.png" width="100px;" alt="Lívia"/><br/>
        <strong>Lívia</strong>
      </a>
    </td>
  </tr>
</table>

---

## Ferramentas

<table>
  <tr>
    <td align="center">
      <a href="https://astah.net/" target="_blank">
        <img
          src="https://github.com/user-attachments/assets/0df28e6c-27d6-4583-ad23-ae71f53f72b4"
          alt="Astah Logo"
          width="80"
        /><br/>
        <strong>Astah SysML</strong>
      </a>
    </td>
    <td align="center">
      <a href="https://aadl.info/" target="_blank">
        <img
          src="https://github.com/user-attachments/assets/dcc8eddf-bea6-4ba6-adb7-e9b8003d617a"
          alt="AADL Logo"
          width="80"
        /><br/>
        <strong>AADL</strong>
      </a>
    </td>
  </tr>
</table>

---

## Artefatos

### SysML

Os artefatos de especificação e modelagem SysML estão organizados na pasta [`sysml/`](./sysml/).

| Artefato | Arquivo |
|---|---|
| Requisitos | [`requisitos.md`](./sysml/requisitos.md) |
| Casos de uso | [`casos-de-uso.md`](./sysml/casos-de-uso.md) |
| BDD | [`bdd.md`](./sysml/bdd.md) |
| IBD | [`ibd.md`](./sysml/ibd.md) |
| Diagrama de atividade | [`atividade.md`](./sysml/atividade.md) |
| Máquina de estados | [`maquina-de-estados.md`](./sysml/maquina-de-estados.md) |

### AADL

O modelo arquitetural AADL está disponível na pasta [`aadl/`](./aadl/).

| Artefato | Arquivo |
|---|---|
| Modelo AADL | [`modelo.aadl`](./aadl/modelo.aadl) |

### Testes

Os casos de teste estão organizados individualmente na pasta [`sysml/testes/`](./sysml/testes/).

| Teste | Arquivo |
|---|---|
| TC01 | [`TC01.md`](./sysml/testes/TC01.md) |
| TC02 | [`TC02.md`](./sysml/testes/TC02.md) |
| TC03 | [`TC03.md`](./sysml/testes/TC03.md) |
| TC04 | [`TC04.md`](./sysml/testes/TC04.md) |
| TC05 | [`TC05.md`](./sysml/testes/TC05.md) |
