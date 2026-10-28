# Search Queries for Job Scraper

<!-- Populated by /setup for Niladribihari Mohanta - Indian market, English-language postings. -->

## Installed portal CLIs (primary for `/scrape`)

`/scrape` discovers every portal skill under `.agents/skills/*/SKILL.md` and runs its CLI first.

**Enabled for this market:**
- `linkedin-search` - LinkedIn Jobs
- `freehire-search` - freehire aggregator

**Installed but disabled** (wrong market - leave off unless you start targeting Denmark):
`jobindex-search`, `jobbank-search`, `jobdanmark-search`, `jobnet-search`.

The `site:` query templates in this file are the **WebSearch fallback** - for Indian portals without a CLI (Naukri, Instahyre, Cutshort, Foundit, Wellfound), company career pages, or when a CLI fails.

**Language scope:** all postings are English-language. The candidate's working language is English only; Hindi and Odia are spoken-only and should never drive a query. Never generate Hindi- or Odia-language queries for this candidate.

## Search Sites

Primary (country-agnostic CLIs, enabled):
- **linkedin.com/jobs** - primary board; filter to India, or city-by-city
- **freehire** - aggregator CLI

Secondary (Indian boards via WebSearch `site:` fallback):
- **naukri.com** - largest Indian general board
- **instahyre.com** - curated tech-only board, strong for backend/startup roles
- **cutshort.io** - startup-focused
- **foundit.in** - general board (formerly Monster India)
- **wellfound.com** (AngelList) - startups, often remote-first
- **Company career pages** - direct `site:` searches for target companies, plus Greenhouse/Lever/Ashby/Workday hosts

## Role Type Note

The candidate's own headline is "Backend Developer | Distributed Systems & Generative AI". Priority 1 therefore spans **two** connected functions rather than one. They converge on the same underlying work pattern (TypeScript/Node backend infrastructure, queues, LLM integration), so they are written as sub-categories of a single top priority rather than separate tiers.

## Query Categories

### Priority 1a: Backend / Distributed Systems

The strongest match: TypeScript/Node backend with queue, infrastructure and systems depth.

```
site:naukri.com "Backend Engineer" "Node.js" (Visakhapatnam OR Hyderabad OR Bengaluru)
site:naukri.com "Backend Developer" "TypeScript" (Bengaluru OR Hyderabad)
site:linkedin.com/jobs "Backend Engineer" TypeScript India
site:linkedin.com/jobs "Senior Backend Engineer" "Node.js" India
site:instahyre.com "Backend Engineer" "Redis" "PostgreSQL"
site:cutshort.io "Backend Developer" "BullMQ" OR "Redis" OR "Node.js"
site:wellfound.com "Backend Engineer" "TypeScript" remote
"distributed systems engineer" "Node.js" India
```

### Priority 1b: AI / GenAI Engineering

Applied AI roles that sit on top of real backend work: RAG, agents, LLM integration.

```
site:naukri.com "AI Engineer" OR "GenAI Engineer" "LangChain" (Bengaluru OR Hyderabad OR Remote)
site:linkedin.com/jobs "AI Engineer" "RAG" "TypeScript" India
site:linkedin.com/jobs "GenAI Engineer" "LangGraph" OR "LangChain" India
site:instahyre.com "AI Engineer" "Python" OR "TypeScript" "LLM"
site:wellfound.com "AI Engineer" "RAG" remote
"LLM engineer" "Node.js" OR "TypeScript" India
```

### Priority 2: Platform / Infrastructure Engineering

Adjacent, and a strong match for the self-hosting, Coolify/Hetzner, CI/CD side of the Baatasari work.

```
site:naukri.com "Platform Engineer" "Docker" "CI/CD" (Bengaluru OR Hyderabad)
site:linkedin.com/jobs "DevOps Engineer" "Node.js" India
site:instahyre.com "Infrastructure Engineer" "PostgreSQL" "Redis"
site:cutshort.io "Platform Engineer" "Docker" "AWS" OR "GCP"
"site reliability engineer" "Node.js" India
```

### Priority 3: Full-stack (Startup)

Smaller startups where one engineer owns both halves. The Next.js/React work at Baatasari supports this honestly.

```
site:naukri.com "Full Stack Developer" "Next.js" "Node.js" (Bengaluru OR Hyderabad OR Remote)
site:cutshort.io "Full Stack Engineer" "TypeScript" "React"
site:wellfound.com "Full Stack Engineer" "Next.js" remote
site:instahyre.com "Full Stack Engineer" "Node.js" "PostgreSQL"
```

### Priority 4: Broader Technical (Wider Net)

Wider net: general backend and software engineering roles where the stack overlaps even if the title differs.

```
site:naukri.com "Software Engineer" "TypeScript" (Bengaluru OR Hyderabad)
site:linkedin.com/jobs "Software Engineer" "PostgreSQL" "Redis" India
site:foundit.in "Backend Developer" "Node.js" (Visakhapatnam OR Hyderabad)
site:naukri.com "Software Development Engineer" "Node.js" India
"technical consultant" backend India remote
```

## Adjacent Role Suggestions

Roles worth watching that the candidate may not have considered, all honestly supported by the current profile:

- **Solutions Engineer / Forward Deployed Engineer** - the LLM-integration plus systems-ownership combination is exactly this role at AI product companies. Search: `"solutions engineer" "LLM" OR "AI" India`.
- **Developer Tooling / DevEx Engineer** - the Project Intelligence Agent is a developer-tooling product; the ATS/Playwright crawler is adjacency. Search: `"developer tools" engineer "TypeScript" India`.
- **Technical Support Engineer (Tier 3) at AI infrastructure companies** - a common entry path into AI-infra companies for people with strong debugging depth. Search: `"technical support engineer" "LLM" OR "vector database" India`.

## Location Filter

The candidate is open to relocation anywhere in India and works remotely well. Tiers:

- **Ideal:** Visakhapatnam (home), Remote (India), Hyderabad, Bengaluru
- **Acceptable:** Chennai, Pune, Gurugram, Noida, Mumbai
- **Borderline:** other Indian metros - acceptable with relocation if the role is strong
- **Too far:** on-site outside India without visa sponsorship

When a posting's location is listed as a city but the role is remote or hybrid for India, treat it as **Ideal**.

## Language Filter

Working language is English only. Hindi and Odia are spoken-only at conversational level - they are **not** working languages for written output.

Apply `04-job-evaluation.md`'s Language Gate:
- A posting requiring any language not on the candidate's table (German, French, Spanish, Japanese, etc.) → **exclude**
- A posting requiring **written** Hindi or Odia → **flag**, and for roles where written work in those languages is structural, treat the flag as a soft fail
- A posting requiring **spoken** Hindi or Odia at conversational level → **pass**
- Postings simply *written* in a language the candidate doesn't work in, that don't require it on the job → fine, but flag for readability

## Date Filter

Only include jobs posted within the last 14 days, or with an application deadline that has not yet passed. If a posting date cannot be determined, include it but flag as "date unknown".

## Seniority Note

The candidate has ~2 years of professional backend experience (Dec 2024 onward) plus a strong independent-project portfolio. Search and score accordingly:
- **Include:** "Backend Engineer", "Software Engineer", plain titles with no seniority prefix, "Engineer II"
- **Include with lower weight:** "Senior Backend Engineer" where the requirement is 2-4 years
- **Exclude:** titles requiring 5+ years, "Staff", "Principal", "Lead" with people-management scope

## Adapting Queries

If the user specifies a focus area, select queries from the matching category and also generate 2-3 custom queries for that focus. For example:
- `/scrape remote` → the Remote-tagged queries plus `site:wellfound.com` startup searches
- `/scrape ai` → Priority 1b plus the Developer Tooling / Solutions Engineer adjacent searches
- `/scrape bengaluru` → all categories filtered to Bengaluru
