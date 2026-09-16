# VW Group — Circuito productivo: tabla input-output a nivel de firma

Repositorio de datos del estudio empírico de la cadena de suministro de Volkswagen Group mediante relaciones input-output, como parte de la tesis doctoral sobre reorganización global de la producción y rotación del capital.

## Estructura

```
data/
  nodes.csv    — Firmas participantes (nodos del grafo)
  edges.csv    — Relaciones de compra-venta (aristas del grafo)
index.html     — Visualización interactiva (D3.js, GitHub Pages)
README.md      — Este archivo
```

## Esquema de datos

### nodes.csv

| Campo | Descripción |
|---|---|
| `id` | Identificador único (slug) |
| `name` | Nombre del grupo consolidado |
| `tier` | Posición en la cadena (0=integrador, 1=proveedor directo, 2=proveedor de proveedor, 3=base) |
| `type` | Clasificación funcional: Integrador, Generalista, Especialista, JV, Filial |
| `country` | País (ISO 2) |
| `revenue` | Facturación total del grupo (millones) |
| `revenue_currency` | Moneda (EUR, USD) |
| `pi_vw` | πVW: porcentaje de facturación atribuible a VW Group |
| `components` | Productos/componentes que suministra |
| `includes` | Filiales absorbidas por M&A |
| `source` | Fuente bibliográfica de identificación |
| `notes` | Notas adicionales |

### edges.csv

| Campo | Descripción |
|---|---|
| `id` | Identificador único de la relación |
| `from` | ID del vendedor |
| `to` | ID del comprador |
| `component` | Qué se vende |
| `evidence` | Nivel de certeza: BOM (confirmado por MarkLines/ETKA/teardown) o EST (estimado por SEC filings/cascada πVW/literatura) |
| `source_ref` | Referencia bibliográfica específica |

## Metodología

Los nodos representan **grupos consolidados** (no filiales individuales). Si una empresa ha sido absorbida por otra (ej. TRW → ZF, HELLA → Forvia), se registra como un solo nodo con la absorbida en el campo `includes`.

Las relaciones tienen dos niveles de certeza:
- **BOM**: confirmadas por datos de Bill of Materials (MarkLines Who Supplies Whom, ETKA, fotos de ferias, informes de teardown)
- **EST**: estimadas por filings regulatorios (SEC XBRL customer concentration >10%), bases de datos de cadena de suministro (LSEG Workspace, Bloomberg SPLC), o literatura analizada

## Fuentes de datos

- VW Group Annual Report 2024
- VW Group Award (2020-2025)
- MarkLines Automotive Information Platform (Who Supplies Whom, Supplier Database)
- SEC EDGAR XBRL filings (customer concentration disclosures)
- Informes anuales de proveedores cotizados
- Orbis (Bureau van Dijk) — datos financieros
- LSEG Workspace (Eikon) — relaciones de cadena de suministro
- Literatura académica sobre cadenas globales de valor automotriz

## Contexto académico

- **Tesis doctoral**: Reorganización global de la producción y rotación del capital
- **Programa**: Doctorado en Economía, Universidad Complutense de Madrid
- **Director**: Juan Pablo Mateo Tomé, Departamento de Economía Aplicada, Estructura e Historia
- **Marco teórico**: Economía política marxista, cadenas globales de mercancías, fragmentación productiva internacional

## Licencia

Datos de investigación académica. Los datos de facturación y relaciones comerciales provienen de fuentes públicas (informes anuales, filings regulatorios, bases de datos comerciales).
