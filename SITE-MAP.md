# AZ Consultoría — Site Map & Edit Reference

> Reference doc for `index.html` so any change request can target an exact element by code (e.g. `H1-HEADLINE`, `CN3-SUB`, `FT-EMAIL`). Line numbers reflect the current `index.html`. **Update this file alongside the HTML when the structure changes.**

---

## How to request a change

Say something like one of:

- **Replace** `H1-HEADLINE` with `"X"`
- **Edit** `LB5-ITEM2-TITLE` → `"Y"`
- **Replace WhatsApp number** with `+56 9 0000 0000` (global — affects all 13 occurrences listed below)
- **Remove** `DG3-ITEM5` (the Compras Internacionales card)
- **Add a new card** to `H2` (servicios grid) → I'll use the pattern in *Component templates* below

The code prefix tells me which section. The suffix tells me which element. I'll edit the exact lines.

---

## Repeated content map — change once, replace everywhere

When Mario asks to change any of these, the change has to be applied in **every** location below. Listed by code so I can grep and replace in one pass.

### `WHATSAPP-NUMBER` — `+56 9 7994 7557` / `56979947557`

| # | Where | Line | Format used |
|---|---|---|---|
| 1 | Header nav phone link (href) | 1300 | `wa.me/56979947557` |
| 2 | Header nav phone link (text) | 1302 | `+56 9 7994 7557` |
| 3 | Header mobile menu | 1318 | `wa.me/56979947557` |
| 4 | WhatsApp floating button | 1328 | `wa.me/56979947557` |
| 5 | Home contact detail | 1605 | `+56 9 7994 7557` |
| 6 | Home contact WhatsApp btn | 1624 | `wa.me/56979947557` |
| 7 | Contable hero CTA | 1704 | `wa.me/56979947557` |
| 8 | Contable final CTA | 1840 | `wa.me/56979947557` |
| 9 | Digital hero CTA | 1872 | `wa.me/56979947557` |
| 10 | Digital final CTA | 1992 | `wa.me/56979947557` |
| 11 | Laboral hero CTA | 2025 | `wa.me/56979947557` |
| 12 | Laboral plan-1 CTA | 2160 | `wa.me/56979947557` |
| 13 | Laboral plan-2 CTA | 2179 | `wa.me/56979947557` |
| 14 | Laboral final CTA | 2196 | `wa.me/56979947557` |
| 15 | Footer contact | 2263 | `+56 9 7994 7557` |

### `EMAIL` — `azetas365@gmail.com`

| # | Where | Line |
|---|---|---|
| 1 | Home contact detail | 1612 |
| 2 | Footer contact | 2267 |

### `DOMAIN` — `azetas365.com`

| # | Where | Line |
|---|---|---|
| 1 | Header logo subtext | 1285 |
| 2 | Hero label | 1345 |
| 3 | Footer logo subtext | 2224 |
| 4 | Footer copyright | 2280 |

### `BRAND-NAME` — `AZ Consultoría`

| # | Where | Line |
|---|---|---|
| 1 | Page `<title>` | 6 |
| 2 | Header logo text | 1284 |
| 3 | Footer logo text | 2223 |
| 4 | Footer copyright | 2280 |

### `LOCATION` — `Valparaíso & Zona`

| # | Where | Line |
|---|---|---|
| 1 | Hero label suffix | 1345 |
| 2 | Home contact detail | 1619 |
| 3 | Footer contact | 2271 (`Valparaíso & Zona, Chile`) |

---

## Brand tokens — single source of truth at `:root` (updated 2026-05-13)

Después del refactor de tokens, **todo cambio de color o fuente se hace en una sola línea del `:root`**. Las referencias en el resto del CSS usan `var(--token)`.

### Marca oficial (AZ Consultoría brand kit)

| Token | Hex | Origen | Rol |
|---|---|---|---|
| `--azul` | `#09699F` | Brand kit — "Medium Persian Blue" | Color primario. Hero backgrounds, footer, headings sobre fondo claro. |
| `--cyan` | `#2393D1` | Brand kit — "Cyan Cornflower Blue" | Acento. Links sobre fondo oscuro, highlight spans, iconos de servicio. |
| `--texto` | `#3C3C3B` | Brand kit — "Black Olive" | Texto principal del cuerpo sobre fondo claro. |

### Off-brand tokens (TBD con Mario 15/05 — ver MA-reunion-01-resumen.md §Off-brand colors)

Estos colores **no existen en la marca oficial** pero el sitio los usa funcionalmente. Mario los aprobó como interinos hasta la reunión.

| Token | Hex | Rol | Ocurrencias |
|---|---|---|---|
| `--naranja` | `#F5831F` | CTA principal (todo botón "primary") | ~25 lugares |
| `--naranja-h` | `#e07015` | Hover del naranja | 2 lugares |
| `--naranja-d` | `#d06010` | Variante oscura para gradientes | 2 lugares |
| `--verde` | `#2ED6A0` | Acento del servicio Derecho Laboral | 7 lugares |
| `--verde-d` | `#1aab7e` | Hover/variante oscura del verde | 1 lugar |
| `--azul-mid` | `#1A4A8A` | Mid-blue para gradientes Digital/Laboral | 2 lugares |

### Hex codes hardcodeados (no tokenizados — funcionales o muy específicos)

| Color | Hex | Dónde | Por qué no se tokenizó |
|---|---|---|---|
| Cyan oscuro | `#1a8cb8` | Avatar Mario Pérez gradient (L761) | Único uso, derivado del cyan |
| Laboral hero gradient pair | `#0d3d7a` | `.laboral-hero` (L1111) | Único uso, gradient del azul |
| Error section bg | `#fff5f0` | `.error-section` (L1114) | Background "advertencia" — único uso |
| WhatsApp green | `#25D366` | Floating button + mobile menu (L340, L1319) | **Color oficial de WhatsApp** — excepción estándar global |

### Typography

| Token | Familia | Pesos cargados | Rol |
|---|---|---|---|
| `--font-heading` | `'Poppins', sans-serif` | 300, 400, 500, 600, 700, 800, **900 (Black)** | Headings — la marca oficial usa Poppins Black |
| `--font-body` | `'Poppins', sans-serif` | (mismas weights) + italic 400 | Cuerpo de texto |

- Carga única en L10: Google Fonts CSS2 API.
- Default body font: `<body>` rule L38-43 usa `var(--font-body)`. Headings `h1-h5` usan `var(--font-heading)` (rule L44).
- **Icons:** Font Awesome 6.5.1 (CDN), carga en L11.

**Cómo cambiar la tipografía:** una sola línea en `:root` (L31 o L32). Si quiere cambiar todo el sitio a Inter, edita `--font-heading: 'Inter', sans-serif;` y listo, 17 elementos se actualizan automáticamente.

### Other tokens (L27-30)

| Token | Value | Role |
|---|---|---|
| `--sombra` | `0 4px 24px rgba(11,43,92,0.10)` | Standard card shadow |
| `--sombra-lg` | `0 12px 48px rgba(11,43,92,0.16)` | Hover / elevated card shadow |
| `--radio` | `12px` | Default border radius |
| `--trans` | `0.3s cubic-bezier(.4,0,.2,1)` | Standard transition curve |

---

## Architecture

Single-file SPA. Four `<div id="page-XXX">` containers; only one visible at a time. Navigation done in JavaScript via `showPage(name)` which toggles the `.hidden` class.

- Pages: `home`, `contable`, `digital`, `laboral` — declared L2293.
- Initial page set by URL pathname (`/contable`, `/digital`, `/laboral`, else `home`) — L2392-2396.
- History API used to update visible URL without reload — L2319-2321.
- Browser back/forward handled — L2400-2406.
- Form submission is stubbed (`console.log` only, no backend) — L2343-2369. **TODO: wire to EmailJS / Formspree / backend before launch.**

---

## Shared elements

### `HD-*` — Header / Nav (L1271-1322)

| Code | Element | Line | Current content |
|---|---|---|---|
| `HD-LOGO-SVG` | Logo SVG markup | 1276-1282 | Inline AZ monogram (blue circle + cyan A + dark square Z) |
| `HD-BRAND` | Brand name text | 1284 | `AZ Consultoría` |
| `HD-DOMAIN` | Domain subtext | 1285 | `azetas365.com` |
| `HD-NAV1` | Nav link 1 | 1291 | `Inicio` |
| `HD-NAV2` | Nav link 2 | 1292 | `Contabilidad` |
| `HD-NAV3` | Nav link 3 | 1293 | `Digital & Ads` |
| `HD-NAV4` | Nav link 4 | 1294 | `Derecho Laboral` |
| `HD-NAV5` | Nav link 5 | 1295 | `Contacto` |
| `HD-PHONE` | Visible phone label | 1302 | `+56 9 7994 7557` |
| `HD-MOBILE-N1..N6` | Mobile menu items | 1313-1320 | Same labels with emoji prefix |

### `WA-FLOAT` — WhatsApp Floating Button (L1328-1331)

| Code | Element | Line | Current content |
|---|---|---|---|
| `WA-URL` | href with prefilled msg | 1328 | `wa.me/56979947557?text=Hola%2C%20me%20interesa...` |
| `WA-TITLE` | Tooltip on hover | 1329 | `Chatea por WhatsApp` |

### `FT-*` — Footer (L2209-2284)

| Code | Element | Line | Current content |
|---|---|---|---|
| `FT-LOGO-SVG` | Footer logo SVG | 2215-2221 | Same monogram, cyan + white version |
| `FT-BRAND` | Brand name | 2223 | `AZ Consultoría` |
| `FT-DOMAIN` | Domain subtext | 2224 | `azetas365.com` |
| `FT-DESC` | Brand description paragraph | 2228-2231 | `Equipo multidisciplinario de contabilidad, derecho laboral y marketing digital...` |
| `FT-COL2-TITLE` | Col 2 heading | 2236 | `Servicios` |
| `FT-COL2-L1..L4` | Col 2 links | 2238-2241 | Contabilidad / Digital / Laboral / Consulta gratuita |
| `FT-COL3-TITLE` | Col 3 heading | 2247 | `Equipo` |
| `FT-COL3-L1..L4` | Col 3 team links | 2249-2252 | FZ / MP / Jerussa / CC |
| `FT-COL4-TITLE` | Col 4 heading | 2258 | `Contacto` |
| `FT-PHONE` | Contact phone | 2263 | `+56 9 7994 7557` |
| `FT-EMAIL` | Contact email | 2267 | `azetas365@gmail.com` |
| `FT-LOCATION` | Contact location | 2271 | `Valparaíso & Zona, Chile` |
| `FT-COPYRIGHT` | Copyright line | 2280 | `© 2025 AZ Consultoría · azetas365.com · Todos los derechos reservados` |
| `FT-TAGLINE` | Right tagline | 2281 | `Hecho con ❤️ para empresas de la zona` |

---

## HOME page (L1336-1678) — `page-home`

### `H1-*` — Hero (L1339-1419)

| Code | Element | Line | Current content |
|---|---|---|---|
| `H1-LABEL` | Eyebrow / pill | 1345 | `azetas365.com · Valparaíso & Zona` |
| `H1-HEADLINE` | Main `<h1>` | 1347-1351 | `El equipo contable / que sí genera / valor real` (last line in cyan span) |
| `H1-SUB` | Subheadline `<p>` | 1353-1356 | `No somos un contador más. Somos un equipo multidisciplinario...` |
| `H1-CTA1` | Primary button | 1358-1360 | `📅 Consulta gratuita` (scrolls to contact) |
| `H1-CTA2` | Ghost button | 1361-1363 | `👥 Conocer el equipo` (scrolls to contact) |
| `H1-STAT1` | Stat number 1 | 1367-1368 | `3+` · `Especialidades en un solo equipo` |
| `H1-STAT2` | Stat number 2 | 1371-1372 | `365` · `Días al año disponibles` |
| `H1-STAT3` | Stat number 3 | 1375-1376 | `0` · `Costo de primera consulta` |
| `H1-CARD-TITLE` | Visual card eyebrow | 1384 | `Nuestros servicios` |
| `H1-PILL1` | Service pill 1 (cyan) | 1386-1393 | `Contabilidad Estratégica` · `Francisco Zamora · Diagnóstico gratis` |
| `H1-PILL2` | Service pill 2 (orange) | 1394-1401 | `Digital & Google Ads` · `Mario Pérez · Reportes semanales` |
| `H1-PILL3` | Service pill 3 (green) | 1402-1409 | `Derecho Laboral` · `Claudio Castro · Revisión gratuita` |
| `H1-BADGE` | Floating badge | 1411-1414 | `🎁 Mes gratis al incorporarte` |

### `H2-*` — Servicios cards (L1421-1482)

| Code | Element | Line | Current content |
|---|---|---|---|
| `H2-LABEL` | Eyebrow | 1425 | `Lo que hacemos` |
| `H2-HEADLINE` | Section title | 1427 | `Un equipo, tres soluciones` (last word in cyan) |
| `H2-DESC` | Section description | 1428-1431 | `Contamos con especialistas en cada área...` |
| `H2-CARD1-TITLE` | Card 1 title | 1440 | `Contabilidad Estratégica` |
| `H2-CARD1-DESC` | Card 1 body | 1441-1445 | `Deja de tener un contador que solo cumple con el SII...` |
| `H2-CARD2-TITLE` | Card 2 title | 1456 | `Digital & Google Ads` |
| `H2-CARD2-DESC` | Card 2 body | 1457-1460 | `Más consultas, más llamadas, más clientes...` |
| `H2-CARD3-TITLE` | Card 3 title | 1471 | `Derecho Laboral` |
| `H2-CARD3-DESC` | Card 3 body | 1472-1475 | `Protege tu empresa antes de que sea tarde...` |

### `H3-*` — Por qué nosotros (L1484-1548)

| Code | Element | Line | Current content |
|---|---|---|---|
| `H3-LABEL` | Eyebrow | 1489 | `¿Por qué elegirnos?` |
| `H3-HEADLINE` | Section title | 1491 | `Contables fuera de lo normal` (last 3 words in cyan) |
| `H3-DESC` | Section description | 1492-1495 | `Trabajamos con empresas de la zona...` |
| `H3-ITEM1-TITLE` | Diferencial 1 title | 1501 | `Visibilidad total de tu empresa` |
| `H3-ITEM1-DESC` | Diferencial 1 body | 1502 | `Accede a toda la información financiera...` |
| `H3-ITEM2-TITLE` | Diferencial 2 title | 1508 | `Equipo de la zona` |
| `H3-ITEM2-DESC` | Diferencial 2 body | 1509 | `Nos importa el desarrollo local...` |
| `H3-ITEM3-TITLE` | Diferencial 3 title | 1515 | `Garantía real` |
| `H3-ITEM3-DESC` | Diferencial 3 body | 1516 | `Primer mes gratis para el servicio contable...` |
| `H3-VISUAL-TITLE` | Right card heading | 1524 | `Tu empresa en números` |
| `H3-METRIC1` | Metric 1 | 1527-1528 | `30` · `días para ver resultados contables` |
| `H3-METRIC2` | Metric 2 | 1531-1532 | `15` · `días para +consultas digitales` |
| `H3-METRIC3` | Metric 3 (wide) | 1537-1538 | `Diagnóstico inmediato` · `Revisión gratuita de contratos laborales` |
| `H3-METRIC-CTA1` | CTA inside visual | 1542 | `📅 Agenda tu consulta gratuita` |
| `H3-METRIC-CTA2` | CTA subtext | 1543 | `Sin compromiso · Sin costo` |

### `H4-*` — Equipo (L1550-1600)

> **Comportamiento desde 2026-05-13:** cada card es clickeable + tiene **hover-switch**. Default visible: nombre + rol (`.team-default`). Hover: bio + CTA (`.team-detail`). Click navega: Francisco → Contable, Mario Pérez → Digital, Claudio → Laboral, Jerussa → home + scroll a contacto. CSS de la interacción: `.team-content` (grid stacking) + `.team-default`/`.team-detail` (opacity/visibility transitions). Pegado al final del bloque `.team-card p` en el `<style>`.


| Code | Element | Line | Current content |
|---|---|---|---|
| `H4-LABEL` | Eyebrow | 1554 | `El equipo` |
| `H4-HEADLINE` | Section title | 1555 | `Personas reales, resultados reales` (last 2 words in cyan) |
| `H4-DESC` | Section description | 1556-1558 | `Conoce a quienes estarán detrás de tu empresa. Transparencia total.` |
| `H4-MEMBER1-AVATAR` | Member 1 initials | 1563 | `FZ` (blue gradient) |
| `H4-MEMBER1-NAME` | Member 1 name | 1564 | `Francisco Zamora` |
| `H4-MEMBER1-ROLE` | Member 1 role | 1565 | `Líder Contable` |
| `H4-MEMBER1-BIO` | Member 1 bio | 1566 | `Especialista en grupos económicos...` |
| `H4-MEMBER2-AVATAR` | Member 2 initials | 1569 | `MP` (cyan gradient) |
| `H4-MEMBER2-NAME` | Member 2 name | 1570 | `Mario Pérez` |
| `H4-MEMBER2-ROLE` | Member 2 role | 1571 | `Digital & Ads` |
| `H4-MEMBER2-BIO` | Member 2 bio | 1572 | `Analista de datos, desarrollo web...` |
| `H4-MEMBER3-AVATAR` | Member 3 initials | 1575 | `JR` (orange gradient) |
| `H4-MEMBER3-NAME` | Member 3 name | 1576 | `Jerussa` |
| `H4-MEMBER3-ROLE` | Member 3 role | 1577 | `Desarrollo de Negocios` |
| `H4-MEMBER3-BIO` | Member 3 bio | 1578 | `Primera persona que atenderá tu consulta...` |
| `H4-MEMBER4-AVATAR` | Member 4 initials | 1581 | `CC` (green gradient) |
| `H4-MEMBER4-NAME` | Member 4 name | 1582 | `Claudio Castro` |
| `H4-MEMBER4-ROLE` | Member 4 role | 1583 | `Abogado Laboral` |
| `H4-MEMBER4-BIO` | Member 4 bio | 1584 | `Experto en negociaciones colectivas...` |
| `H4-MEMBER1-CTA` | Member 1 hover CTA | new | `Ver Contabilidad →` |
| `H4-MEMBER2-CTA` | Member 2 hover CTA | new | `Ver Digital →` |
| `H4-MEMBER3-CTA` | Member 3 hover CTA | new | `Contactar →` (Jerussa = contacto, no landing) |
| `H4-MEMBER4-CTA` | Member 4 hover CTA | new | `Ver Asesoría Legal →` |

### `H5-*` — Contacto + Form (L1590-1676)

| Code | Element | Line | Current content |
|---|---|---|---|
| `H5-LABEL` | Eyebrow | 1595 | `Hablemos` |
| `H5-HEADLINE` | Section title | 1597 | `¿Listo para dar el primer paso?` (last 2 words in cyan) |
| `H5-SUB` | Sub | 1599 | `La primera consulta es gratis. Sin compromiso. Te respondemos antes de 24 horas.` |
| `H5-CONTACT-PHONE-LABEL` | Phone label | 1606 | `WhatsApp disponible` |
| `H5-CONTACT-EMAIL-LABEL` | Email label | 1613 | `Respuesta en 24 hrs` |
| `H5-CONTACT-LOC-LABEL` | Location label | 1620 | `Atención presencial y online` |
| `H5-CONTACT-CTA` | WhatsApp button | 1624-1626 | `Escribir por WhatsApp` |
| `H5-FORM-TITLE` | Form card title | 1632 | `Solicitar reunión o consulta` |
| `H5-FORM-NOMBRE` | Nombre label/placeholder | 1637-1638 | `Nombre *` / `Tu nombre` |
| `H5-FORM-EMPRESA` | Empresa label/placeholder | 1641-1642 | `Empresa` / `Nombre de tu empresa` |
| `H5-FORM-EMAIL` | Email label/placeholder | 1647-1648 | `Email *` / `tu@email.com` |
| `H5-FORM-TEL` | Teléfono label/placeholder | 1651-1652 | `Teléfono` / `+56 9 ...` |
| `H5-FORM-SERVICIO` | Servicio dropdown | 1657-1663 | Selecciona... / 4 options (Contable, Digital, Laboral, Todos) |
| `H5-FORM-MENSAJE` | Mensaje textarea | 1666-1667 | `Mensaje *` / `Cuéntanos sobre tu empresa...` |
| `H5-FORM-SUBMIT` | Submit button | 1669-1671 | `Enviar consulta gratuita` |

---

## CONTABLE page (L1684-1847) — `page-contable`

### `CN1-*` — Hero (L1687-1710)

| Code | Element | Line | Current content |
|---|---|---|---|
| `CN1-LABEL` | Eyebrow | 1690-1692 | `Contabilidad Estratégica · Francisco Zamora` |
| `CN1-HEADLINE` | Hero `<h1>` | 1694 | `Tu contador actual / ¿te genera valor / o solo cumple?` |
| `CN1-SUB` | Sub paragraph | 1695-1699 | `La contabilidad estratégica no es solo ahorro de impuestos...` |
| `CN1-CTA1` | Primary button | 1701-1703 | `🩺 Solicitar diagnóstico gratuito` |
| `CN1-CTA2` | WhatsApp ghost btn | 1704-1706 | `Hablar con Francisco` (prefill: `Hola, quiero consultar sobre contabilidad estratégica`) |

### `CN2-*` — Dolor / Problema (L1713-1758)

| Code | Element | Line | Current content |
|---|---|---|---|
| `CN2-LABEL` | Eyebrow | 1716 | `El problema` |
| `CN2-HEADLINE` | Section title | 1717 | `¿Te suena familiar?` (last word in cyan) |
| `CN2-TEXT-TITLE` | Left col subhead | 1721 | `Lo que pasa en la mayoría de empresas` |
| `CN2-TEXT-DESC` | Left col intro | 1722-1725 | `La mala relación con el contador es más común...` |
| `CN2-PAIN1..5` | Pain bullets | 1728-1732 | 5 items: balances, declaración only, no real-time, "solo grandes", decisiones sin datos |
| `CN2-CARD-TITLE` | Right card heading | 1737 | `Lo que tendrás en 30 días` |
| `CN2-RESULT1..4` | Result items | 1739-1754 | Visualización / Dashboard / Plan de acción / Acceso directo a Francisco |

### `CN3-*` — Garantía banner (L1761-1776)

| Code | Element | Line | Current content |
|---|---|---|---|
| `CN3-ICON` | Emoji icon | 1765 | `🎁` |
| `CN3-TITLE` | Banner title | 1767 | `Garantía: Primer mes GRATIS` |
| `CN3-BODY` | Banner body | 1768-1772 | `Al incorporarte como cliente contable, el primer mes no te cobramos nada...` |

### `CN4-*` — Pasos / Proceso (L1779-1804)

| Code | Element | Line | Current content |
|---|---|---|---|
| `CN4-LABEL` | Eyebrow | 1782 | `¿Cómo funciona?` |
| `CN4-HEADLINE` | Section title | 1783 | `3 pasos para empezar` (last word in cyan) |
| `CN4-STEP1-TITLE` | Step 1 title | 1789 | `Diagnóstico gratuito` |
| `CN4-STEP1-BODY` | Step 1 body | 1790 | `Nos cuentas tu situación actual...` |
| `CN4-STEP2-TITLE` | Step 2 title | 1794 | `Plan personalizado` |
| `CN4-STEP2-BODY` | Step 2 body | 1795 | `Diseñamos un plan contable hecho para tu empresa...` |
| `CN4-STEP3-TITLE` | Step 3 title | 1799 | `Primer mes gratis` |
| `CN4-STEP3-BODY` | Step 3 body | 1800 | `Empezamos de inmediato...` |

### `CN5-*` — Métricas (L1807-1828)

| Code | Element | Line | Current content |
|---|---|---|---|
| `CN5-LABEL` | Eyebrow | 1810 | `Resultados` |
| `CN5-HEADLINE` | Section title | 1811 | `Lo que cambia contigo` (`cambia` in cyan) |
| `CN5-METRIC1` | Metric 1 | 1815-1816 | `30d` · `Para tener visibilidad completa de tu empresa` |
| `CN5-METRIC2` | Metric 2 | 1819-1820 | `0$` · `Costo del primer mes al incorporarte` |
| `CN5-METRIC3` | Metric 3 | 1823-1824 | `1clic` · `Para acceder a información contable cuando la necesites` |

### `CN6-*` — CTA Final (L1831-1845)

| Code | Element | Line | Current content |
|---|---|---|---|
| `CN6-HEADLINE` | CTA heading | 1834 | `Tu empresa merece una contabilidad que trabaje para ti` |
| `CN6-SUB` | CTA sub | 1835 | `Escríbenos hoy y te hacemos el diagnóstico sin costo. Solo necesitamos 30 minutos.` |
| `CN6-CTA1` | Primary button | 1837-1839 | `🩺 Solicitar diagnóstico gratuito` |
| `CN6-CTA2` | WhatsApp ghost btn | 1840-1842 | `WhatsApp ahora` |

---

## DIGITAL page (L1853-1999) — `page-digital`

### `DG1-*` — Hero (L1856-1878)

| Code | Element | Line | Current content |
|---|---|---|---|
| `DG1-LABEL` | Eyebrow | 1859-1861 | `Digital & Google Ads · Mario Pérez` |
| `DG1-HEADLINE` | Hero `<h1>` | 1863 | `Multiplica tus / consultas en / 15 días` (last in orange) |
| `DG1-SUB` | Sub paragraph | 1864-1867 | `¿Gastas en publicidad sin saber si funciona?...` |
| `DG1-CTA1` | Primary button | 1869-1871 | `🚀 Multiplica tus consultas hoy` |
| `DG1-CTA2` | WhatsApp ghost btn | 1872-1874 | `Hablar con Mario` |

### `DG2-*` — Miedo / Objeción (L1881-1909)

| Code | Element | Line | Current content |
|---|---|---|---|
| `DG2-LABEL` | Eyebrow | 1884 | `Tu principal duda` |
| `DG2-HEADLINE` | Section title | 1885 | `¿Cuánto cuesta / vs cuánto retorna?` (last 2 words in cyan) |
| `DG2-DESC` | Section description | 1886-1888 | `Entendemos que invertir en digital genera miedo...` |
| `DG2-CARD1-TITLE` | Card 1 title | 1894 | `Control de gastos semanal` |
| `DG2-CARD1-BODY` | Card 1 body | 1895 | `Cada semana recibes un reporte detallado...` |
| `DG2-CARD2-TITLE` | Card 2 title | 1899 | `Reportes de usuarios reales` |
| `DG2-CARD2-BODY` | Card 2 body | 1900 | `Ves cuántas personas llegaron a tu sitio...` |
| `DG2-CARD3-TITLE` | Card 3 title | 1904 | `Estimaciones de Google` |
| `DG2-CARD3-BODY` | Card 3 body | 1905 | `Antes de invertir, Google nos entrega estimaciones...` |

### `DG3-*` — Servicios digitales (L1912-1964)

| Code | Element | Line | Current content |
|---|---|---|---|
| `DG3-LABEL` | Eyebrow | 1915 | `Servicios digitales` |
| `DG3-HEADLINE` | Section title | 1916 | `Todo lo que hacemos por ti` (last 3 in cyan) |
| `DG3-ITEM1-TITLE` | Service 1 title | 1923 | `Google Ads` |
| `DG3-ITEM1-BODY` | Service 1 body | 1924 | `Campañas de búsqueda, display y remarketing...` |
| `DG3-ITEM2-TITLE` | Service 2 title | 1930 | `Desarrollo Web` |
| `DG3-ITEM2-BODY` | Service 2 body | 1931 | `Sitios profesionales, rápidos y optimizados...` |
| `DG3-ITEM3-TITLE` | Service 3 title | 1937 | `Analítica y Datos` |
| `DG3-ITEM3-BODY` | Service 3 body | 1938 | `Google Analytics, Search Console, Tag Manager...` |
| `DG3-ITEM4-TITLE` | Service 4 title | 1944 | `Herramientas Digitales` |
| `DG3-ITEM4-BODY` | Service 4 body | 1945 | `Automatizaciones, apps, integraciones...` |
| `DG3-ITEM5-TITLE` | Service 5 title | 1951 | `Compras Internacionales` |
| `DG3-ITEM5-BODY` | Service 5 body | 1952 | `Asesoría para importación y gestión de compras...` |
| `DG3-ITEM6-TITLE` | Service 6 title | 1958 | `Reuniones mensuales` |
| `DG3-ITEM6-BODY` | Service 6 body | 1959 | `Cada mes nos reunimos contigo para revisar...` |

### `DG4-*` — Garantía digital (L1967-1981)

| Code | Element | Line | Current content |
|---|---|---|---|
| `DG4-ICON` | Emoji icon | 1971 | `📊` |
| `DG4-TITLE` | Banner title | 1973 | `Resultados en 15-30 días` |
| `DG4-BODY` | Banner body | 1974-1977 | `Mayor cantidad de llamadas y consultas...` |

### `DG5-*` — CTA Final (L1984-1997)

| Code | Element | Line | Current content |
|---|---|---|---|
| `DG5-HEADLINE` | CTA heading | 1986 | `¿Listo para que más clientes encuentren tu negocio?` |
| `DG5-SUB` | CTA sub | 1987 | `Sin compromiso. Te mostramos las estimaciones de alcance antes de invertir un peso.` |
| `DG5-CTA1` | Primary button | 1989-1991 | `🚀 Multiplica tus consultas` |
| `DG5-CTA2` | WhatsApp ghost btn | 1992-1994 | `Hablar con Mario` |

---

## LABORAL page (L2005-2203) — `page-laboral`

### `LB1-*` — Hero (L2008-2031)

| Code | Element | Line | Current content |
|---|---|---|---|
| `LB1-LABEL` | Eyebrow | 2011-2013 | `Derecho Laboral · Claudio Castro` |
| `LB1-HEADLINE` | Hero `<h1>` | 2015 | `Protege tu empresa / antes de que / sea tarde` (last in orange) |
| `LB1-SUB` | Sub paragraph | 2016-2020 | `El error más caro para un empleador no es la multa...` |
| `LB1-CTA1` | Primary button | 2022-2024 | `🛡️ Protege tu empresa ahora` |
| `LB1-CTA2` | WhatsApp ghost btn | 2025-2027 | `Revisión gratuita de contrato` |

### `LB2-*` — Errores frecuentes (L2034-2073)

| Code | Element | Line | Current content |
|---|---|---|---|
| `LB2-LABEL` | Eyebrow | 2037 | `El error más caro` |
| `LB2-HEADLINE` | Section title | 2038 | `Lo que no sabes ya te está costando` (last 4 in cyan) |
| `LB2-BANNER-TITLE` | Banner heading | 2041 | `Errores laborales frecuentes en empresas de la zona` |
| `LB2-ERR1-TITLE` | Error 1 title | 2046 | `Trabajadores sin contrato o con contrato desactualizado` |
| `LB2-ERR1-BODY` | Error 1 body | 2047 | `Un contrato mal redactado o sin actualizar...` |
| `LB2-ERR2-TITLE` | Error 2 title | 2053 | `Imposiciones no pagadas o pagadas con errores` |
| `LB2-ERR2-BODY` | Error 2 body | 2054 | `Las imposiciones mal declaradas generan deudas...` |
| `LB2-ERR3-TITLE` | Error 3 title | 2060 | `Falta de anexos de contrato` |
| `LB2-ERR3-BODY` | Error 3 body | 2061 | `Cambios de funciones, de jornada o de sueldo...` |
| `LB2-ERR4-TITLE` | Error 4 title | 2067 | `No tener asesoría en negociaciones colectivas` |
| `LB2-ERR4-BODY` | Error 4 body | 2068 | `Una negociación colectiva mal manejada...` |

### `LB3-*` — Resultado inmediato (L2076-2097)

| Code | Element | Line | Current content |
|---|---|---|---|
| `LB3-LABEL` | Eyebrow | 2079 | `Resultado inmediato` |
| `LB3-HEADLINE` | Section title | 2080 | `¿Qué obtienes desde el primer día?` (last 3 in cyan) |
| `LB3-CARD1` | Card 1 | 2083-2086 | `📄` · `Revisión documental completa` · `de contratos y anexos con análisis detallado` |
| `LB3-CARD2` | Card 2 | 2087-2090 | `📋` · `Plan de acción` · `con pasos concretos para regularizar tu situación` |
| `LB3-CARD3` | Card 3 | 2091-2094 | `⚖️` · `Asesoría preventiva` · `para evitar problemas antes de que ocurran` |

### `LB4-*` — Cobertura completa (L2100-2132)

| Code | Element | Line | Current content |
|---|---|---|---|
| `LB4-LABEL` | Eyebrow | 2103 | `Cobertura completa` |
| `LB4-HEADLINE` | Section title | 2104 | `Prevenimos y representamos` (last word in cyan) |
| `LB4-COL1-TITLE` | Col 1 (blue) title | 2109 | `🛡️ Asesoría Preventiva` |
| `LB4-COL1-L1..L6` | Col 1 list items | 2111-2116 | 6 bullets: Contratos / Anexos / Liquidaciones / Imposiciones / Desvinculaciones / Negociaciones |
| `LB4-COL2-TITLE` | Col 2 (orange) title | 2120 | `⚖️ Representación en Litigios` |
| `LB4-COL2-L1..L6` | Col 2 list items | 2122-2127 | 6 bullets: Demandas / Inspección / Mediación / Negociaciones / Reclamación / Tribunales |

### `LB5-*` — Planes / Modalidades (L2135-2185)

| Code | Element | Line | Current content |
|---|---|---|---|
| `LB5-LABEL` | Eyebrow | 2138 | `Modalidades` |
| `LB5-HEADLINE` | Section title | 2139 | `Elige cómo trabajar con nosotros` (last 3 in cyan) |
| `LB5-DESC` | Section description | 2140-2142 | `Cotización personalizada en ambos casos. Sin precio público...` |
| `LB5-PLAN1-BADGE` | Plan 1 badge | 2147 | `Opción 1` |
| `LB5-PLAN1-TITLE` | Plan 1 title | 2148 | `Plan mensual a todo evento` |
| `LB5-PLAN1-PRECIO` | Plan 1 price | 2149 | `A consultar / mes` |
| `LB5-PLAN1-DESC` | Plan 1 description | 2150-2153 | `Asesoría laboral permanente...` |
| `LB5-PLAN1-FEAT1..4` | Plan 1 features | 2155-2158 | 4 bullets: <24hr / Revisión mensual / Representación básica / WhatsApp ilimitado |
| `LB5-PLAN1-CTA` | Plan 1 button | 2160-2162 | `Consultar precio` |
| `LB5-PLAN2-BADGE` | Plan 2 badge | 2166 | `Opción 2` |
| `LB5-PLAN2-TITLE` | Plan 2 title | 2167 | `Trabajos puntuales` |
| `LB5-PLAN2-PRECIO` | Plan 2 price | 2168 | `Por proyecto / servicio` |
| `LB5-PLAN2-DESC` | Plan 2 description | 2169-2172 | `Necesitas algo específico...` |
| `LB5-PLAN2-FEAT1..4` | Plan 2 features | 2174-2177 | 4 bullets: Sin permanencia / Presupuesto / Revisión gratuita / Urgente |
| `LB5-PLAN2-CTA` | Plan 2 button | 2179-2181 | `Solicitar presupuesto` |

### `LB6-*` — CTA Final (L2188-2201)

| Code | Element | Line | Current content |
|---|---|---|---|
| `LB6-HEADLINE` | CTA heading | 2190 | `La primera revisión de contrato es gratis` (`gratis` in orange) |
| `LB6-SUB` | CTA sub | 2191 | `Escríbenos hoy. Revisamos un contrato sin costo...` |
| `LB6-CTA1` | Primary button | 2193-2195 | `🛡️ Protege tu empresa ahora` |
| `LB6-CTA2` | WhatsApp ghost btn | 2196-2198 | `Revisión gratuita` |

---

## Component templates (for adding new items)

### Add a service card to `H2-*` (Home, Servicios)

Pattern at L1435-1449 (existing CARD1). Copy the block, change:
- Stripe color (`--stripe-color` inline style): `var(--cyan)` / `var(--naranja)` / `#2ED6A0` or a new hex
- Icon background (`background:rgba(...)` inline): match stripe color at 12% alpha
- Icon color (`color:var(...)` inline): match stripe color
- Font Awesome icon class (`<i class="fas fa-...">`): pick from https://fontawesome.com/icons
- `onclick="showPage('contable')"`: target page or remove if it's not a landing
- `<h3>` title and `<p>` body

Also: update `.servicios-grid` (L572-575) `grid-template-columns` if going past 3 columns — current is `repeat(3, 1fr)`.

### Add a team member to `H4-*` (Home, Equipo)

Pattern at L1562-1567 (FZ card). Copy block, change:
- Avatar class: `av-azul` / `av-cyan` / `av-naranja` / `av-verde` (defined L760-763) — or define a new gradient in CSS
- Initials inside `<div class="team-avatar ...">`
- `<h4>` name, `<div class="team-role">` role, `<p>` bio

Also: equipo-grid (L731-735) uses `repeat(4, 1fr)`. Adding a 5th requires resizing or it'll squeeze the row.

### Add a new error to `LB2-*` (Laboral, Errores)

Pattern at L2043-2049 (ERR1 block). Inside `<div class="error-banner ...">`. Copy `.error-item` block, change `<h5>` title + `<p>` body. Last item should not need extra styling — `.error-item:last-child` rule (L1137) handles the bottom border.

### Add a step to `CN4-*` (Contable, Pasos)

Pattern at L1787-1791 (paso-card block). Increment `paso-num` ("04", "05"...). Update `.pasos-grid` columns if going past 3 (L961: `repeat(3, 1fr)`).

### Add a new page (e.g., "auditoría")

Non-trivial — touches multiple places:
1. Add nav link in `HD-NAV*` (L1290-1296 desktop, L1312-1317 mobile).
2. Add a footer link in `FT-COL2-*` (L2237-2242).
3. Add the page block: `<div id="page-auditoria" class="hidden">...</div>` somewhere between existing page divs.
4. Add `'auditoria'` to the `pages` array (L2293).
5. Add URL mapping in `urls` object (L2313-2318).
6. Add path detection in `DOMContentLoaded` (L2392-2396) and `popstate` (L2401-2406).
7. Add `showPage('auditoria')` references where needed.

---

## TODOs / known issues

- **Form is stubbed**: `submitForm()` at L2343 just logs to console. Wire to EmailJS / Formspree / backend before launch.
- **No favicon**: missing `<link rel="icon">` in `<head>` (L3-12).
- **No OG tags**: missing `<meta property="og:title">` / `og:image` / `og:description` etc. for social sharing.
- **No JSON-LD structured data**: would help SEO for a local business.
- **`alt` attributes**: SVGs are inline (good), no `<img>` tags found, so no accessibility issue on that front.
- **The detached HTML comment at L2412-2444** is the original Claude artifact's "how to split into files" guide. Harmless but can be deleted if not needed.
- **Copyright says `© 2025`** at L2280 — today's date is 2026-05-13. Probably should update.

---
<!-- METADATA: type: site-map · version: 1.0 · created: 2026-05-13 · source: MA/ma-site/index.html (2444 lines) -->
