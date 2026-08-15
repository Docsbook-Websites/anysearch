---
title: Tags & Params — AnySearch Domain Taxonomy
description: Every tag and sub-domain parameter AnySearch routes to, from academic and finance to security and travel.
---

# Tags & Params

The `tag` field routes your query to a specific data source in the form `{domain}.{sub_domain}` (e.g. `code.doc`). AI agents using MCP or Skill handle this routing automatically — this reference is for direct API integrations that want to select a source explicitly.

Domains: All · academic · agriculture · business · code · energy · environment · film · finance · gaming · general · health · ip · legal · resource · security · social_media · travel

<!-- widget:accordion -->

### academic.biomedical

Biomedical and clinical literature search covering MEDLINE journals with MeSH terms and PMC full-text links.

| Parameter | Required | Description |
|---|---|---|
| `date_type` | Optional | Date filter dimension. Values: `pdat` (publication date, default), `edat` (entry date), `mdat` (modification date) |
| `field` | Optional | Query field restriction. Values: `tiab` (title+abstract, default), `title`, `author`, `journal`, `mesh`, `all` |
| `has_pdf` | Optional | Whether to return only publications with PDF full text |
| `open_access` | Optional | Whether to return only open access publications |
| `sort` | Optional | Sort order: `relevance` (default), `date`, `pub_date`, `author`, `journal`, `cited` |
| `source` | Optional | Data sub-database filter: `MED`, `PMC`, `PPR`, `AGR`, `PAT`, etc. |
| `year_from` / `year_to` | Optional | Publication year/date bounds. Format `YYYY` or `YYYY/MM/DD` |

### academic.citation

Citation relationships, citation counts, and reference lists by DOI or title.

| Parameter | Required | Description |
|---|---|---|
| `id` | Required | Persistent identifier — DOI, PMID, ISSN, ISBN, ORCID, OMID, or OCI, without type prefixes |
| `id_type` | Optional | `doi`, `pmid`, `issn`, `isbn`, `orcid`, `omid` — auto-detected when empty |
| `op` | Optional | `metadata` (default), `citations`, `references`, `citation-count`, `reference-count`, `author`, `editor`, `venue-citation-count`, `citation` |
| `category` | Optional | Subject category, comma-separated (Computer Science, Medicine, Biology, Physics, ...) |
| `type` | Optional | Document/publication type filter |
| `venue` | Optional | Journal/conference name (NeurIPS, ICML, Nature, Science, ...) |
| `min_citations` | Optional | Minimum citation count |
| `open_access` | Optional | `true` / `false` |
| `filter` / `sort` | Optional | RAMOSE filter and sort expressions |
| `year_from` / `year_to` | Optional | Publication date bounds |

### academic.dataset

Research datasets, open-source code, and scientific software across Zenodo, Dryad, and Figshare.

| Parameter | Required | Description |
|---|---|---|
| `client_id` | Optional | Repository identifier, e.g. `cern.zenodo`, `figshare.ars`, `bl.dryad` |
| `resource_type` | Optional | `Dataset`, `Software`, `Text`, `Image`, `Audiovisual`, `Collection`, `InteractiveResource` |
| `year_from` / `year_to` | Optional | Publication year bounds |

### academic.preprint

Preprint search across CS, physics, math, biology, and economics for cutting-edge research.

| Parameter | Required | Description |
|---|---|---|
| `doi` | Optional | Direct DOI lookup |
| `field` | Optional | `ti`, `au`, `abs`, `co`, `jr`, `cat`/`category`, `all` (default) |
| `language` | Optional | ISO language code |
| `open_access` | Optional | `true` / `false` |
| `sort` / `order` | Optional | `relevance` (default), `date_submitted`, `date_updated`; `asc`/`desc` |
| `type` | Optional | Document/publication type filter |
| `year_from` / `year_to` | Optional | Publication year bounds |

### academic.search

Cross-discipline paper search by keyword, title, author, or institution with metadata and open access links.

| Parameter | Required | Description |
|---|---|---|
| `category` | Optional | Subject category, comma-separated |
| `doi` | Optional | Direct DOI lookup |
| `min_citations` | Optional | Minimum citation count |
| `open_access` | Optional | `true` / `false` |
| `sort` | Optional | `cited_by_count`, `publication_date`, `publication_year`, `relevance_score`, `display_name` (+ `:asc`/`:desc`) |
| `type` | Optional | Document/publication type filter |
| `venue` | Optional | Journal/conference name |
| `year_from` / `year_to` | Optional | Publication year bounds |

### agriculture.fao

FAO global agriculture statistics covering production, trade, and food prices.

| Parameter | Required | Description |
|---|---|---|
| `date_start` | Optional | Year, e.g. `2023` |
| `domain` | Optional | `production` / `trade` / `prices` |
| `keyword` | Optional | e.g. `wheat production`, `rice trade` |
| `location` | Optional | Region name |
| `type` | Optional | `GlobalAgriculture` |

### business.company

Company registration, shareholder structure, executives, and business status across global financial entities.

| Parameter | Required | Description |
|---|---|---|
| `keyword` | Optional | Company name, credit code, LEI code, or ticker |
| `type` | Optional | `ChineseEnterprise` / `GlobalLEI` / `USFilings` |

### business.jobs

Global job listings by position, skills, location, and salary across 16+ countries.

| Parameter | Required | Description |
|---|---|---|
| `keyword` | Optional | e.g. `software engineer`, `python` |
| `location` | Optional | City / region / country |
| `salary_min` | Optional | Minimum annual salary (USD) |
| `type` | Optional | `GeneralJobs` / `RemoteJobs` / `USFederalJobs` |

### business.people

Business contacts search by title, company, and location with business email and professional background.

| Parameter | Required | Description |
|---|---|---|
| `keyword` | Optional | Search keyword or company domain |
| `location` | Optional | Location filter |
| `seniority` | Optional | `executive` / `senior` / `entry` |
| `title` | Optional | e.g. `CTO`, `Head of Engineering` |
| `type` | Optional | `PeopleSearch` / `EmailLookup` |

### business.trade

International trade statistics by commodity code, country, and time period for imports and exports.

| Parameter | Required | Description |
|---|---|---|
| `date_start` | Optional | Year, e.g. `2023` |
| `flow` | Optional | `export` / `import` / `both` |
| `hs_code` | Optional | HS code, 2/4/6/10 digits |
| `location` | Optional | Partner country name |
| `type` | Optional | `GlobalBilateralTrade` / `USImportExport` |

### code.doc

Query developer documentation and code examples by library name and topic across npm, PyPI, and Cargo ecosystems.

| Parameter | Required | Description |
|---|---|---|
| `library` | Required | Library or framework name, e.g. `react`, `express` |

### code.snippet

Search real code implementations across 1M+ public GitHub repositories with regex and language filtering.

| Parameter | Required | Description |
|---|---|---|
| `lang` | Optional | Programming language filter, e.g. `TypeScript`, `Python` |
| `path` | Optional | File path pattern, e.g. `src/components/` |
| `repo` | Optional | GitHub repository, e.g. `facebook/react` |

### energy.electricity

Electricity market data: prices, generation mix, demand, and carbon intensity across 200+ countries.

| Parameter | Required | Description |
|---|---|---|
| `date_start` / `date_end` | Optional | Date range |
| `location` | Optional | Region name |
| `metric` | Optional | `price` / `generation` / `emissions` / `demand` / `capacity` |
| `type` | Optional | `EUElectricity` / `AustralianElectricity` / `USEnergyData` / `GlobalElectricity` |

### energy.production

Energy production and consumption stats for oil, gas, coal, nuclear, and renewables including output and inventory.

| Parameter | Required | Description |
|---|---|---|
| `date_start` | Optional | Start date |
| `frequency` | Optional | `monthly` / `annual` / `quarterly` |
| `keyword` | Optional | e.g. `crude oil production` |
| `location` | Optional | Region name |
| `type` | Optional | `USEnergyData` |

### environment.aqi

Real-time global air quality index (AQI) and PM2.5/PM10 data by city name.

| Parameter | Required | Description |
|---|---|---|
| `location` | Optional | Zip code, coordinates, or city name |
| `type` | Optional | `GlobalAirQuality` |

### film.torrent

Search film and music BT torrent resources with magnet links, file size, and seeder count. No parameters.

### finance.calendar

Earnings dates, guidance, economic data releases, and IPO schedules.

| Parameter | Required | Description |
|---|---|---|
| `type` | Required | `earnings` / `dividends` / `ipos` / `economic` |
| `period` | Optional | Forward-looking time range, default `7d` |
| `symbol` | Optional | Stock ticker, used when `type=dividends` |

### finance.fundamental

Financial statements, valuation metrics, analyst ratings, shareholder structure, and SEC filings.

| Parameter | Required | Description |
|---|---|---|
| `type` | Required | `overview` / `income` / `balance` / `cashflow` / `indicator` / `holder` |
| `cn_code` | Required for A-shares | Required when `type=income/balance/cashflow/indicator/holder` |
| `symbol` | Required for `overview` | International ticker, e.g. `AAPL` |
| `period` | Optional | Used only for `type=holder`, default `1y` |

### finance.macro

Macroeconomic indicators: GDP, CPI, PMI, interest rates, money supply, and social financing.

| Parameter | Required | Description |
|---|---|---|
| `type` | Required | `gdp` / `cpi` / `fed_funds` / `treasury` / `unemployment` / `nonfarm` / `shibor` / `lpr` / `money_supply` / `social_finance` |
| `period` | Optional | Data range, default varies by type |

### finance.news

Global financial news, company announcements, and broker research summaries.

| Parameter | Required | Description |
|---|---|---|
| `type` | Required | `general` / `stock` / `flash` / `announcement` |
| `cn_code` | Optional | A-share ticker, used with `type=announcement` |
| `news_src` | Optional | Chinese flash news source, used with `type=flash` |
| `period` | Optional | Query time range |
| `symbol` | Optional | International ticker, used with `type=stock` |

### finance.quote

Real-time and historical quotes for stocks, forex, crypto, commodities, indices, and ETFs.

| Parameter | Required | Description |
|---|---|---|
| `type` | Required | `stock` / `forex` / `crypto` / `commodity` / `index` / `etf` |
| `cn_code` | Required for CN markets | Chinese market symbol |
| `symbol` | Required for intl markets | International market symbol |
| `period` | Optional | Historical range, e.g. `7d`, `30d`, `1y` |

### finance.screen

Screen stocks by market cap, PE, dividend yield, sector, and country (international markets only).

| Parameter | Required | Description |
|---|---|---|
| `type` | Required | `stock` / `etf` |
| `country` | Optional | ISO 3166-1 alpha-2 code, used with `type=stock` |
| `sector` | Optional | GICS sector, used with `type=stock` |

### gaming.esports

Esports player stats, rankings, champion attributes, and item data for League of Legends and other titles.

| Parameter | Required | Description |
|---|---|---|
| `type` | Required | `player` / `ranked` / `mastery` / `live_game` / `match_detail` / `leaderboard` / `champion` / `item` / `champion_rotation` |
| `game_name` | Required for player queries | Game ID, optionally with `#tagLine` |
| `region` | Required for player queries | Server region, e.g. `kr`, `na`, `euw` |
| `champion` / `division` / `match_id` / `queue` / `tier` | Optional | Filter and detail parameters — see field descriptions in the API |

### gaming.store

Steam game real-time prices, discounts, user ratings, online player count, and achievements with China region pricing. No parameters.

### general.general

General search. No parameters.

### health.drug

Drug labels, adverse reactions, interactions, and recalls by drug name, NDC code, or barcode.

| Parameter | Required | Description |
|---|---|---|
| `type` | Required | `name` / `ndc` / `upc` |

### health.stats

Global public health statistics across 194 countries: mortality, morbidity, life expectancy, disease burden. No parameters.

### health.trial

Clinical trial registry search by disease, drug, phase, and region with enrollment criteria and status. No parameters.

### ip.global

Global patent aggregation and family tracing via EPO DOCDB/INPADOC, covering 100+ countries with legal status.

| Parameter | Required | Description |
|---|---|---|
| `applicant` | Optional | Applicant/organization name filter |
| `date_start` | Optional | Publication/application date start |
| `ipc` | Optional | IPC/CPC classification filter |
| `keyword` | Optional | Search keyword |
| `type` | Optional | `GlobalPatent` |

### legal.case

Court decisions and legal opinions, searchable by keyword, case name, court, and date across CN, US, CA, and ECHR.

| Parameter | Required | Description |
|---|---|---|
| `case_id` | Optional | CanLII case identifier for exact lookup |
| `database_id` | Optional | Target court database code |
| `doc_type` | Optional | Document type — opinions, dockets, oral arguments, or ECHR judgment types |
| `language` | Optional | `en` (default) / `fr` |
| `respondent` | Optional | Respondent country, ISO 3166-1 alpha-3 |
| `service` | Optional | Search service, overrides tag-based routing |

### legal.legislation

Legislation tracking: bill status, voting records, and committee deliberations for US Congress (international only).

| Parameter | Required | Description |
|---|---|---|
| `congress` | Optional | US Congress session number, e.g. `118`, `119` |

### legal.statute

Legal text lookup for laws, administrative regulations, and regulatory rules with article positioning and version history.

| Parameter | Required | Description |
|---|---|---|
| `agency` | Optional | Publishing agency slug (EPA, SEC, FDA, FCC, DOE, DOL) |
| `collection` | Optional | `FR` / `CFR` / `USCODE` / `BILLS` / `PLAW` / `USCOURTS` / `CREC` / `STATUTE` |
| `date_from` / `date_to` | Optional | Effective or publication date bounds |
| `doc_type` | Optional | Type code, meaning varies by jurisdiction |
| `historical` | Optional | Include historical revision versions |
| `language` | Optional | ISO 639-1 code |
| `title` | Optional | CFR Title number |

### resource.image

Professional photography, diverse stock photos, SVG, illustrations, and vector graphics. No parameters.

### security.intel

Threat intelligence for IP, domain, URL, or file hash with historical malicious records and IOC indicators.

| Parameter | Required | Description |
|---|---|---|
| `ioc` | Required | Indicator of compromise: domain, IP, URL, or file hash |

### security.noise

Check if an IPv4 address is internet background scanning noise or a known legitimate service.

| Parameter | Required | Description |
|---|---|---|
| `ip` | Required | Single IPv4 address, e.g. `8.8.8.8` |

### security.scan

Submit a file hash, URL, IP, or domain to a 70+ security vendor aggregate scan.

| Parameter | Required | Description |
|---|---|---|
| `ioc` | Required | Indicator of compromise to scan (MD5/SHA1/SHA256 supported for file hashes) |

### security.vuln

CVE vulnerability details with CVSS scores, affected versions, patch links, and exploitation status.

| Parameter | Required | Description |
|---|---|---|
| `type` | Required | `cve` / `commit` / `package` |
| `value` | Required | Value matching `type`: CVE ID, 40-char hex, or `ecosystem:name@version`. Comma-separated for batch |

### social_media.social_media

Social media information search and retrieval.

| Parameter | Required | Description |
|---|---|---|
| `keyword` | Optional | Search keyword, takes precedence over `query` |
| `region` | Optional | Region filter, only for `type=weibo_hot` |
| `type` | Optional | `weibo` / `weibo_hot` / `zhihu` / `zhihu_hot` / `x_top` / `x_latest` / `x_media` / `x_people` / `x_lists` / `reddit_post` / `reddit_community` / `reddit_comment` / `reddit_media` / `reddit_people` / `linkedin_people` / `linkedin_jobs` / `linkedin_company` / `linkedin_posts` / `wechatmp` |

### travel.flight

Search global flight tickets by origin, destination, and date with baggage and price comparison.

| Parameter | Required | Description |
|---|---|---|
| `arrival` / `departure` | Required | Airport IATA 3-letter codes |
| `date` | Required | Departure date |
| `adults` / `children` / `infants` | Optional | Passenger counts |
| `cabin_class` | Optional | `Economy` / `Business` / `First` / `PremiumEconomy` |
| `currency` | Optional | Currency code |
| `return_date` | Optional | Return date, empty = one-way |

### travel.flight_status

Real-time flight departure/arrival status, gate info, delay information, and airport boards.

| Parameter | Required | Description |
|---|---|---|
| `arrival` / `departure` | Required | Airport IATA 3-letter codes |
| `date` | Required | Query date |
| `flight_number` | Optional | e.g. `DL47`, `CA981` |

<!-- /widget -->

## Related

- [Endpoints](./endpoints.md) — Where `tag` and `params` are sent
- [Quick Start](../get-started/quickstart.md) — A minimal working request
