# Zotero registration list (reference list items 1–14 + 2 candidates)

Prepared 5 Oct 2026. Source list: `reference_list_verified.md` in the academic-writing-2026-2027 repo.

**How the fields were filled.** Every value below was checked against an authoritative record (Crossref DOI record, arXiv abstract page, USENIX/NIST/ENISA official pages, the publisher's PDF front matter, or the GitHub repo). Field names are Zotero's own, so you can type them straight into the item pane.

- **⚠** = could not be confirmed from an official record. Left blank or marked; please check before citing.
- **Fields not listed** (Abstract, Language, Library Catalog, Call Number, Archive…) can stay empty.
- **Accessed**: fill in the date you actually open the page; Harvard UL requires it for online sources.
- **Faster route**: for items with a DOI or arXiv ID, Zotero's *Add Item by Identifier* (magic-wand button) fills most fields automatically. Then compare against this list. An importable file is alongside: `zotero_reference_list.ris` (File → Import). It holds 15 items: everything except no. 11, MITRE Evaluations, whose page you still need to choose, and the ENISA 2025 alternative. After importing, check the item type of the preprints (3, 5, 9, 10). RIS has no dedicated preprint type, so change them to **Preprint** if Zotero imports them as Manuscript.
- **DOI/ISBN on Report items**: if your Zotero version shows no DOI or ISBN field for a Report, put them in **Extra** as `DOI: …` / `ISBN: …` on separate lines. Zotero passes these to the citation style.
- **Corporate authors** (ENISA, Red Canary, MITRE, SCYTHE): click the small "switch to single field" icon next to the author box and enter the organisation name as one field.

---

## Layer A: Theory and framework foundations

### 1. Strom et al. (2018, rev. 2020): MITRE ATT&CK: Design and Philosophy
| Field | Value |
|---|---|
| Item Type | **Report** |
| Title | MITRE ATT&CK®: Design and Philosophy |
| Author (Last, First) | Strom, Blake E · Applebaum, Andy · Miller, Doug P. · Nickels, Kathryn C. · Pennington, Adam G. · Thomas, Cody B. |
| Report Type | Technical Report |
| Institution | The MITRE Corporation |
| Place | McLean, VA |
| Date | 2020-03 |
| URL | https://www.mitre.org/sites/default/files/2021-11/prs-19-01075-28-mitre-attack-design-and-philosophy.pdf |
| Accessed | 2026-09-28 |
| Short Title | MITRE ATT&CK |
| Language | English |
| Extra | Originated out of a project to document and categorize post compromise adversary tactics, techniques and procedures |

**Harvard:** Strom, B. E., Applebaum, A., Miller, D. P., Nickels, K. C., Pennington, A. G., & Thomas, C. B. (2020). *MITRE ATT&CK®: Design and Philosophy*. Online. McLean, VA: The MITRE Corporation. Available at: https://www.mitre.org/sites/default/files/2021-11/prs-19-01075-28-mitre-attack-design-and-philosophy.pdf [Accessed 28th September 2026].

Notes: the cover of the PDF also gives the document number **MP180360R1** (fits the Report Number field) and the original July 2018 publication date. Neither is in the Zotero record yet.

### 2. Alford, Lawrence & Kouremetis (2022): CALDERA: A Red-Blue Cyber Operations Automation Platform
| Field | Value |
|---|---|
| Item Type | **Report** |
| Title | CALDERA: A Red-Blue Cyber Operations Automation Platform |
| Author (Last, First) | Alford, Ron · Lawrence, Dean · Kouremetis, Michael |
| Report Number | 21-03192-1 |
| Report Type | Conference paper |
| Institution | The MITRE Corporation |
| Place | Singapore |
| Date | 2022 |
| URL | https://icaps22.icaps-conference.org/demos/ICAPS_2022_paper_375.pdf |
| Accessed | 2026-09-29 |
| Short Title | CALDERA |
| Language | English |

**Harvard:** Alford, R., Lawrence, D., & Kouremetis, M. (2022). *CALDERA: A Red-Blue Cyber Operations Automation Platform*. Online. Singapore: The MITRE Corporation. Available at: https://icaps22.icaps-conference.org/demos/ICAPS_2022_paper_375.pdf [Accessed 29th September 2026].

Notes: this is the ICAPS 2022 demo paper listed under item 2 as "related". The repo list's main item 2, Applebaum et al., "Intelligent, Automated Red Team Emulation", ACSAC 2016, pp. 363–373, DOI 10.1145/2991079.2991111, is a different paper and is not registered in Zotero.

---

## Layer B: Core: detection coverage / evaluation

### 3. Roy et al. (2023): SoK: The MITRE ATT&CK Framework in Research and Practice
| Field | Value |
|---|---|
| Item Type | **Preprint** |
| Title | SoK: The MITRE ATT&CK Framework in Research and Practice |
| Author (Last, First) | Roy, Shanto · Panaousis, Emmanouil · Noakes, Cameron · Laszka, Aron · Panda, Sakshyam · Loukas, George |
| Repository | arXiv |
| Archive ID | arXiv:2304.07411 |
| Date | 2023-04-14 |
| DOI | 10.48550/arXiv.2304.07411 |
| URL | https://arxiv.org/abs/2304.07411 |
| Short Title | SoK: The MITRE ATT&CK Framework |
| Rights | arXiv non-exclusive distribution licence 1.0 |
| Extra | Preprint, not peer reviewed. Only v1 exists; no journal reference on arXiv. |

**Harvard:** Roy, S., Panaousis, E., Noakes, C., Laszka, A., Panda, S., & Loukas, G. (2023). *SoK: The MITRE ATT&CK Framework in Research and Practice*. Preprint. arXiv:2304.07411. Available at: https://arxiv.org/abs/2304.07411 [Accessed 5th October 2026].

Notes: your list says "et al." after Panaousis. There are **6 authors**, Roy is first. No peer-reviewed version was found (arXiv has no journal ref; a Crossref search found nothing). I could not reach DBLP from here, so do one last check there before submission.

### 4. ★Anchor★ Al-Sada, Sadighian & Oligeri (2024): MITRE ATT&CK: State of the Art and Way Forward
| Field | Value |
|---|---|
| Item Type | **Journal Article** |
| Title | MITRE ATT&CK: State of the Art and Way Forward |
| Author | Al-Sada, Bader · Sadighian, Alireza · Oligeri, Gabriele |
| Publication | ACM Computing Surveys |
| Volume | 57 |
| Issue | 1 |
| Pages | 1–37 |
| Date | 2024-10-07 |
| Journal Abbr | ACM Comput. Surv. |
| DOI | 10.1145/3687300 |
| ISSN | 0360-0300 (print) · 1557-7341 (online) |
| URL | https://dl.acm.org/doi/10.1145/3687300 |
| Short Title | MITRE ATT&CK |
| Rights | © ACM (standard ACM copyright) |
| Extra | ⚠ ACM article number not confirmed (Crossref record gives pages 1–37 only). Earlier arXiv version: arXiv:2308.14016 |

**Harvard:** Al-Sada, B., Sadighian, A., & Oligeri, G. (2024). 'MITRE ATT&CK: State of the Art and Way Forward'. *ACM Computing Surveys*, 57(1), pp. 1–37. Available at: https://doi.org/10.1145/3687300 [Accessed 5th October 2026].

Notes: your list had no authors. Authors come from the Crossref record.

### 5. Jiang et al. (2025): MITRE ATT&CK Applications in Cybersecurity and The Way Forward
| Field | Value |
|---|---|
| Item Type | **Preprint** |
| Title | MITRE ATT&CK Applications in Cybersecurity and The Way Forward |
| Author | Jiang, Yuning · Meng, Qiaoran · Shang, Feiyang · Oo, Nay · Minh, Le Thi Hong · Lim, Hoon Wei · Sikdar, Biplab |
| Repository | arXiv |
| Archive ID | arXiv:2502.10825 |
| Date | 2025-02-15 |
| DOI | 10.48550/arXiv.2502.10825 |
| URL | https://arxiv.org/abs/2502.10825 |
| Short Title | MITRE ATT&CK Applications in Cybersecurity |
| Rights | arXiv non-exclusive distribution licence 1.0 |
| Extra | Preprint, not peer reviewed. 37 pages. |

**Harvard:** Jiang, Y., Meng, Q., Shang, F., Oo, N., Minh, L. T. H., Lim, H. W., & Sikdar, B. (2025). *MITRE ATT&CK Applications in Cybersecurity and The Way Forward*. Preprint. arXiv:2502.10825. Available at: https://arxiv.org/abs/2502.10825 [Accessed 5th October 2026].

Notes: your list had no authors. ⚠ "Le Thi Hong Minh" is a Vietnamese name; arXiv lists it in that order. Check the PDF author line to decide which part is the family name. No published version was found.

### 6. Karantzas & Patsakis (2021): EDR assessment against APT attack vectors
| Field | Value |
|---|---|
| Item Type | **Journal Article** |
| Title | An Empirical Assessment of Endpoint Detection and Response Systems against Advanced Persistent Threats Attack Vectors |
| Author | Karantzas, George · Patsakis, Constantinos |
| Publication | Journal of Cybersecurity and Privacy |
| Volume | 1 |
| Issue | 3 |
| Pages | 387–421 |
| Date | 2021-07-09 |
| Journal Abbr | J. Cybersecur. Priv. |
| DOI | 10.3390/jcp1030021 |
| ISSN | 2624-800X |
| URL | https://doi.org/10.3390/jcp1030021 |
| Short Title | An Empirical Assessment of Endpoint Detection and Response Systems |
| Rights | CC BY 4.0 |
| Extra | Publisher: MDPI (Basel). |

**Harvard:** Karantzas, G., & Patsakis, C. (2021). 'An Empirical Assessment of Endpoint Detection and Response Systems against Advanced Persistent Threats Attack Vectors'. *Journal of Cybersecurity and Privacy*, 1(3), pp. 387–421. Available at: https://doi.org/10.3390/jcp1030021 [Accessed 5th October 2026].

Notes: your list had no title or DOI. Both are now filled from Crossref.

### 7. Shen et al. (2024): Decoding the MITRE Engenuity ATT&CK Enterprise Evaluation
| Field | Value |
|---|---|
| Item Type | **Conference Paper** |
| Title | Decoding the MITRE Engenuity ATT&CK Enterprise Evaluation: An Analysis of EDR Performance in Real-World Environments |
| Author | Shen, Xiangmin · Li, Zhenyuan · Burleigh, Graham · Wang, Lingzhi · Chen, Yan |
| Proceedings Title | Proceedings of the 19th ACM Asia Conference on Computer and Communications Security |
| Conference Name | ASIA CCS '24: 19th ACM Asia Conference on Computer and Communications Security (Singapore, 1–5 July 2024) |
| Place | New York, NY, USA |
| Publisher | Association for Computing Machinery |
| Pages | 96–111 |
| Date | 2024-07 |
| DOI | 10.1145/3634737.3645012 |
| ISBN | 979-8-4007-0482-6 |
| URL | https://dl.acm.org/doi/10.1145/3634737.3645012 |
| Short Title | Decoding the MITRE Engenuity ATT&CK Enterprise Evaluation |
| Rights | CC BY 4.0 |
| Extra | Preprint: arXiv:2401.15878 |

**Harvard:** Shen, X., Li, Z., Burleigh, G., Wang, L., & Chen, Y. (2024). 'Decoding the MITRE Engenuity ATT&CK Enterprise Evaluation: An Analysis of EDR Performance in Real-World Environments'. In: *Proceedings of the 19th ACM Asia Conference on Computer and Communications Security (ASIA CCS '24)*, Singapore, 1–5 July 2024. New York, NY: Association for Computing Machinery, pp. 96–111. Available at: https://doi.org/10.1145/3634737.3645012 [Accessed 5th October 2026].

Notes: the full title is longer than in your list (adds "…in Real-World Environments"). Pages are from Crossref. The arXiv preprint shows "Article 237, 1–20", but that is preprint layout, so don't use it.

### 8. ★H2 core★ Uetz et al. (2024): You Cannot Escape Me
| Field | Value |
|---|---|
| Item Type | **Conference Paper** |
| Title | You Cannot Escape Me: Detecting Evasions of SIEM Rules in Enterprise Networks |
| Author | Uetz, Rafael · Herzog, Marco · Hackländer, Louis · Schwarz, Simon · Henze, Martin |
| Proceedings Title | 33rd USENIX Security Symposium (USENIX Security 24) |
| Conference Name | 33rd USENIX Security Symposium |
| Place | Philadelphia, PA |
| Publisher | USENIX Association |
| Pages | 5179–5196 |
| Date | 2024-08 |
| ISBN | 978-1-939133-44-1 |
| DOI | (none; USENIX papers have no DOI) |
| URL | https://www.usenix.org/conference/usenixsecurity24/presentation/uetz |
| Short Title | You Cannot Escape Me |
| Rights | Open access (USENIX) |
| Extra | Distinguished Artifact Award |

**Harvard:** Uetz, R., Herzog, M., Hackländer, L., Schwarz, S., & Henze, M. (2024). 'You Cannot Escape Me: Detecting Evasions of SIEM Rules in Enterprise Networks'. In: *33rd USENIX Security Symposium (USENIX Security 24)*, Philadelphia, PA, August 2024. USENIX Association, pp. 5179–5196. Available at: https://www.usenix.org/conference/usenixsecurity24/presentation/uetz [Accessed 5th October 2026].

Source: the official USENIX BibTeX on the presentation page.

### 9. ★H3★ Tyagi (2026): Static Quality Assessment of Sigma Detection Rules
| Field | Value |
|---|---|
| Item Type | **Preprint** |
| Title | Static Quality Assessment of Sigma Detection Rules: Framework and Empirical Evaluation |
| Author | Tyagi, Nishant |
| Repository | SSRN |
| Archive ID | 6823718 |
| Date | 2026-05-24 |
| DOI | 10.2139/ssrn.6823718 |
| URL | https://ssrn.com/abstract=6823718 |
| Short Title | Static Quality Assessment of Sigma Detection Rules |
| Extra | Preprint, not peer reviewed. 24 pages. Posted 5 Jun 2026. Author affiliation: Independent. Also deposited at Zenodo: 10.5281/zenodo.20371761 |

**Harvard:** Tyagi, N. (2026). *Static Quality Assessment of Sigma Detection Rules: Framework and Empirical Evaluation*. Preprint. SSRN. Available at: https://doi.org/10.2139/ssrn.6823718 [Accessed 5th October 2026].

Notes: SSRN gives the date written as 24 May 2026 and the posting date as 5 June 2026. Its suggested citation uses the 24 May date. The author is **independent**, not affiliated with a university. That is worth weighing if you rely on it for H3.

### 10. Shukla et al. (2025): RuleGenie
| Field | Value |
|---|---|
| Item Type | **Preprint** |
| Title | RuleGenie: SIEM Detection Rule Set Optimization |
| Author | Shukla, Akansha · Gandhi, Parth Atulbhai · Elovici, Yuval · Shabtai, Asaf |
| Repository | arXiv |
| Archive ID | arXiv:2505.06701 |
| Date | 2025-05-10 |
| DOI | 10.48550/arXiv.2505.06701 |
| URL | https://arxiv.org/abs/2505.06701 |
| Short Title | RuleGenie |
| Rights | arXiv non-exclusive distribution licence 1.0 |
| Extra | Preprint, not peer reviewed. |

**Harvard:** Shukla, A., Gandhi, P. A., Elovici, Y., & Shabtai, A. (2025). *RuleGenie: SIEM Detection Rule Set Optimization*. Preprint. arXiv:2505.06701. Available at: https://arxiv.org/abs/2505.06701 [Accessed 5th October 2026].

Notes: your list had no authors. No published version was found.

---

## Layer C: Standards / practice (grey literature)

### 11. MITRE ATT&CK Evaluations
| Field | Value |
|---|---|
| Item Type | **Web Page** |
| Title | ⚠ depends on which page you cite (see note) |
| Author | MITRE *(single-field / corporate)* |
| Website Title | MITRE ATT&CK Evaluations |
| URL | ⚠ see note |
| Accessed | *(your date)* |
| Extra | Grey literature |

**Harvard:** ⚠ Template until you choose the evaluation round: MITRE (Year). *[Title of the evaluation round page]*. Online. MITRE ATT&CK Evaluations. Available at: [URL of that page] [Accessed Day Month Year].

Notes: ⚠ **The URL in your list points to the wrong page.** `attack.mitre.org/resources/adversary-emulation-plans/` is the *adversary emulation plans* page, not the Evaluations. The Evaluations (methodology and results) are published on MITRE's separate Evaluations site. Cite the specific round you use, e.g. "Enterprise 2024", with its own page URL and title. I did not register a single page here because the right one depends on the round you read.

### 12. SCYTHE: Purple Team Exercise Framework (PTEF)
| Field | Value |
|---|---|
| Item Type | **Report** |
| Title | Purple Team Exercise Framework (PTEF) |
| Author | SCYTHE *(single-field / corporate)* |
| Report Type | Framework, version 4 |
| Institution | SCYTHE |
| Date | ⚠ not stated on the page or in the GitHub README |
| URL | https://github.com/scythe-io/purple-team-exercise-framework (also https://scythe.io/ptef) |
| Accessed | *(your date)* |
| Rights | MIT License (per the GitHub repository) |
| Extra | Grey literature. Version 4. |

**Harvard:** SCYTHE (n.d.). *Purple Team Exercise Framework (PTEF)*, version 4. Online. SCYTHE. Available at: https://github.com/scythe-io/purple-team-exercise-framework [Accessed 5th October 2026].

Notes: Report (not Software) because PTEF is a methodology document. For Harvard, use "n.d." unless you find a date in PTEFv4.md.

### 13. Olsen: Enterprise Purple Teaming: An Exploratory Qualitative Study
| Field | Value |
|---|---|
| Item Type | **Thesis** |
| Title | Enterprise Purple Teaming: An Exploratory Qualitative Study |
| Author | Olsen, Xena |
| Type | ⚠ Doctoral dissertation (degree not confirmed) |
| University | ⚠ not confirmed (see note) |
| Place | ⚠ |
| Date | ⚠ not confirmed |
| # of Pages | ⚠ |
| URL | https://www.proquest.com/docview/2658836337 |
| Extra | Practitioner resources: https://github.com/ch33r10/EnterprisePurpleTeaming |

**Harvard:** Olsen, X. (n.d. ⚠). *Enterprise Purple Teaming: An Exploratory Qualitative Study*. Doctoral dissertation. ⚠ [University]. Available at: https://www.proquest.com/docview/2658836337 [Accessed 5th October 2026].

Notes: **cite the dissertation, not the GitHub repo.** The repo is only a companion. ProQuest blocked my access, so the university, year and degree are not confirmed. The committee names in the repo, and the hosting on the WRLC repository (muislandora), suggest **Marymount University (Arlington, VA)**. That is an inference. Open the ProQuest link and copy the university, year and page count from there.

### 14. Red Canary: Threat Detection Report
| Field | Value |
|---|---|
| Item Type | **Report** |
| Title | 2026 Threat Detection Report |
| Author | Red Canary *(single-field / corporate)* |
| Institution | Red Canary |
| Place | ⚠ not confirmed |
| Date | 2026-03 |
| URL | https://redcanary.com/threat-detection-report/ |
| Accessed | *(your date)* |
| Extra | Grey literature. Annual. |

**Harvard:** Red Canary (2026). *2026 Threat Detection Report*. Online. Red Canary. Available at: https://redcanary.com/threat-detection-report/ [Accessed 5th October 2026].

Notes: the current edition is 2026, released in mid-March 2026. A press article of 25 Mar 2026 says it "came out last week", but I found no exact day. Your list gave no year. If you used an earlier edition, change the year in the title and date.

---

## Candidates (standards, to confirm)

### NIST SP 800-94
| Field | Value |
|---|---|
| Item Type | **Report** |
| Title | Guide to Intrusion Detection and Prevention Systems (IDPS) |
| Author | Scarfone, Karen · Mell, Peter |
| Report Number | 800-94 |
| Report Type | Special Publication |
| Series Title | NIST Special Publication |
| Place | Gaithersburg, MD |
| Institution | National Institute of Standards and Technology |
| Date | 2007-02 |
| DOI | 10.6028/NIST.SP.800-94 |
| URL | https://csrc.nist.gov/pubs/sp/800/94/final |
| Short Title | Guide to Intrusion Detection and Prevention Systems |
| Rights | U.S. Government work (public domain in the US) |
| Extra | Standard. 2007 version is still final; the 2012 draft Rev. 1 was retired and never finalised. |

**Harvard:** Scarfone, K., & Mell, P. (2007). *Guide to Intrusion Detection and Prevention Systems (IDPS)*. NIST Special Publication 800-94. Gaithersburg, MD: National Institute of Standards and Technology. Available at: https://doi.org/10.6028/NIST.SP.800-94 [Accessed 5th October 2026].

Notes: cite the **2007** edition. Don't cite "Rev. 1"; that draft was never finalised and has been retired.

### ENISA Threat Landscape (annual): latest edition
| Field | Value |
|---|---|
| Item Type | **Report** |
| Title | ENISA Threat Landscape 2026 |
| Author | European Union Agency for Cybersecurity (ENISA) *(single-field / corporate)* |
| Place | ⚠ not stated in the PDF front matter (ENISA is based in Athens) |
| Institution | European Union Agency for Cybersecurity (ENISA) |
| Date | 2026-09-22 |
| DOI | 10.2824/0806036 |
| ISBN | 978-92-9204-807-5 |
| URL | https://www.enisa.europa.eu/publications/enisa-threat-landscape-2026 |
| Rights | CC BY 4.0 |
| Extra | Grey literature. Covers 1 Jan–31 Dec 2025. TLP:CLEAR. |

**Harvard:** European Union Agency for Cybersecurity (ENISA) (2026). *ENISA Threat Landscape 2026*. Online. European Union Agency for Cybersecurity. Available at: https://doi.org/10.2824/0806036 [Accessed 5th October 2026].

Previous edition, if you prefer it:

| Field | Value |
|---|---|
| Item Type | **Report** |
| Title | ENISA Threat Landscape 2025 |
| Author | Boutemeur, Jamila · Lella, Ifigeneia · Bakatsis, Ilias · Chatzichristos, Georgios · Foley, Kevin · Leskinen, Jussi · Otcenasek, Jakub · Ziolek, Dominik (as listed in the report; or use ENISA as corporate author) |
| Series Title | ENISA Threat Landscape (ISSN 2363-3050) |
| Institution | European Union Agency for Cybersecurity (ENISA) |
| Date | 2025-10 |
| DOI | 10.2824/1946374 |
| ISBN | 978-92-9204-723-8 |
| URL | https://www.enisa.europa.eu/publications/enisa-threat-landscape-2025 |
| Rights | CC BY 4.0 |
| Extra | Grey literature. Covers 1 Jul 2024–30 Jun 2025. Current file is v1.3 (Sep 2026, corrected figures). |

**Harvard:** European Union Agency for Cybersecurity (ENISA) (2025). *ENISA Threat Landscape 2025*. Online. European Union Agency for Cybersecurity. Available at: https://doi.org/10.2824/1946374 [Accessed 5th October 2026].

Notes: the **2026 edition came out on 22 Sep 2026**, which is newer than when your list was written. It is the one to cite for currency. For the 2026 edition, the front matter gives "ENISA" as the author.

---

## What I could not confirm (summary)
- **Olsen (13)**: university, year, degree, pages. Open the ProQuest link.
- **MITRE ATT&CK Evaluations (11)**: your URL is the wrong page; pick the round you cite.
- **PTEF (12)**: date. Red Canary (14): exact release day and place.
- **ACM CSUR article number (4)**: Zotero's "Add by Identifier" may fill this.
- **Preprints 3, 5, 10**: no peer-reviewed version found. I could not reach DBLP, so re-check there before you submit.
