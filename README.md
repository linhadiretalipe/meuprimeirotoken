# DIOToken - Contrato de Token ERC20 com SafeMath

## Visão Geral

O contrato `DIOToken` é uma implementação do padrão ERC20 com a biblioteca SafeMath para evitar erros comuns de matemática, como estouros (overflows) e subtrações inválidas (underflows). Este contrato oferece funcionalidades básicas de ERC20, como transferências de tokens, aprovação para transferências de terceiros e gerenciamento de permissões. Além disso, ele suporta um mecanismo de "aprovação e chamada", permitindo que contratos externos interajam com o token por meio de uma função de callback após a aprovação. O contrato também possui um mecanismo de segurança para reverter transações em caso de erros.

## Funcionalidades

- **Padrão ERC20**: Implementa os métodos padrão para interação com tokens (verificação de saldo, transferência e aprovação).
- **SafeMath**: Protege contra estouros e subtrações inválidas em operações aritméticas.
- **Aprovação e Chamada**: Permite que contratos aprovem e chamem outro contrato em uma única transação.
- **Failsafe**: Um mecanismo para reverter transações em caso de problemas inesperados.
- **Fallback**: Impede o contrato de aceitar ether.

## Informações do Token

- **Nome do Token**: DIO Test Coin
- **Sigla do Token**: DTC
- **Valor Inicial (Supply Inicial)**: 500.000 DTC
- **Decimais**: 2

## Componentes

### 1. **Contrato SafeMath**
O contrato `SafeMath` fornece quatro funções para operações matemáticas seguras:
- `safeAdd`: Adiciona dois números de forma segura, garantindo que não ocorra estouro.
- `safeSub`: Subtrai dois números de forma segura, garantindo que não ocorra underflow.
- `safeMul`: Multiplica dois números de forma segura, verificando possíveis estouros.
- `safeDiv`: Divide dois números de forma segura, garantindo que não haja divisão por zero.

```solidity
contract SafeMath {
    function safeAdd(uint a, uint b) public pure returns (uint c);
    function safeSub(uint a, uint b) public pure returns (uint c);
    function safeMul(uint a, uint b) public pure returns (uint c);
    function safeDiv(uint a, uint b) public pure returns (uint c);
}
