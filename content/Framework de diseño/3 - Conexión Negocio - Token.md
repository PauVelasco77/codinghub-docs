#### 0. Sanity Check

-  **Gobernanza on-chain**  
    Permite votaciones y decisiones descentralizadas (1 token = 1 voto).
    
-  **Alineación de incentivos**  
    Conecta directamente recompensas y crecimiento de la plataforma con creadores, moderadores y usuarios.
    
-  **Mejora de la experiencia**  
    Habilita funciones exclusivas (dashboards avanzados, acceso beta, reputación staking, Soulbound Tokens).
    
-  **Solución a puntos críticos**  
    Automatiza pagos mínimos garantizados, financia el treasury DAO y distribuye recompensas según engagement.
    
-  **Nuevas fuentes de ingresos**  
    Genera comisiones (reclamación/intercambio), venta directa de tokens, suscripciones, grants, patrocinios y gamificación (NFT, hackatones).

---

#### 1. Identificación del Contexto: "Principal-Agent"

- **Principal**  
    El “Principal” es la entidad que diseña y posee la plataforma CodeHub: sus fundadores y, de forma más amplia, la DAO gobernada por la comunidad, que define las reglas, administra el treasury y controla la emisión de `CODE` 5 - Whitepaper.
    
- **Agents**
    
    1. **Developers / Usuarios:** creadores de contenido (posts, retos) y lectores que comentan, votan y resuelven desafíos.
        
    2. **Moderadores / Admins:** validan y moderan aportes, garantizando calidad y disparan la recompensa on-chain.
        
    3. **Holders / Inversores:** adquieren y retienen `CODE` para acceder a funciones premium, participar en votaciones y operar staking.
        
    4. **Socios / Colaboradores externos:** organizadores de hackatones, sponsors o integradores que aportan eventos y contenidos.
        
- **Comportamientos y resultados clave**
    
    - **Crear y compartir valor:** publicar posts de calidad y proponer soluciones a retos para generar engagement y atraer nuevos usuarios 2 - Modelo de negocio.
        
    - **Validación y moderación:** moderadores activos que revisen y aprueben contribuciones, manteniendo un estándar óptimo de contenido y disparando las emisiones de `CODE` correspondientes 1 - Arquitectura.
        
    - **Participación en gobernanza:** votar y proponer cambios en la DAO (parámetros de tokenomics, uso del treasury, nuevos features), asegurando que la plataforma evolucione alineada a las necesidades reales de la comunidad 5 - Whitepaper.
        
    - **Economía y monetización:** reclamar tokens (`CODE`), realizar staking para reputación y comprar suscripciones o tokens directos, generando flujos de ingreso y alimentando el treasury DAO mediante comisiones del 2 % 4 - Tokenomics.
        
    - **Difusión y crecimiento:** participar en eventos, hackatones y programas de grants, extendiendo la red de usuarios y socios, e incrementando la demanda de `CODE` para funciones premium y reconocimientos on-chain.

---

#### 2. Propósito del Token

##### ¿Qué rol jugará el token?

- **Rol global del token (`CODE`):** Token de utilidad que vertebra todo el ecosistema, sirviendo simultáneamente como medio de intercambio interno, instrumento de gobernanza y métrica de reputación .
    
- **Incentivo:** Sí. Se recompensa a creadores, moderadores y usuarios por acciones concretas —publicar o validar posts y retos, comentar, dar “likes” o resolver desafíos— con asignaciones automáticas on-chain según el modelo de tokenomics (recompensa base + componente variable por visitas) .
    
- **Gobernanza:** Sí. Cada `CODE` equivale a un voto en la DAO (implementada con `ERC20Votes` y `Governor + TimelockController`), permitiendo proponer cambios, definir comisiones y gestionar el treasury de forma descentralizada .
    
- **Acceso:** Sí. Poseer y/o stakear `CODE` desbloquea funciones premium: dashboards avanzados, acceso beta a nuevas features, visibilidad reforzada, suscripciones exclusivas y Soulbound Tokens de reputación .
    
- **Moneda interna:** Sí. `CODE` se utiliza para pagar suscripciones (en token o fiat), adquirir badges/NFTs, abonar comisiones del 2 % al reclamar recompensas y realizar intercambios internos, facilitando todas las transacciones dentro de la plataforma .

##### ¿Qué problema específico del negocio soluciona el token?

>El token `CODE` aborda de manera directa las carencias clave de nuestro modelo de negocio:

- **Falta de transparencia y control comunitario:** sustituye los esquemas opacos de las plataformas centralizadas al registrar todas las contribuciones, recompensas y votaciones on-chain, devolviendo el poder de decisión a los usuarios mediante la DAO .
    
- **Incentivos poco alineados:** garantiza recompensas justas y automáticas por creación de contenido, moderación e interacción —con un mínimo fijo y un componente variable según el engagement— eliminando la incertidumbre y el sesgo humano en la distribución de incentivos .
    
- **Reputación no verificable:** implementa Soulbound Tokens (SBTs) y staking reputacional para que el historial y el prestigio de cada contribución queden inmutables y fácilmente auditables on-chain .
    
- **Dificultad para monetizar contribuciones de forma justa:** habilita comisiones del 2 % en reclamaciones y ventas directas de tokens, creando flujos de ingresos claros—suscripciones, fees por intercambio y grants comunitarios—que financian el treasury de la DAO y aseguran la sostenibilidad económica de la plataforma .

##### ¿Cómo el token mejora la experiencia del usuario?

- **Recompensas inmediatas y automáticas**  
    Cada contribución valiosa (posts, retos, comentarios) se traduce al instante en tokens `CODE`, sin trámites manuales ni demoras, lo que motiva la participación continua y ofrece feedback inmediato sobre el valor aportado .
    
- **Acceso anticipado y dashboards avanzados**  
    Al poseer o stakear `CODE`, los usuarios desbloquean CodeHub Pro, que incluye analytics en tiempo real de visitas, “likes” y tokens ganados, así como acceso beta a nuevas funcionalidades antes que el resto de la comunidad .
    
- **Visibilidad reforzada y reconocimiento on-chain**  
    Los holders de `CODE` disfrutan de mayor protagonismo en el feed (posts destacados) y pueden ganar badges NFT y Soulbound Tokens que quedan grabados en su perfil, consolidando su reputación de forma transparente y permanente .
    
- **Staking reputacional**  
    Bloquear `CODE` incrementa el peso de voto en la DAO y mejora las condiciones de recompensa (p. ej., límites más altos en el cálculo de tokens), reforzando el estatus de los usuarios más comprometidos .
    
- **Participación activa en gobernanza**  
    Cada token `CODE` equivale a un voto en decisiones clave (nuevas features, parámetros de tokenomics, uso del treasury), permitiendo a los usuarios influir directamente en la evolución de la plataforma y sentirse parte de la comunidad .

---

#### 3. Diseño de la Distribución de Valor

##### ¿Qué beneficios obtiene cada actor al usar el token?

- **Usuarios**
    
    - **Recompensas inmediatas y automáticas:** cada contribución (posts, retos, comentarios, “likes”) genera al instante `CODE`, eliminando demoras y trámites manuales .
        
    - **Reputación on-chain verificable:** Soulbound Tokens y badges NFT inmortalizan tu histórico de aportes, reforzando tu prestigio frente a la comunidad .
        
    - **Voz en la gobernanza:** 1 `CODE` = 1 voto en la DAO; participa en decisiones clave sobre tokenomics, features y uso del treasury .
        
    - **Acceso a features premium:** dashboards avanzados, acceso beta, visibilidad destacada en el feed y descuentos al pagar servicios con `CODE` .
        
- **Negocio**
    
    - **Ingresos recurrentes y escalables:**
        
        - **Comisión del 2 %** en cada reclamo o intercambio de tokens, que va al treasury para grants y mejoras continuas .
            
        - **Suscripciones premium** (mensual/trimestral/anual), pagables en `CODE` o fiat, que garantizan ingresos predecibles y engagement sostenido .
            
        - **Venta directa de tokens** (1 `CODE` = 5 USDC) para acceso inmediato a funciones avanzadas .
            
    - **Retención y ciclo virtuoso:** al alinear recompensas on-chain con la creación de valor real, se incentiva la participación continua, reduciendo churn y aumentando la adopción orgánica .
        
- **Colaboradores / Partners**
    
    - **Grants comunitarios y patrocinios:** la DAO destina fondos del treasury a propuestas de desarrollo (artículos, plugins, workshops), con criterios transparentes definidos por votación .
        
    - **Eventos y hackatones patrocinados:** organizadores reciben visibilidad en la plataforma, co-branding en banners y pueden ofrecer premios en `CODE` y SBT “Ganador”, incentivando su participación y la de la comunidad .
        
    - **Pools de liquidez y marketing:** socios pueden aportar liquidez (CODE/USDC) a cambio de fees de transacción y campañas de airdrop, beneficiándose de la tracción de la plataforma .

##### ¿Qué porcentaje del valor total capturado queda para cada grupo?

- **Usuarios (Incentivos y Recompensas): 30 %**  
    Destinado directamente a creadores de contenido, moderadores y usuarios activos como recompensas on-chain .
    
- **Negocio (DAO Treasury + Equipo & Fundadores): 45 %**
    
    - Treasury DAO: 25 % para grants, mejoras de producto y financiamiento de desarrollos mediante gobernanza comunitaria
        
    - Equipo y Fundadores: 20 % con vesting on-chain para alinear incentivos a largo plazo .
        
- **Colaboradores / Partners (Airdrop & Marketing + Liquidez + Reserva Estratégica): 25 %**
    
    - Airdrop/Marketing: 10 % para campañas de difusión y captación de nuevos usuarios
        
    - Liquidity Pool (DEX): 10 % emparejados con USDC/ETH para asegurar liquidez
        
    - Reserva Estratégica: 5 % para alianzas o emergencias aprobadas por la DAO .

---
#### 4. Estructura de Uso del Token

##### ¿Cómo y dónde se usa el token?

- **Acceso a productos y servicios premium**  
    Los usuarios emplean `CODE` para suscribirse a **CodeHub Pro**, desbloqueando dashboards avanzados, acceso beta a nuevas funcionalidades, visibilidad reforzada en el feed y descuentos en servicios on-chain . Además, pueden usarlo para comprar badges/NFTs exclusivos y participar en eventos con premios.
    
- **Transacciones internas entre usuarios**  
    `CODE` funciona como moneda interna para pagar comisiones de servicios (p. ej., fees de reclamo e intercambio), transferir valor entre creadores y consumidores de contenido, y operar pools de liquidez en DEXs (CODE/USDC) gestionados por la DAO .
    
- **Recompensas y liquidaciones on-chain**  
    Cada contribución validada (posts, retos, moderación, interacciones) desencadena la emisión automática de tokens, que los usuarios pueden reclamar y luego gastar o reinvertir sin procesos manuales, gracias al smart contract de reclamación con comisión del 2 % .
    
- **Gobernanza descentralizada**  
    `CODE` otorga **1 voto por token** en la DAO, permitiendo a los holders proponer y decidir sobre parámetros de tokenomics, uso del treasury, desarrollo de nuevas features y cualquier cambio estratégico de la plataforma mediante el módulo `Governor + TimelockController` .

##### ¿Existen límites o restricciones en su uso?

- **Supply fijo y emisión controlada:** el máximo total de `CODE` está limitado a **1 000 000** y cualquier aumento de supply requiere aprobación de la DAO vía `Governor` .
    
- **Tope de recompensa por publicación:** cada post validado puede generar como máximo **100 CODE** (10 base + hasta 90 variables) para evitar inflación excesiva .
    
- **Comisión de reclamación:** al reclamar cualquier recompensa se aplica una tasa del **2 %**, que va al treasury de la DAO; esto desalienta reclamaciones fraccionadas continuas y financia mejoras .
    
- **Vesting para equipo y fundadores:** los tokens asignados al equipo están sujetos a un cliff de **6 meses** (0 % desbloqueado) y vesting lineal hasta completar **100 % en 24 meses**, garantizando compromiso a largo plazo .
    
- **Parámetros de gobernanza:**
    
    - **Quorum mínimo:** 4 % del supply (40 000 CODE)
        
    - **Propuesta mínima:** 10 000 CODE bloqueados por el proponente
        
    - **Delay de propuesta:** 1 día antes de iniciar la votación
        
    - **Período de votación:** 3 días
        
    - **Delay de ejecución:** 1 día tras la aprobación
        
    
    Estos umbrales evitan spam de propuestas y aseguran que solo los holders comprometidos lancen y voten iniciativas .
    
- **Lock-up de staking:** aunque los usuarios pueden stakear y unstakear `CODE`, el peso de voto y las condiciones preferentes de recompensa se calculan según el saldo bloqueado en cada snapshot, fomentando staking sostenido antes de las votaciones .
    
- **Restricciones de acceso a features:** algunas funcionalidades premium (CodeHub Pro, acceso beta, dashboards avanzados) requieren un **mínimo de tokens stakeados**, definido dinámicamente por la DAO, asegurando que solo usuarios con aportes reales disfruten de privilegios exclusivos .

##### ¿Cómo puedes fomentar su demanda dentro del ecosistema?

- **Crear sinks de utilidad claros:** exige `CODE` para acceder a funciones premium (dashboards avanzados, acceso beta, visibilidad reforzada) y para comprar badges/NFTs exclusivos, de modo que quienes quieran estas ventajas deban adquirir y mantener tokens .
	
- **Staking con recompensas progresivas:** ofrece mejoras de reputación y multiplica ligeramente las recompensas on-chain cuanto más tiempo y más tokens stakee un usuario, incentivando el lock-up y reduciendo la oferta circulante .
    
- **Mecanismos de quema (“burn”):** aplica una pequeña quema (p.ej. 0,5 %) sobre ciertos fees de transacción o compra de NFTs, creando presión deflacionaria que aumente el valor percibido del token .
    
- **Programas de liquidity mining y rewards temporales:** lanza campañas de “yield farming” o recompensas extra en `CODE` para proveedores de liquidez en pools CODE/USDC, atrayendo capital y usuarios interesados en farming .
    
- **Partnerships y grants comunitarios:** destina parte del treasury a grants para proyectos que integren o extiendan CodeHub, pagados en `CODE`, generando casos de uso externos y visibilidad del token .
    
- **Gamificación y eventos especiales:** organiza hackatones, retos y competiciones donde la inscripción y los premios sean en `CODE`, fomentando la adquisición de tokens para participar y aumentando el engagement .
    
- **Buy-back y treasury management:** utiliza parte de los ingresos de comisiones (2 %) para recomprar `CODE` en el mercado y destinarlo a quema o a grants, demostrando compromiso con el valor del token .
    
- **Marketing focalizado y airdrops condicionados:** realiza drops selectivos de `CODE` a usuarios que completen hitos (p.ej. 50 interacciones valiosas) o a nuevos usuarios que se registren con un referido, creando impulso inicial de circulación .
