# pharma-mcp

**MCP server for clinical and pharmaceutical data.**

Gives Claude and any MCP-compatible AI agent direct access to:

- **ClinicalTrials.gov** — search and retrieve trial protocols, endpoints, eligibility criteria
- **PubMed** — literature search with MeSH terms, full abstracts, citation formatting
- **FDA openFDA** — drug labels, approved indications, warnings, boxed warnings
- **FDA FAERS** — adverse event reports with patient demographics and outcomes
- **ICH Guidelines** — structured summaries of E3, E6, E9, M4, Q1A, and more

No API keys required. All data sources are public. Runs locally in under 60 seconds.

---

## Tools

| Tool | Description |
|------|-------------|
| `search_clinical_trials` | Search ClinicalTrials.gov by condition, drug, or sponsor |
| `get_trial_details` | Full protocol details by NCT ID |
| `search_pubmed` | PubMed literature search with MeSH, Boolean, date filters |
| `get_pubmed_abstract` | Full abstract + metadata by PMID |
| `search_fda_drugs` | FDA drug label search — indications, warnings, dosage forms |
| `get_fda_adverse_events` | FAERS adverse event reports by drug and/or reaction |
| `get_ich_guideline` | ICH guideline summaries by code (E3, E6, M4…) or topic |
| `format_citation` | Vancouver, APA, or AMA citation from a PMID |

---

## Quickstart

### Install

```bash
git clone https://github.com/pubspro/pharma-mcp.git
cd pharma-mcp
npm install
```

### Add to Claude Desktop

Edit `~/Library/Application Support/Claude/claude_desktop_config.json` (macOS) or `%APPDATA%\Claude\claude_desktop_config.json` (Windows):

```json
{
  "mcpServers": {
    "pharma-mcp": {
      "command": "node",
      "args": ["/absolute/path/to/pharma-mcp/src/index.js"]
    }
  }
}
```

Restart Claude Desktop. The tools appear automatically.

### Add to Claude Code

```bash
claude mcp add pharma-mcp node /absolute/path/to/pharma-mcp/src/index.js
```

---

## Example prompts

Once connected, ask Claude:

```
Search ClinicalTrials.gov for Phase 3 recruiting trials for non-small cell lung cancer involving osimertinib.
```

```
Find the 10 most recent PubMed papers on GLP-1 receptor agonists and cardiovascular outcomes. Format citations in Vancouver style.
```

```
Get the FDA label for semaglutide — what are the boxed warnings and contraindications?
```

```
What does ICH E3 require for a clinical study report? Which sections are mandatory?
```

```
Pull adverse event reports for dupilumab involving anaphylaxis from FAERS.
```

---

## Use cases

**Medical writers and publications teams**
- Rapid literature gap analysis for advisory boards and manuscripts
- Auto-format reference lists from PubMed searches
- Check ICH E3 requirements mid-draft without switching tabs

**Regulatory affairs**
- Search FDA labels for labeling precedent
- Check FAERS signal for benefit-risk narratives
- Retrieve ICH guideline requirements for CTD modules

**Clinical development**
- Competitive landscape searches across ClinicalTrials.gov
- Identify comparable trial designs and endpoints

**AI agent pipelines**
- Chain pharma-mcp tools with other MCP servers for autonomous regulatory research workflows

---

## Data sources

All data retrieved in real time from official public APIs — no data stored, no API keys required:

- [ClinicalTrials.gov API v2](https://clinicaltrials.gov/data-api/api)
- [NCBI E-utilities (PubMed)](https://www.ncbi.nlm.nih.gov/books/NBK25501/)
- [openFDA API](https://open.fda.gov/apis/)
- [ICH Guidelines](https://www.ich.org/page/guidelines)

---

## Requirements

- Node.js 18+
- npm

---

## Roadmap

- [ ] EMA EPAR search
- [ ] DailyMed full prescribing information
- [ ] GPP4 / ICMJE authorship criteria checker
- [ ] ClinVar genetic variant lookup

PRs and issues welcome.

---

## License

MIT
