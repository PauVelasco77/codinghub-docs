# Whitepaper CodeHub

> 📚 **Documentación Completa**: [[index]] | [[1 - Arquitectura]] | [[2 - Modelo de negocio]] | [[4 - Tokenomics]] | [[3 - Monetización]]

## 1. Introducción

CodeHub es una plataforma descentralizada gobernada por su comunidad de desarrolladores. Utiliza [Forem](https://github.com/forem/forem) (la base tecnológica de dev.to) como fundación y agrega una capa de tokenización y gobernanza DAO mediante el uso del token `CodeToken (CODE)`, para incentivar la participación, colaboración y toma de decisiones democráticas.

> 🎯 **Propuesta de valor**: [[Framework de diseño/1 - Modelo de Negocio y propuesta de valor]]

## 2. Estrategia Tecnológica: Forem + Web3

### Justificación para usar Forem

CodeHub adopta una estrategia híbrida aprovechando Forem como base tecnológica por las siguientes razones:

**Ventajas técnicas:**
- ✅ **Madurez demostrada**: Potencia dev.to con millones de usuarios activos
- ✅ **Funcionalidades completas**: Sistema de posts, usuarios, moderation, APIs
- ✅ **Comunidad activa**: 22.3k stars, 713 contributors, mantenimiento constante
- ✅ **Escalabilidad probada**: Ruby on Rails + PostgreSQL para cargas altas
- ✅ **Licencia compatible**: AGPL-3.0 permite modificación y extensión

**Ventajas de desarrollo:**
- ⚡ **Reducción tiempo**: 60-80% menos desarrollo vs plataforma desde cero
- 🔧 **APIs listas**: RESTful API completa para integración Web3
- 🎨 **UI/UX probada**: Interfaz familiar para desarrolladores
- 🛡️ **Seguridad**: Años de hardening y patches de seguridad

### Arquitectura híbrida propuesta

```
┌─────────────────┐    ┌──────────────────┐    ┌─────────────────┐
│   Forem Base    │    │  Web3 Services   │    │ Smart Contracts │
│  (Ruby/Rails)   │◄──►│   (Node.js)      │◄──►│   (Solidity)    │
│                 │    │                  │    │                 │
│ • Posts/Users   │    │ • Reward Calc    │    │ • CODE Token    │
│ • Comments      │    │ • DAO Bridge     │    │ • Governance    │
│ • Moderation    │    │ • Blockchain     │    │ • NFT Badges    │
│ • Analytics     │    │   Indexer        │    │ • Treasury      │
└─────────────────┘    └──────────────────┘    └─────────────────┘
```

> 🔧 **Detalles técnicos**: [[1 - Arquitectura#Arquitectura Híbrida Forem + Web3]]

## 3. Problema y Solución

### Problema

- Las plataformas centralizadas limitan el control comunitario.
    
- Incentivos poco transparentes para creadores y colaboradores.
    
- Reputación no verificable ni descentralizada.
    

### Solución

- **Base sólida**: Forem proporciona funcionalidades probadas de comunidad
    
- **Extensión Web3**: Blockchain para asegurar propiedad, transparencia y trazabilidad.
    
- Token `CODE` como medio de recompensa, acceso y voto.
    
- DAO para definir el rumbo de la plataforma, sus reglas y recursos.

> 💡 **Análisis detallado**: [[Framework de diseño/2 - Value proposition canvas]] | [[2 - Modelo de negocio]]
    

## 4. Token `CodeToken (CODE)`

### Propósito

- Incentivar publicaciones, retos y contribuciones valiosas.
    
- Desbloquear funciones premium dentro del ecosistema.
    
- Participar activamente en gobernanza DAO.
    
- Reforzar la reputación y el reconocimiento on-chain.

> 🔧 **Implementación técnica**: [[1 - Arquitectura#Smart Contracts]]
    

### Especificaciones

- Tipo: ERC-20 con `ERC20Votes`
    
- Nombre: CodeToken
    
- Símbolo: CODE
    
- Decimales: 18
    
- Supply Inicial: 1,000,000 CODE
    

## 5. Distribución de Tokens

|**Categoría**|**Cantidad**|**% del Total**|**Notas**|
|---|---|---|---|
|Incentivos y Recompensas|300,000 CODE|30%|Para creadores y usuarios|
|DAO Treasury|250,000 CODE|25%|Fondos para decisiones vía gobernanza|
|Equipo y Fundadores|200,000 CODE|20%|Vesting controlado on-chain|
|Marketing y Airdrops|100,000 CODE|10%|Difusión inicial y campañas|
|Liquidity Pool|100,000 CODE|10%|CODE/USDC en DEXs|
|Reserva Estratégica|50,000 CODE|5%|Fondos para alianzas o emergencias|

> 📊 **Detalles completos**: [[4 - Tokenomics#Tokenomics Propuesta]]

### Vesting

|   |   |
|---|---|
|**Período**|**Desbloqueo**|
|Cliff|6 meses|
|Mes 6|25%|
|Mes 24|100%|

Implementado vía `VestingWallet` y multisig de la DAO.

## 6. Gobernanza DAO

### Mecanismo

- Gobernanza mediante `ERC20Votes`, `Governor` y `TimelockController`.
    
- Cada CODE = 1 voto.
    
- Snapshot y ejecución segura.
    

**Parámetros sugeridos:**

|   |   |
|---|---|
|**Parámetro**|**Valor**|
|Quorum|4% del supply (40,000 CODE)|
|Propuesta mínima|10,000 CODE|
|Delay de propuesta|1 día|
|Período de votación|3 días|
|Delay de ejecución|1 día tras aprobación|

> 🏛️ **Modelo de gobernanza**: [[4 - Tokenomics#Gobernanza DAO]] | [[2 - Modelo de negocio#Roles del Sistema]]

### Ámbitos de decisión

- Emisión de tokens o distribución especial.
    
- Modificaciones económicas (fees, comisiones).
    
- Subvenciones y fondos para desarrollos.
    
- Validación de cambios estratégicos (nuevas funciones, integraciones).
    

## 7. Economía del Token

### Control de Oferta

- Fijo en 1,000,000 CODE, modificable solo por la DAO.
    

### Demanda

- Pago por funcionalidades premium.
    
- Participación en gobernanza.
    
- Recompensas on-chain por contribuciones.
    

### Liquidez

- Pool CODE/USDC inicial.
    
- Precio sugerido: 1 CODE = 1 USDC.

> 💰 **Monetización**: [[3 - Monetización]] | [[Framework de diseño/3 - Conexión Negocio - Token]]
    

## 8. Flujo de Usuario

### Creadores / Colaboradores

1. Conectan wallet.
    
2. Publican contenido en Forem (experiencia familiar).
    
3. Reciben tokens automáticamente si son validados.
    
4. Usan tokens para reputación, staking y votaciones.
    

### Lectores / Usuarios

1. Interactúan como en dev.to: comentando, votando o resolviendo retos.
    
2. Ganan tokens CODE por participación activa.
    
3. Acceden a contenido exclusivo o funciones DAO.

> 🔄 **Flujo detallado**: [[2 - Modelo de negocio#Flujo del Sistema]]
    

## 9. Reputación Descentralizada

- Cada cuenta tiene un perfil visible con logros y contribuciones.
    
- SBTs (Soulbound Tokens) opcionales como distintivos de mérito.
    
- Parte de la información on-chain, visualizada en frontend de Forem.
    

## 10. Cálculo de Recompensas

Para alinear las recompensas con el valor real generado por cada publicación y garantizar la sostenibilidad de la economía de tokens CODE, se propone el siguiente esquema:

1. **Recompensa base fija tras validación**  
    Cada post validado otorga un mínimo garantizado de **10 CODE**.
    
2. **Componente variable por visitas**
    
    - Se añaden **2 CODE × log₂(visitas + 1)** al cálculo.
        
    - Visitas calculadas por analytics nativo de Forem.
        
    - Máximo adicional por post: **90 CODE**.
        
3. **Tope máximo de recompensa**  
    La recompensa total por publicación no podrá exceder los **100 CODE**.
    
4. **Comisión de reclamación**  
    Al reclamar tokens, se aplica una tasa del **2 %** que se destina al **DAO Treasury** para financiar mejoras, grants y liquidez.

> 🔧 **Implementación técnica**: [[1 - Arquitectura#calculatePostReward]] | [[4 - Tokenomics#Cálculo de Recompensas]]
    

## 11. ¿Por qué Forem + Web3 y no desarrollar desde cero?

| Aspecto | Desarrollo desde cero | Forem + Web3 (CodeHub) |
|---------|----------------------|-------------------------|
| **Tiempo desarrollo** | 18-24 meses | 6-8 meses |
| **Riesgo técnico** | Alto | Bajo |
| **Funcionalidades base** | A desarrollar | Ya probadas |
| **Escalabilidad** | Incierta | Demostrada (dev.to) |
| **Comunidad** | A construir | Aprovecha ecosistema Forem |
| **Mantenimiento** | Full responsibility | Shared con comunidad Forem |

### Ventajas competitivas vs dev.to

| Aspecto | dev.to (Forem puro) | CodeHub (Forem + Web3) |
|---------|---------------------|-------------------------|
| **Control** | Centralizado | DAO descentralizada |
| **Incentivos** | No monetarios | Tokens CODE transparentes |
| **Reputación** | Interna/limitada | SBTs verificables on-chain |
| **Decisiones** | Equipo dev.to | Votación comunitaria |
| **Monetización** | Publicidad/sponsors | Tokenomics + comisiones |

---

## 📊 Documentos Relacionados

- [[1 - Arquitectura]] - Implementación técnica completa
- [[2 - Modelo de negocio]] - Concepto y flujo del sistema
- [[3 - Monetización]] - Streams de ingresos y sostenibilidad
- [[4 - Tokenomics]] - Economía detallada del token
- [[Framework de diseño/|Framework de diseño]] - Marco conceptual y análisis
- [[index]] - Página principal del proyecto