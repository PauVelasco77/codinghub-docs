## 🧩 **Modelo Propuesto: CodeHub — Plataforma Tokenizada para Developers**

> 🔗 **Relacionado**: [[1 - Arquitectura]] | [[4 - Tokenomics]] | [[Framework de diseño/1 - Modelo de Negocio y propuesta de valor]]

### 🔑 Concepto Clave:

- Plataforma tipo dev.to con posts, artículos y retos para developers.
    
- Usuarios ganan **tokens por contribuir**: publicar posts, resolver retos, comentar, etc.
    
- Tokens se usan para acceder a funciones premium, votar en decisiones ([[Framework de diseño/3 - Conexión Negocio - Token|DAO]]) y desbloquear recompensas.
    
- Todo registro de contribuciones y recompensas queda **on-chain**, auditado y gobernado por la comunidad DAO.

---

## 👥 Roles del Sistema

|**Rol**|**Función**|
|---|---|
|Developer / Usuario|Publica posts, participa en retos y gana tokens.|
|Moderador / Admin|Modera contenido, valida retos y administra el sistema.|
|DAO (comunidad)|Aprueba propuestas, define reglas, distribuye incentivos y gestiona el treasury.|

> 💡 Ver detalles técnicos en [[1 - Arquitectura#Smart Contracts]]

---

## ⚙️ ¿Qué se tokeniza?

|   |   |   |
|---|---|---|
|**Elemento**|**Tipo de Token**|**Función**|
|Contribuciones|ERC-20 `CodeToken`|Recompensas por acciones dentro de la plataforma.|
|Reputación|Soulbound Token (SBT)|Reconocimiento no transferible vinculado al historial de participación.|
|Retos y logros|NFTs|Badges únicos por hitos y completitud de desafíos.|

> 🔍 **Profundizar**: [[4 - Tokenomics]] | [[Framework de diseño/2 - Value proposition canvas]]

---

## 🔄 Flujo del Sistema (DAO-Driven)

|   |   |
|---|---|
|**Paso**|**Descripción**|
|1. Creación de contenido o solución de retos|El usuario publica o responde un reto.|
|2. Validación y recompensa|Moderadores o la DAO validan la contribución, calculan la recompensa según el modelo de [[4 - Tokenomics|tokenomics]] y emiten `CodeToken` tras la aprobación on-chain.|
|3. Uso de Tokens|- Acceso a funciones premium.|

- Participación en propuestas y votaciones.
    
- Compra de badges u otros beneficios NFT. | | 4. Gobernanza | Holders presentan propuestas (nuevos retos, cambios de reglas, ajustes económicos). La comunidad vota y ejecuta decisiones mediante `Governor` + `Timelock`. | | 5. Reputación | La actividad validada por la DAO se refleja en SBTs que muestran la trayectoria de cada usuario. |

> ⚙️ **Implementación técnica**: [[1 - Arquitectura#Funciones clave de la DAO]]

---

## 🛠️ Ejemplo Simplificado de Smart Contract

```
struct Post {
  address author;
  string contentURI;
  uint256 timestamp;
  bool validated;
}

struct Challenge {
  uint256 id;
  string description;
  uint256 reward;
  bool completed;
  address completer;
}
```

---

## 🧠 Tokenomics

- Oferta inicial fija de **1,000,000 CODE**, modificable solo por votación en la DAO.
    
- Emisión controlada por contrato `Governor` + `ERC20Votes`.
    
- DAO gestiona treasury, recompensas y ajustes de parámetros.
    
- Staking para mejorar visibilidad y condiciones de recompensas.

> 📊 **Detalles completos**: [[4 - Tokenomics]] | [[3 - Monetización]]

---

## Propuesta de implementación (Tokenomics)

Para alinear las recompensas con el valor real generado por cada publicación y garantizar la sostenibilidad de la economía de tokens CODE, se propone el siguiente esquema:

1. **Recompensa base fija tras validación**  
    Cada post validado otorga un mínimo garantizado de **10 CODE**.
    
2. **Componente variable por visitas**
    
    - Se añaden **2 CODE** × log₂(visitas + 1) al cálculo.
        
    - Visitas filtradas contra bots y validadas off-chain.
        
    - Máximo adicional por post: **90 CODE**.
        
3. **Tope máximo de recompensa**  
    La recompensa total por publicación no podrá exceder los **100 CODE**.
    
4. **Comisión de reclamación**  
    Al reclamar tokens, se aplica una tasa del **2 %** que se destina al treasury de la DAO para financiar mejoras, grants y liquidez.

> 🔧 **Implementación**: [[1 - Arquitectura#calculatePostReward]] | [[3 - Monetización#Comisiones]]

---

## 💡 Diferenciadores Clave

- Comunidad como centro de decisiones: DAO define reglas, recompensas y evolución del producto.
    
- Reputación transparente y verificable mediante SBTs.
    
- Incentivos justos mediante gobernanza tokenizada.
    
- Integración con identidades Web3 (ENS, Lens, Gitcoin Passport).    
    - A través de SBTs y actividad validada por la DAO.

> 🎯 **Análisis detallado**: [[Framework de diseño/1 - Modelo de Negocio y propuesta de valor]]

---

## 📊 Documentos Relacionados

- [[1 - Arquitectura]] - Implementación técnica del sistema
- [[3 - Monetización]] - Streams de ingresos y modelo económico  
- [[4 - Tokenomics]] - Economía y distribución del token CODE
- [[5 - Whitepaper]] - Documento técnico completo
- [[Framework de diseño/|Framework de diseño]] - Marco conceptual y propuesta de valor
- [[index]] - Página principal del proyecto