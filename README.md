# BVS / VHL: Searching Regional Databases for Evidence Synthesis

> Strategic guidance for identifying, retrieving, and managing health science literature from the Virtual Health Library across Latin America and the Caribbean.

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-blue.svg)](https://creativecommons.org/licenses/by/4.0/)
![Status: Active](https://img.shields.io/badge/status-active-success)
![Last Updated](https://img.shields.io/badge/updated-2026--05-blue)

**Wilson Falco, MD**  
FAMECA | Catanduva, SP, Brazil

---

## Table of Contents

- [Rationale](#-rationale)
- [The BVS Infrastructure](#-the-bvs-infrastructure)
- [Controlled Vocabulary Fundamentals](#-controlled-vocabulary-fundamentals)
- [Building Search Strings](#-building-search-strings)
- [Query Construction](#-query-construction)
- [Reference Export Workflow](#-reference-export-workflow)
- [Institutional Resources](#-institutional-resources)
- [References & Examples](#-references--examples)
- [Contributing & Feedback](#-contributing--feedback)

---

## 🎯 Rationale

Systematic reviews and meta-analyses that rely exclusively on MEDLINE, Embase, and Scopus systematically exclude evidence published in smaller journals, national repositories, and regional proceedings across Latin America and the Caribbean. The Virtual Health Library (VHL / *Biblioteca Virtual em Saúde* — BVS) exists specifically to address this gap.

```
┌─────────────────────────────────────────────────────┐
│   Global Biomedical Literature Landscape            │
├─────────────────────────────────────────────────────┤
│                                                       │
│  ┌─────────────┐  ┌──────────┐  ┌─────────────┐     │
│  │ PubMed /    │  │ Embase   │  │  Scopus     │     │
│  │ MEDLINE     │  │          │  │             │     │
│  └─────────────┘  └──────────┘  └─────────────┘     │
│         ▲                ▲               ▲            │
│         │      ┌────────┴────────┐      │            │
│         └──────│    Primary      │──────┘            │
│                │  Indexing Flow  │                   │
│                └────────┬────────┘                   │
│                         │                            │
│                ┌────────▼────────┐                   │
│                │  Regional &     │                   │
│                │  Grey Literature│                   │
│                │  Not Captured    │  ◄─── BVS Gap   │
│                └─────────────────┘     Fills Here   │
│                                                       │
└─────────────────────────────────────────────────────┘
```

**Key advantages of searching the BVS:**

- Accesses LILACS (>900k records since 1982) — journals not in PubMed
- Indexes grey literature: dissertations, conference abstracts, government reports
- Multilingual coverage: Portuguese, Spanish, English, French
- Meets PRISMA and Cochrane Handbook requirements for multi-database searches
- Reduces publication bias by capturing null/negative results often excluded from mainstream venues

---

## 🏗️ The BVS Infrastructure

The VHL is operated by **BIREME** under the Pan American Health Organization (PAHO/WHO), established in 1998 to democratize access to health information. The platform integrates approximately 60 bibliographic sources.

### 📊 Primary Databases

| Name | Scope | Coverage |
|---|---|---|
| **LILACS** | Latin American & Caribbean journals, theses, reports | 1982–present; 900k+ records |
| **MEDLINE** | Via parallel indexing | All MEDLINE content |
| **IBECS** | Spanish health journals | Spain-focused |
| **WPRIM** | Western Pacific journals | China, Japan, Korea, Philippines, etc. |
| **BINACIS** | Argentine national bibliography | Argentina-focused |
| **BRISA/RedTESA** | Health technology assessments | Brazil & regional HTA |
| **PAHO-IRIS** | PAHO institutional repository | Policy, technical reports |

### 📂 Result Organization

Search results appear in two tabs:

- **LILACS Plus**: Curated subset emphasizing regional sources with quality filters
- **Complete Collection**: All integrated databases (MEDLINE included)

For systematic reviews, report both independently and apply database-level filters to identify records unique to each source.

---

## 🔤 Controlled Vocabulary Fundamentals

Each database tags articles using a standardized **indexing vocabulary**. Using the correct terms is the foundation of reproducible, sensitive searches.

```
    ┌──────────────────────────────────────────────────┐
    │   How Controlled Vocabulary Works                 │
    ├──────────────────────────────────────────────────┤
    │                                                    │
    │  Author writes:                                   │
    │  "Thermal trauma in children"                     │
    │           │                                       │
    │           ▼                                       │
    │  Indexer assigns:                                 │
    │  MeSH:  "Burns" + "Child"                         │
    │  DeCS:  "Queimaduras" + "Criança"                 │
    │           │                                       │
    │           ▼                                       │
    │  Researcher searches:                             │
    │  MH:"Burns" OR (Burn) OR (Thermal injury)         │
    │           │                                       │
    │           ▼                                       │
    │  ✓ Article retrieved regardless of author's word  │
    │    choice—because indexing standardized it        │
    │                                                    │
    └──────────────────────────────────────────────────┘
```

### Database Vocabularies

| Platform | Vocabulary | URL |
|---|---|---|
| **PubMed** | MeSH (Medical Subject Headings) | [mesh.nlm.nih.gov](https://mesh.nlm.nih.gov) |
| **Embase** | Emtree | [embase.com](https://www.embase.com) |
| **BVS/LILACS** | DeCS (Descritores em Ciências da Saúde) | [decs.bvsalud.org](https://decs.bvsalud.org) |

Most DeCS terms correspond to MeSH equivalents, but regional health topics are unique to DeCS (e.g., *Serviços de Saúde do Interior*, rural health services).

---

## 🔍 Building Search Strings

### 📍 Step 1: Retrieve Descriptors from DeCS

Navigate to [decs.bvsalud.org](https://decs.bvsalud.org) and search for your concept.

For each relevant descriptor, record:
- **English name** and equivalents in Spanish, Portuguese, French
- **Entry terms** (synonyms indexed to that descriptor)
- **Tree number** (hierarchical code; use * suffix to capture narrower terms)

### 🏗️ Step 2: Construct Term Strings

General format:
```
MH:"Preferred Term" OR (Synonym 1) OR (Synonym 2) OR (Foreign equivalent) OR MH:TreeNumber*
```

#### Syntax Rules

⚠️ **Critical details:**

1. Use **straight quotation marks** `"` — typographic smart quotes break the BVS parser
2. **No space** after `MH:` → `MH:"Burns"` ✓ · `MH: "Burns"` ✗
3. Tree numbers must end with `*` to include child terms in the hierarchy

### 💡 Step 3: Example — Burns + United States

```
#1  MH:"United States" OR (United States) OR (Estados Unidos) 
    OR MH:Z01.107.567.875*

#2  MH:"Queimaduras" OR (Queimaduras) OR (Burns) OR (Quemaduras) 
    OR (Queimadura) OR MH:C26.200*

#3  MH:"Queimaduras Químicas" OR (Queimaduras Químicas) 
    OR (Burns, Chemical) OR (Quemaduras Químicas) OR MH:C26.200.156*

#4  MH:"Queimaduras Oculares" OR (Queimaduras Oculares) OR (Eye Burns) 
    OR (Quemaduras Oculares) OR MH:C10.900.300.284.250.250*

#5  MH:"Queimaduras por Inalação" OR (Queimaduras por Inalação) 
    OR (Burns, Inhalation) OR MH:C26.200.322*

#6  #2 OR #3 OR #4 OR #5           [Exposure block]

#7  #1 AND #6                       [Final: Population AND Exposure]
```

---

## 💻 Query Construction

### Workflow: Block-Building Strategy

```
    Input Term Strings
           │
           ▼
    ┌──────────────────┐
    │ Merge within     │
    │ blocks using OR  │
    └─────┬────────────┘
          │
          ▼
    ┌──────────────────┐
    │ Population Block │  #1 OR #2
    │ Exposure Block   │  #3 OR #4 OR #5
    │ Outcome Block    │  #6 OR #7
    └─────┬────────────┘
          │
          ▼
    ┌──────────────────┐
    │ Combine blocks   │
    │ using AND        │  #1-2 AND #3-5 AND #6-7
    └─────┬────────────┘
          │
          ▼
    Final Query String
           │
           ▼
    Submit to BVS Advanced Search
    ──→ [View both LILACS Plus & Complete Collection tabs]
    ──→ [Apply database filters on sidebar]
```

### 🧭 Navigating the BVS Advanced Search

1. Open [BVS Advanced Search](https://bvsalud.org)
2. Enter **one search string per line**
3. Use Boolean operator dropdown (AND/OR) to chain lines
4. Click "Search" to retrieve results

**Result tips:**
- Filter by individual database (MEDLINE, LILACS, WPRIM, etc.)
- Export all references from the export button on results sidebar

---

## 📤 Reference Export Workflow

BVS export files often contain formatting artifacts incompatible with screening platforms. Use this middleware approach:

```
┌─────────────────────────────────────────────────────┐
│  BVS Export Compatibility Pathway                   │
├─────────────────────────────────────────────────────┤
│                                                      │
│  ┌──────────┐      ┌───────────┐                   │
│  │  BVS     │      │ Mendeley  │                   │
│  │ Results  │──1──▶│ (Import)  │──2──┐             │
│  │          │      │           │     │             │
│  └──────────┘      └───────────┘     │             │
│                                       ▼             │
│  ┌──────────┐      ┌───────────┐  ┌─────────┐      │
│  │ Rayyan   │◀──4──│ .RIS File │◀─│ Mendeley│  3  │
│  │ (or      │      │ Export    │  │ (Re-exp)│     │
│  │ Covidence)      │           │  └─────────┘     │
│  └──────────┘      └───────────┘                   │
│                                                      │
│  Notes:                                             │
│  • Do NOT import raw BVS exports to Zotero         │
│  • Mendeley reformats metadata to standard RIS     │
│  • Re-export from Mendeley as .RIS before import   │
│                                                      │
└─────────────────────────────────────────────────────┘
```

### 🚀 Step-by-Step

1. **Export from BVS:** Click "Export" on results sidebar → "All references"
2. **Import to Mendeley:** Open Mendeley Desktop/Reference Manager → File → Import
3. **Re-export to standard format:** Select all → Export → .RIS format
4. **Upload to screening platform:** Rayyan, Covidence, or ASReview → Import from file

**Known issue:** Direct Zotero imports from BVS cause parsing failures (malformed author names, missing fields). Always use the Mendeley intermediary.

---

## 📚 References & Examples

1. **Paraná VC, Feitosa CA, da Silva GC, Gois LL, Santos LA.** Risk factors associated with severe dengue in Latin America: a systematic review and meta-analysis. *Tropical Medicine & International Health*. 2024;29(3):173–191. [https://doi.org/10.1111/tmi.13968](https://doi.org/10.1111/tmi.13968)
   
   **Rationale:** Exemplifies multi-database strategy (PubMed, SciELO, LILACS, EMBASE) for regional health topics. Demonstrates LILACS contribution to Latin American epidemiology where regional databases were essential for capturing local studies.

2. **Delfino C, Núñez M, Asenjo-Lobos C, Gonzalez F, Riviotta A, Urrutia F, Lavados P, Anderson CS, Muñoz Venturelli P.** Stroke in Latin America: systematic review of incidence, prevalence, and case-fatality in 1997–2021. *International Journal of Stroke*. 2023;18(6):645–656. [https://doi.org/10.1177/17474930221143323](https://doi.org/10.1177/17474930221143323)
   
   **Rationale:** Demonstrates why LILACS is irreplaceable for regional health data. The authors searched MEDLINE, Web of Science, and LILACS specifically because many Latin American stroke epidemiology studies are published locally and not indexed in mainstream databases.

3. **Guzman-Holst A, DeAntonio R, Prado-Cohrs D, Juliao P.** Barriers to vaccination in Latin America: a systematic literature review. *Vaccine*. 2019;38(3):470–481. [https://doi.org/10.1016/j.vaccine.2019.10.088](https://doi.org/10.1016/j.vaccine.2019.10.088)
   
   **Rationale:** Searched nine databases including LILACS, MedCarib, and SciELO to capture region-specific vaccine hesitancy studies. Documents that many LAC publications are linguistically diverse and concentrated in regional repositories.

4. **Campanatti-Ostiz H, Andrade CRF.** Health sciences descriptors in the Brazilian speech-language and hearing science. *Pro Fono*. 2010;22(4):397–402. [https://doi.org/10.1590/s0104-56872010000400006](https://doi.org/10.1590/s0104-56872010000400006)
   
   **Rationale:** Demonstrates the construction and application of DeCS descriptors for specialized domains. Shows how controlled vocabulary works across Portuguese, English, and Spanish, fundamental to BVS indexing philosophy.

5. **Alves Martins BA, Avellaneda N, Piozzi GN.** Robotic colorectal surgery in Latin America: a systematic review on surgical outcomes. *Frontiers in Surgery*. 2024;11:1480444. [https://doi.org/10.3389/fsurg.2024.1480444](https://doi.org/10.3389/fsurg.2024.1480444)
   
   **Rationale:** Recent systematic review of LAC surgical literature that explicitly searched LILACS, Scopus, Cochrane, and SciELO. Demonstrates current best practice in comprehensive regional search strategy design.

---

## 🌐 Institutional Resources

- **BVS Regional Portal:** https://bvsalud.org
- **DeCS Descriptor Database:** https://decs.bvsalud.org
- **Official BVS Search Tutorial:** https://bvsalud.org/searchtutorial/EN/index.html
- **BIREME/PAHO:** https://www.paho.org/bireme

---

## 📋 License

This repository is offered under [Creative Commons Attribution 4.0 International] (https://creativecommons.org/licenses/by/4.0/). You are free to share, adapt, and use this material for educational, clinical, and research purposes.

---
## 🤝 Contributing & Feedback

Missing a critical reference? 📌 Found an inaccuracy? 🔧 This repository is living documentation and welcomes evidence-based corrections and additions. Please open an issue or submit a pull request if you identify references that strengthen the methodological grounding of this tutorial.

**Note on Text Refinement:** This documentation was created with computational assistance from Claude (Anthropic) to ensure clarity, consistency, and originality of the technical content while maintaining accuracy of the information architecture and search methodology.

---

<p align="center">
  <em>Decentralizing evidence synthesis from North to South.</em><br/>
  Made in Catanduva, SP — Wilson Falco, MD
</p>
