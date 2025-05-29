## 🧩 **Modelo Propuesto: CodeHub — Plataforma Tokenizada para Developers**

> 🔗 **Relacionado**: [[1 - Arquitectura]] | [[4 - Tokenomics]] | [[Framework de diseño/1 - Modelo de Negocio y propuesta de valor]]

### �� Concepto Clave:

- **Base estratégica**: Utilizar [Forem](https://github.com/forem/forem) (la plataforma que potencia dev.to) como fundación
    
- **Extensión Web3**: Agregar capa de tokenización y gobernanza DAO sobre Forem
    
- Usuarios ganan **tokens por contribuir**: publicar posts, resolver retos, comentar, etc.
    
- Tokens se usan para acceder a funciones premium, votar en decisiones ([[Framework de diseño/3 - Conexión Negocio - Token|DAO]]) y desbloquear recompensas.
    
- Todo registro de contribuciones y recompensas queda **on-chain**, auditado y gobernado por la comunidad DAO.

> 💡 **Ventaja competitiva**: Combinar la madurez de Forem con innovación Web3

---

## 🏗️ **Estrategia de Desarrollo: Forem + Web3**

### ¿Por qué Forem como base?

| Ventaja | Impacto |
|---------|---------|
| **Tiempo de desarrollo** | Reducción 60-80% vs desarrollo desde cero |
| **Funcionalidades probadas** | Sistema de posts, usuarios, moderación ya maduro |
| **Comunidad establecida** | 22.3k stars, 713 contributors activos |
| **Escalabilidad demostrada** | Potencia dev.to con millones de usuarios |
| **Licencia AGPL-3.0** | Compatible con proyecto open source |

### Fases de implementación

1. **Fase 1 - Base Forem**: Desplegar instancia customizada de Forem
2. **Fase 2 - Smart Contracts**: Desarrollar tokenomics y DAO on-chain
3. **Fase 3 - Integración**: Conectar Forem con blockchain via microservicios
4. **Fase 4 - UX Web3**: Extender UI para wallet, votaciones y recompensas

> 🔧 **Detalles técnicos**: [[1 - Arquitectura#Arquitectura Híbrida Forem + Web3]]

---

## 👥 Roles del Sistema

|**Rol**|**Función en Forem**|**Función Web3**|
|---|---|---|
|Developer / Usuario|Publica posts, comenta, interactúa|Conecta wallet, reclama tokens, participa en DAO|
|Moderador / Admin|Modera contenido usando herramientas nativas|Valida contribuciones para recompensas|
|DAO (comunidad)|N/A (nuevo)|Aprueba propuestas, define reglas, gestiona treasury|

> 💡 Ver detalles técnicos en [[1 - Arquitectura#Smart Contracts]]

---

## ⚙️ ¿Qué se tokeniza?

|   |   |   |
|---|---|---|
|**Elemento**|**Tipo de Token**|**Función**|
|Contribuciones (posts, comments)|ERC-20 `CodeToken`|Recompensas por acciones dentro de Forem|
|Reputación|Soulbound Token (SBT)|Reconocimiento no transferible vinculado al historial|
|Retos y logros|NFTs|Badges únicos por hitos y completitud de desafíos|

> 🔍 **Profundizar**: [[4 - Tokenomics]] | [[Framework de diseño/2 - Value proposition canvas]]

---

## 🔄 Flujo del Sistema (Forem + DAO)

|   |   |
|---|---|
|**Paso**|**Descripción**|
|1. Creación de contenido|Usuario publica en Forem (experiencia nativa)|
|2. Detección automática|Microservicios detectan nueva actividad y registran en blockchain|
|3. Validación|Moderadores/DAO validan contribución según criterios de calidad|
|4. Recompensa|Sistema calcula tokens según [[4 - Tokenomics|tokenomics]] y los distribuye|
|5. Uso de Tokens|Acceso a funciones premium, participación en votaciones DAO|
|6. Gobernanza|Propuestas creadas en Forem se sincronizan con smart contracts|

> ⚙️ **Implementación técnica**: [[1 - Arquitectura#Flujo de Integración Forem + Blockchain]]

---

## 🛠️ Ejemplo de Integración

### Estructura de datos híbrida
```ruby
# Forem (Rails) - Datos tradicionales
class Article < ApplicationRecord
  belongs_to :user
  has_many :comments
  # Funcionalidad nativa de Forem
end

# Extensión Web3
class BlockchainReward < ApplicationRecord
  belongs_to :article
  belongs_to :user
  
  # Estado de la recompensa
  enum status: { pending: 0, validated: 1, claimed: 2 }
  
  # Datos del smart contract
  validates :transaction_hash, presence: true, if: :claimed?
end
```

### API extendida
```javascript
// Endpoint nativo de Forem
GET /api/articles/:id

// Nuevos endpoints Web3
GET /api/articles/:id/rewards
POST /api/articles/:id/claim_reward
GET /api/dao/proposals
POST /api/dao/vote
```

---

## 🧠 Tokenomics sobre Forem

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
        
    - Visitas calculadas por analytics nativo de Forem.
        
    - Máximo adicional por post: **90 CODE**.
        
3. **Tope máximo de recompensa**  
    La recompensa total por publicación no podrá exceder los **100 CODE**.
    
4. **Comisión de reclamación**  
    Al reclamar tokens, se aplica una tasa del **2 %** que se destina al treasury de la DAO para financiar mejoras, grants y liquidez.

> 🔧 **Implementación**: [[1 - Arquitectura#calculatePostReward]] | [[3 - Monetización#Comisiones]]

---

## 💡 Diferenciadores Clave vs dev.to

| Aspecto | dev.to (Forem puro) | CodeHub (Forem + Web3) |
|---------|---------------------|-------------------------|
| **Control** | Centralizado | DAO descentralizada |
| **Incentivos** | No monetarios | Tokens CODE por contribuir |
| **Reputación** | Interna | SBTs verificables on-chain |
| **Decisiones** | Equipo dev.to | Votación comunitaria |
| **Monetización** | Publicidad tradicional | Tokenomics transparente |

> 🎯 **Análisis detallado**: [[Framework de diseño/1 - Modelo de Negocio y propuesta de valor]]

---

## 📊 Documentos Relacionados

- [[1 - Arquitectura]] - Implementación técnica híbrida Forem + Web3
- [[3 - Monetización]] - Streams de ingresos y modelo económico  
- [[4 - Tokenomics]] - Economía y distribución del token CODE
- [[5 - Whitepaper]] - Documento técnico completo
- [[Framework de diseño/|Framework de diseño]] - Marco conceptual y propuesta de valor
- [[index]] - Página principal del proyecto