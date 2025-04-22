# DispersionContract

## Descripción
El `DispersionContract` es un contrato inteligente desarrollado en Solidity que permite la dispersión controlada de CELO (la criptomoneda nativa de la red Celo) a direcciones específicas, con autorización de gobernanza.

## Características Principales

- **Control de Gobernanza**: Solo las direcciones autorizadas pueden realizar operaciones críticas.
- **Dispersión Fija**: Permite enviar una cantidad predefinida de CELO a direcciones específicas.
- **Seguridad**: Implementa `ReentrancyGuard` para prevenir ataques de reentrada.
- **Flexibilidad**: Permite actualizar las direcciones de gobernanza y dispersión, así como la cantidad fija a dispersar.

## Funcionalidades

1. **Dispersión de CELO**
   - Envía una cantidad fija de CELO a una dirección específica
   - Solo puede ser ejecutado por la dirección de dispersión autorizada

2. **Gestión de Gobernanza**
   - Transferencia del rol de gobernanza a nuevas direcciones
   - Actualización de la dirección de dispersión
   - Actualización de la cantidad fija de CELO a dispersar
   - Retiro de CELO del contrato

3. **Eventos**
   - `CeloDispersed`: Registra cuando se dispersa CELO
   - `GovernanceUpdated`: Registra cambios en la dirección de gobernanza
   - `DispersionUpdated`: Registra cambios en la dirección de dispersión
   - `FixedAmountUpdated`: Registra cambios en la cantidad fija
   - `CeloWithdrawn`: Registra retiros de CELO

## Requisitos

- Solidity ^0.8.20
- OpenZeppelin Contracts (para ReentrancyGuard)

## Uso

1. **Inicialización**
   ```solidity
   constructor(
       address _governance,
       address _dispersion,
       uint256 _fixedAmount
   )
   ```

2. **Dispersión de CELO**
   ```solidity
   function disperseCelo(address _recipient)
   ```

3. **Gestión de Gobernanza**
   ```solidity
   function transferGovernance(address _newGovernance)
   function updateDispersion(address _newDispersion)
   function updateFixedAmount(uint256 _newFixedAmount)
   function withdrawCelo()
   ```

## Seguridad

- Todas las funciones críticas están protegidas por modificadores de acceso
- Implementa protección contra reentrada
- Validaciones de direcciones y cantidades
- Verificaciones de balance antes de transferencias

## Eventos

El contrato emite eventos para todas las operaciones importantes, permitiendo un seguimiento transparente de las transacciones en la blockchain.
