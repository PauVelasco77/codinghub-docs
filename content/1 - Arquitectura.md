## ⚙️ **Arquitectura del Proyecto**

> Ver también: [[2 - Modelo de negocio|Modelo de Negocio]] | [[4 - Tokenomics]] | [[Framework de diseño/3 - Conexión Negocio - Token]]

## 🌟 **Opción Estratégica: Integración con Forem**

> 💡 **Nueva Propuesta**: Utilizar [Forem](https://github.com/forem/forem) como base para acelerar el desarrollo de CodeHub

**Ventajas de usar Forem:**
- ✅ **Base probada**: El mismo código que potencia dev.to (22.3k stars, 713 contributors)
- ✅ **Funcionalidades listas**: Sistema de posts, comentarios, usuarios, moderation
- ✅ **Comunidad activa**: Mantenido por Forem con actualizaciones constantes
- ✅ **Licencia AGPL-3.0**: Compatible con proyecto open source
- ✅ **Stack Ruby on Rails**: Maduro y escalable para comunidades grandes

**Integración propuesta:**
- **Frontend Base**: Forem UI + extensiones Web3 (wallet connection, DAO interface)
- **Backend Base**: Forem API + microservicios blockchain (indexing, reward calculation)
- **Smart Contracts**: Capa adicional para tokenomics y gobernanza DAO

> 🔧 **Implementación híbrida**: [[#Arquitectura Híbrida Forem + Web3]]

---

## 🏗️ **Arquitectura Híbrida Forem + Web3**

#### 1. **Capa Base: Forem (Ruby on Rails)**

**Funcionalidades nativas de Forem:**
- Sistema de usuarios y perfiles
- Publicación y gestión de artículos
- Comentarios y reacciones
- Sistema de tags y búsqueda
- Moderation tools
- API RESTful completa

**Extensiones Web3 agregadas:**
- Plugin de conexión de wallet (MetaMask, WalletConnect)
- Dashboard de tokens CODE y recompensas
- Interface de votación DAO
- Visualización de reputación on-chain

#### 2. **Smart Contracts (Solidity + Viem)**

- Token ERC-20 (`CODE`) con extensión `ERC20Votes` para gobernanza.
    
- Contrato `Governor` de OpenZeppelin con `TimelockController` para control seguro.
    
- Contratos para emisión de Badges NFT (Soulbound tokens) para reconocer logros.

**Funciones clave de la DAO:**

- `propose(description, targets, values, calldatas)`
    
- `vote(proposalId, support)`
    
- `execute(proposalId)`

**Otras funciones y lógica de tokenomics:**

- `publishPost(ipfsHash, metadata)`  
    Registra un nuevo post y emite un evento para cálculo de recompensa.
    
- `calculatePostReward(address author, uint256 visits) returns (uint256 reward)`
    
    ```solidity
    uint256 base = 10 * 10**decimals();  // 10 CODE base
    uint256 variable = 2 * 10**decimals() * log2(visits + 1);
    if (variable > 90 * 10**decimals()) {
      variable = 90 * 10**decimals();
    }
    uint256 total = base + variable;
    if (total > 100 * 10**decimals()) {
      total = 100 * 10**decimals();
    }
    return total;
    ```
    > 💡 Para más detalles sobre esta fórmula, consulta [[4 - Tokenomics#Cálculo de Recompensas]]
    
- `applyClaimCommission(uint256 amount) returns (uint256 netAmount)`  
    Aplica una comisión del 2% y transfiere esa parte al `DAO Treasury`.
    > 💰 Ver [[3 - Monetización]] para entender el modelo de comisiones
    
- `awardTokens(address user, uint256 visits)`
    
    ```solidity
    uint256 reward = calculatePostReward(user, visits);
    uint256 net = applyClaimCommission(reward);
    _mint(user, net);
    _mint(daoTreasury, reward - net);
    ```
    
- `likePost(postId)`  
    Permite a usuarios dar "like" y dispara lógica de reputación.
    
- `submitChallengeSolution(challengeId, solutionData)`  
    Envía solución a reto para revisión y posible premio.
    
- `mintBadgeNFT(address user, uint256 badgeId)`  
    Emite badges NFT no transferibles que reconocen logros.
    
- `stakeTokens(uint256 amount)` / `unstakeTokens(uint256 amount)`  
    Permiten bloquear CODE para reputación, gobernanza y mejores condiciones de recompensa.

#### 3. **Microservicios Web3 (Node.js + Express)**

- **Blockchain Indexer**: Escucha eventos de contratos y sincroniza con Forem DB
    
- **Reward Calculator**: Calcula recompensas basadas en métricas de Forem
    
- **DAO Bridge**: Conecta propuestas de Forem con smart contracts de gobernanza
    
- **Wallet Service**: Gestiona autenticación Web3 y firma de transacciones

#### 4. **Base de Datos Híbrida**

- **Forem PostgreSQL**: Datos tradicionales (posts, users, comments)
- **Web3 Events Table**: Cache de eventos blockchain para performance
- **Rewards Queue**: Cola de recompensas pendientes de distribución

#### 5. **Almacenamiento descentralizado**

- IPFS / Arweave para respaldo de posts importantes y propuestas de gobernanza.
    
- Metadatos JSON con conteo de visitas y métricas de engagement.

---

## 🔄 **Flujo de Integración Forem + Blockchain**

### Publicación de Post
1. **Usuario publica en Forem** (UI nativa)
2. **Post se guarda en PostgreSQL** (Forem normal)
3. **Microservicio detecta post** (webhook o polling)
4. **Se llama `publishPost()`** en smart contract
5. **Evento blockchain emitido** para tracking de recompensas

### Reclamación de Recompensas
1. **Usuario ve recompensas pendientes** (dashboard Web3)
2. **Click en "Claim Rewards"** (UI extendida)
3. **Microservicio valida métricas** (anti-bot, visitas reales)
4. **Se llama `awardTokens()`** si validación exitosa
5. **Tokens transferidos a wallet** del usuario

### Votación DAO
1. **Propuesta creada en Forem** (post especial)
2. **Se sincroniza con smart contract** (`propose()`)
3. **Usuarios votan desde Forem** (UI extendida)
4. **Votos se registran on-chain** (`vote()`)
5. **Ejecución automática** si propuesta aprobada

---

## 🛠️ **Stack Técnico Actualizado**

| Capa | Tecnologías |
|------|-------------|
| **Base Platform** | Forem (Ruby on Rails) + PostgreSQL |
| **Frontend Extensions** | React components para Web3 + Tailwind CSS |
| **Smart Contracts** | Solidity + Hardhat + OpenZeppelin |
| **Web3 Services** | Node.js microservices + Express |
| **Blockchain** | Polygon, Arbitrum (L2s) |
| **Storage** | PostgreSQL (main) + IPFS (backup) |
| **Wallet Integration** | Wagmi + Viem + MetaMask |

---

## 🧪 **Funciones clave**

|Función|Descripción|
|---|---|
|`publishPost()`|Publicar un post guardando su hash en blockchain.|
|`calculatePostReward()`|Calcula la recompensa según visitas, con tope.|
|`applyClaimCommission()`|Aplica 2% de comisión al reclamar tokens.|
|`awardTokens()`|Recompensar usuarios según tokenomics y comisiones.|
|`submitChallengeSolution()`|Enviar solución a reto para revisión y posible premio.|
|`mintBadgeNFT()`|Emitir badges NFT no transferibles que reconocen logros.|
|`stakeTokens()`|Bloquear CODE para reputación y gobernanza.|

---

## 🔐 Opciones adicionales

- **Soulbound Tokens:** para badges y reputación no transferible.
    
- **Sistema de Karma:** bonificaciones y premios por participación continuada.
    
- **DAO:** gobernanza descentralizada para definir reglas, retos y mejoras.
    
- **Contenido premium:** accesible solo para holders de cierto número de tokens.

---

## 🎓 Enfoque académico para la memoria

- Justificación del uso de Forem como base técnica → Análisis de alternativas
    
- Justificación social y tecnológica del proyecto → [[Framework de diseño/1 - Modelo de Negocio y propuesta de valor]]
    
- Diseño de la integración blockchain + plataforma tradicional
    
- Diseño del tokenomics y estructura de recompensas → [[4 - Tokenomics]]
    
- Elección del stack tecnológico híbrido.
    
- Análisis de escalabilidad y costos (gas, uso de L2).
    
- Aspectos legales sobre propiedad intelectual y economía tokenizada.
    
- Métricas relevantes: número de posts, usuarios activos, tokens en circulación.
    
- Futuras mejoras: privacidad, interoperabilidad, gamificación avanzada.

---

## 📊 Documentos Relacionados

- [[2 - Modelo de negocio]] - Concepto y roles del sistema
- [[3 - Monetización]] - Streams de ingresos y comisiones
- [[4 - Tokenomics]] - Economía del token CODE
- [[5 - Whitepaper]] - Documento técnico completo
- [[Framework de diseño/2 - Value proposition canvas]] - Canvas de propuesta de valor
- [[index]] - Página principal del proyecto