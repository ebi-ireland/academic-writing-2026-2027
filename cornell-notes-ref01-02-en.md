# Cornell Notes — Reference 01 & 02 (English)

> Source: clean transcription of the handwritten notes `Cornell Ref 01_02.pdf`.
> All content is the author's own reading. `[?]` marks an uncertain reading; `[...]` marks text cut off in the original.
> Transcription only — no analysis or claims have been added. (Japanese version: `cornell-notes-ref01-02.md`.)

---

## Reference 01 — MITRE ATT&CK
Related source: Strom, B. et al. "MITRE ATT&CK: Design and Philosophy." (reference_list No.1)

| Cue | Notes |
|---|---|
| Where does it come from? | - ATT&CK → a MITRE environment (2010) where researchers practiced catching intruders, assuming they were already inside.<br>- Started on Windows in 2013; went public in 2015 with 96 techniques in 9 tactics. |
| What is it used for? (1) | - Adversary emulation: imitate a real threat group to test defenses.<br>- Red teaming: act like an attacker without relying on intel about a specific group. |
| What is it used for? (2) | - Behavioral analytics: detect suspicious actions, not just known malware fingerprints.<br>- Defensive gap assessment: reveal blind spots and decide where to invest.<br>- Threat intel enrichment: describe groups by what they do rather than [what] tools they are. |

Leading fragment: "... (tests) don't try to attack real software." — possibly continued from the previous page.

**Summary**
- ATT&CK is a catalog of real attacker behavior that grew out of MITRE's FMX testing lab.
- Goal of the method: (1) separate the specific real-world execution; (2) raise confidence / detail [?]
- Connects broad lifecycle models (e.g. kill chains) with low-level exploit and malware databases.

---

## Reference 02 — CALDERA
Related source: Applebaum, A. et al. "Intelligent, Automated Red Team Emulation." (reference_list No.2)

| Cue | Notes |
|---|---|
| What is CALDERA? | - An open-source MITRE [tool] for testing of networks.<br>- attacker model lin[ked] [?]<br>- A planning system that packs and runs techniques. |
| What problem does it solve? | - Real red team engagements are expensive.<br>- Real red team members: their scope, detail, and results vary from one engagement to the next. |
| What is an operation? | - Defined by two choices: (1) adversary profile; (2) planner.<br>- The planner turns abilities into concrete instructions for agents.<br>- Red and blue operations can run side by side. |
| What are abilities? | - The actions agents can perform — dumping credentials, mounting remote shares, scheduling remote tasks.<br>- Written in YAML with a name, description, and platform-specific instructions and requirements. |

**Summary**
- (1) CALDERA is MITRE's open-source platform for automating red team and blue team cyber exercises.
- (2) Built to make adversary testing cheaper, faster, and repeatable.
- Current planners are simple, running all abilities [... note cut off]
