# SecCertRoadmapHTML
Security Certification Roadmap — Interactive Mind Map

This is a fork of [pauljerimy.com/security-certification-roadmap](https://pauljerimy.com/security-certification-roadmap/), rebuilt as a fully interactive D3.js mind map with real-time filtering, a multi-cert compare tray, and an AI-powered certification path planner.

The tool is a single self-contained HTML file. No build step, no dependencies to install, no server required — open it in any modern browser.

---

## Usage

1. Download `security-cert-mindmap.html`
2. Open it in a browser
3. Navigate the mind map: **scroll** to zoom, **drag** to pan
4. Filter by domain, skill level, or ops team using the top bar
5. Toggle **DECLUTTER** to reduce to ~66 high-signal curated certs
6. Press **/** to search, **Escape** to clear
7. Click any cert node to add it to the **Compare Tray**
8. With certs in the tray, click **Plan Path ↗** to open the AI path planner

### AI Path Planner — API Key

The path planner calls the Anthropic Claude API. No key is stored in this file or the repository. When you open the planner modal, paste your key into the **Anthropic API Key** field and click **Save**.

The key is stored in `sessionStorage` only — it is tab-scoped, clears automatically when the tab closes, and is never written to disk or committed to the repo.

Get a key at [console.anthropic.com](https://console.anthropic.com)

> **If you fork this repo:** do not add your key to the HTML file. Do not create a `.env` file without adding it to `.gitignore` first.

---

## Change Log

### May 2025 (this fork):
- Rebuilt visualization from static CSS grid to interactive D3.js radial mind map
- Center node radiates to 8 domain clusters; cert nodes orbit each domain in concentric arcs by skill level (Entry → Expert)
- Infinite pan (drag) and zoom (scroll, 0.18×–3.5×) via D3 zoom behavior
- Preserved original color coding: Network=green, IAM=teal, Architecture=orange, Asset=yellow, GRC=gray, Audit=purple, Software Security=blue, Ops=red
- Blue Team ops and Red Team ops rendered in distinct colors (#3a7bd5 / #d05050) within the Operations domain
- Level pip dot on each cert node encodes skill tier (bottom-right corner)
- Key cert indicator dot (top-left corner) marks declutter-visible certs
- Dead/stale URL certs render at reduced opacity with amber ⚠ glyph
- Added domain filter: ALL / NET / IAM / ARCH / ASSET / GRC / AUDIT / SDEV / OPS
- Added skill level filter: ALL / Entry / Intermediate / Advanced / Expert
- Added Ops subcat filter: ALL / Blue Team / Red Team
- All three filters compound — e.g. "Advanced Red Team" isolates only those nodes
- Inactive domains fade to ~8% opacity rather than disappearing, preserving spatial context
- Added DECLUTTER mode: toggle filters to ~66 curated high-signal certs
  - key:true flag added to industry-recognized certs across all domains
  - Designed for presentations and onboarding conversations
  - Stacks correctly with domain and level filters
- Added live search: real-time filter against cert name and full description (cost, vendor, etc.)
  - Press / to focus search from anywhere on the page
  - Press Escape to clear the query
  - "reset" link appears whenever any filter is active
- Added hover tooltips: full cert name, domain, subcat, cost, skill level badge, dead-link warning, and compare tray context hint
- Added compare tray: click any node to add to a slide-up tray (max 8 certs)
  - Each card shows name, domain, level, subcat, and cost
  - Individual × remove or bulk Clear
  - Tray only appears in topbar when at least one cert is selected
- Added AI Certification Path Planner powered by claude-sonnet-4-20250514
  - Takes compare tray contents as target certifications
  - User inputs: current certs/experience, role goal, time available
  - Returns: Alignment Check, Prerequisites, Ordered Path with cost and study time, Quick Wins, Watch Outs (lab costs, access windows, logistical traps)
  - Regenerate button for iterating with updated inputs
- Added runtime API key management (Option 3 — no backend required)
  - Key entered in the planner modal at runtime, never stored in the file or repo
  - Stored in sessionStorage only: tab-scoped, clears on tab close
  - Masked display after save, Show/Hide toggle for verification
  - Invalid/expired keys auto-cleared on authentication error with guidance
  - Source comment block at top of file documents the security model
- Flagged stale/dead URLs identified during audit:
  - eLearnSecurity certs (migrated to INE): eCTHP, eCDFP flagged
  - Offensive Security domain rename (offensive-security.com → offsec.com)
  - VMware/Broadcom cert pages flagged after acquisition migration: VCDX DCV, VCIX DCV, VCP DCV
  - AccessData ACE flagged (acquired by Exterro, status unknown)

---

### July 2024:
- Added GIAC certifications: GRTP, GEIR, GX-FA, GX-PT, GMLE
- Added ISACA certification: CCOA
- Added CyberDefenders certification: CCD (credit: 0xHasanM)
- Added TCM Security certification: PJMR (credit: Brandon-Russell-1)
- Added Hack the Box certifications: HTB CDSA, HTB CWEE
- Added The SecOps Group certifications: SOG CAP, SOG NSP, SOG CCSP-AWS, SOG CAPen, SOG CNPen, SOG CMPen And, SOG CMPen iOS, CCPenX-AWS, SOG CAPenX
- Added Fortinet certifications: FCF, FCA, FCP NS, FCP PCS, FCP SO, FCSS SO, FCSS OT, FCSS NS, FCSS SASE, FCSS PCS, FCSS ZTA, FCX
- Removed defunct Fortinet certifications: NSE 3, 4, 5, 6, 7, 8
- Removed defunct Palo Alto certifications: PA CRTP, and PA CRTE (credit: MaLevi4)
- Removed defunct Linux Foundation certification: LFCE (credit: MaLevi4)
- Removed defunct CREST certifications: CRTSA, CMRE (credit: sawft99)
- Removed defunct INE certifications: eCRE, eCPTX, eCMAP, eWDP, eCXD (credit: Brandon-Russell-1 & r-yu-2)
- Removed defunct GIAC certifications: GPPA, GEVA, and also ICS612 because its not a certification
- Removed defunct ISC2 certification: HCISPP
- Removed defunct ISACA certifications: CSX-PA, CSX-T
- Removed defunct IA Certification certification: CEREA
- Moved GIAC GSE down 2 rows after removal of lab requirement
- Shortened Security+, SSCP, GSEC, Programming Languages, CASP+, CISSP, CISSP Concentrations, and GSE to cover 4 spaces in only GRC to make room for more certifications
- Shortened GREM to fit with the new size of the GRC certifications
- Corrected GIAC GPYC as a blue ops certification instead of a red ops
- Corrected (ISC)2 branding to ISC2 (credit: kabaki1982)
- Corrected links for eLearnSecurity Certifications
- Corrected link for S-EHR (credit: kasperkarlsson)
- Corrected link to CISSP concentrations (credit: psarossy)
- Corrected links to CREST certifications (credit: sawft99)
- Corrected links for Cisco DevNet Pro and DevNet A
- Corrected spelling for PSM III and MTH description
- Corrected certification names for CREST CCTINF, CCTIM, CCHIA, CCTAPP, CCNIA (credit: sawft99)
- Corrected certification name for SC-400 (credit: ep3p)
- Corrected certification name for AZ-305 (credit: wongsenoch)
- Corrected certification name for CAP to CGRC (credit: corbin-lounsbury)
- Corrected price for Splunk ECSA (credit: aserpi)
- Corrected prices for GIAC certifications
- Corrected prices for CompTIA certifications

### February 2023:
- January's update was done to the wrong version which brought some old bugs back:
- Duplicate AZ-500 fixed to AZ-305
- Static mobile version changed back to dynamic

### January 2023:
- Added ISC2 certification: CC
- Added ISMI certifications: CSM and CSMP
- Added OCEG certifications: GRCP and GRCA
- Added Zero Point Security certification: CRTO II
- Added GIAC certifications: GCTD and GCWN
- Added Scrum.org certifications: PSM I and PSM II
- Added IDPro certification: CIDPRO
- Added Mosse Institute: MSAF
- Added HTB certification: HTB CPTS
- Added Shared Assessments certifications: CTPRP and CTPRA
- Removed duplicate Zero Point CRTO
- Removed Mosse Institute MTCF (defunct)
- Removed SUSE SEA (defunct)
- Updated link and exam cost for eJPT
- Corrected CSP-SM as PSM III
- Corrected links for SUSE SCA and SCE
- Moved BSCP from Test to Penetration Testing
- Moved BSCP up 1 row
- Moved OSEE up 1 row
- Moved S-CISO down 5 rows
- Moved CIISec ICSF down 1 row
- Moved MTIA down 2 rows
- Moved MDSO down 2 rows
- Moved MVRE down 2 rows
- Moved MTH down 3 rows
- Moved MRT down 3 rows
- Moved MRE down 3 rows
- Moved MCD down 4 rows
- Moved MCSE down 5 rows
- Reduced Cloud+, Server+, and CCSP size to just the Security Architecture & Engineering - Cloud/SysOps sub-domain

### August 2022:
- Added SANS certifications: GIME and GCFR
- Added SECO certifications: S-TA, S-SA, and S-CSPL
- Added Certiport certifications: ITS-C and ITS-NS
- Added EC Council certification: CCSE
- Added Mile2 certifications: C)HISSP, C)ISRM, IS20, C)IHE, C)DRE, CM)ISSO, CM)IPS, and CM)DFI
- Added PCI certification: PCI QSA
- Added The H Layer certification: SACP
- Added Cyber Scheme certifications: CSTM and CSTL
- Added Microsoft certification: SC-100
- Added Hack the Box certification: HTB CBBH
- Removed duplicate PCNSA
- Removed CREST CWS
- Moved MCSE from Security Operations to Security Architecture and Engineering
- Moved GPEN up 1 row
- Moved CFCE up 1 row
- Moved C)ISSM up 2 rows
- Moved CISSM up 1 row
- Moved CAP up 1 row
- Moved HCISPP up 1 row
- Corrected HCISSP to HCISPP
- Corrected the CCIE Ent link
- Corrected SECO certification links and prices
- Corrected SANS certification prices from $849 to $949
- Corrected Offensive Security prices to $1499 except OSWE to $1649
- Other link and price fixes that I lost track of because I accidentally closed this readme without saving

### April 2022:
- Added Fair Institute certification: Fair Fdn
- Added Dark Vortex certifications: DV MoS, DV RTOS, DV OTD, DV AOPH, and DV MILF
- Added Mosse Institute certifications: MCSF, MICS, MTCF, MASE, MCL, MCPT, MCSE, MESE, MCPE, MDSO, and MVRE
- Added Mitre Att&ck certifications: MAD CTI and MAD SOCA
- Added EXIN certifications: 27001F, 27001P, and 27001E
- Added Axelos certifications: M_o_S Foundation and M_o_S Practitioner
- Added SANS certifications: GFACT, GSOC, and GPCS
- Added Microsoft certification: SC-400
- Added Fortinet certifications: NSE 3 and NSE 5
- Added Palo Alto certifications: PCCET, PCDRA, PCCSE, and PCSAE
- Added Mile2 certifications: C)SWAE, C)CSA, and C_TIA
- Added EC First certifications: CSCS, CCSA, and CCP
- Added PECB certifications: 27001F, 27001LI, 27001LA, 27032F, 27032CM, 27005RM, and 27005LM, and CLCSM
- Added Offensive Security certifications: OSDA, OSWA, and OSMR
- Added Docker certification: DCA
- Added Cloud Native Computing Foundation certifications: CKS, CKA, CKAD, and KCNA
- Removed Palo Alto certifications: PCCSA
- Removed Infosec Institute / IACRB certifications: CPT, CEPT, and CEREA which do not appear to be available at this time
- Removed Mile2 certifications: C)VE, C)VCP, C)VFE, and Red vs Blue
- Removed 9 Lunarline certifications as they were purchased by Motorola and the certifications appear to be discontinued: CEIM, CESO, CEPP, CERP, CEPM, CESA, CESE, CECS, and CEIA
- Removed GSSP which was retired
- Moved F5 CA up 3 rows
- Moved WCNA down 1 row
- Moved CCT down 1 row
- Moved OSCE3 up 1 row
- Moved DevNetA up 1 row
- Moved CCSC up 1 row
- Corrected Mile2 web links and exam prices from $400 to $550
- Corrected C)PTC from "Expert" to "Consultant"
- Corrected IACRB certifications to reflect take over by Infosec Institute and new pricing: CSAP, CREA, CMWAPT, CRTOP, CDRP, CSSA, CCTHP, CMFE, and CCFE
- Corrected LPIC-1 and LPIC-2 to reflect they require 2 exams each, with each exam costing $200
- Corrected GIAC certifications to reflect the exam price drop from $1,999 to $849 if taken without a SANS course
- Corrected GREM certification link
- Corrected SF CIAMD to fit in its container
- Corrected link to CIISec ICSF
- Renamed Microsoft certifications to their exam code. I.E., MSOAA is now SC-200
- Added hover text over domain titles with domain descriptions in line with the ISC2 CBK
- Added a row to the bottom of the certification to allow for more beginner level certifications
- Added a column on the left to add proficiency level indicators to the rows with: Beginner, Intermediate, and Advanced
- Added a column to Security Architecture & Engineering - Cloud/SysOps for container certs and more spacing
- Added a column to Security and Risk Management in order to add additional ISO/IEC 27000 certifications
- Added more code comments
- Redesigned tooltips to display in place (absolute to relative positioning)
- Added more contrast to colors: dark blue for blue team, lighter blue for software sec, darker purple for testing, grey for management, and lighter yellow for asset sec

### July 2021:
- Added Mosse Cyber Security Institute Certifications: MOIS, MNSE, MRCI, MBT, MDFIR, MGRC, MPT, MRE, MTH, MCD, MRT, and MTIA
- Added GIAC Certification: GCPN
- Added PDSO Certifications: CDP and CDE
- Added Microsoft Certification: MSOAA, MSCIF, and MIAAA
- Added Offensive Security Certification: OSED and OSCE3
- Added TCM Security Certification: PNPT
- Added Zero Point Security Certification: ZPRTO
- Added TUV Certifications: COSP, COSTE, and COSM
- Added EC Council Certification: CPENT
- Added (ISC)2 Certification: HCISSP
- Added Security Blue Team Certification: BLT2
- Removed CCAr due to it being retired March 1st, 2021
- Removed MTA due to that category of certification being retired on June 30th, 2021
- Removed ECSA due to it being retired May 15th, 2021
- Moved GCWN from the Unix to SysOps sub domain
- Moved eCIR up 1 row based on feedback
- Moved CSX-P down 3 rows based on feedback
- Moved CEPT down 7 rows and expanded into exploitation based on feedback
- Moved CPT down 5 rows based on feedback
- Moved eJPT up 1 row based on feedback
- Moved the CIST, CIGE, and SFCIAMD certifications up 1 row in the IAM domain
- Corrected the exam price for Offensive Security OSWE from $2799 to ~$1299
- Corrected the exam price for eJPT from $400 to $200
- Corrected the exam price for CFR from $149 to $250
- Corrected the exam price and link for KLCP
- Corrected the link for EITCA/IS
- Corrected the tooltip for S-CEHL due to a spelling typo
- Asset Security certifications now properly colored "yellow" instead of "orange"

### February 2021:
- Added PAI Certification: WCNA
- Added eLearnSecurity Certification: eCMAP
- Added Cisco Certification: CCCOP
- Added Linux Foundation Certifications: LFCA, LFCS, and LFCE
- Added APMG Certifications: 27001F, 27001P, and 27001A
- Expanded the GRC sub-domain to 3 columns & shifted certifications accordingly
- Moved CCCOA from Network to Security Operations
- Corrections to CCCOA, IIA CIA, FortiNET NSE 8, CAD, CAC, CCSP, eCRE, and GCPEH

### November 2020:
- Added to GitHub for pull requests
- Added Security Blue Team certification: BTL1
- Added Sales Force Certifications: SFCCCC, SFCIAMD, and SFCTA
- Added The Institute of Internal Auditors: CIA
- Added Offensive Security certification: OSEP
- Added Cisco Certification: CCCOA
- Removed Offensive Security OSCE (retired)
- Removed Cisco CCNA CyberOps (retired)
- Removed duplicate Pentester Academy CRTP
- Corrected links for Cloud+ and eWPTX
- Corrected Typo for NSCS Certs, OPSA, CCFE, and CCIE
- Corrected exam cost for AWS Security Spec and eWPTX

### October 2020:
- Updated HTML/CSS logic to increase chart size
- Updated HTML/CSS logic to allow certifications to span domains
- Updated HTML/CSS logic to allow sub-domains
- Updated HTML/CSS logic to allow easier updates
- Changed hover text to be in a static location in order to avoid clipping
- Aligned columns/towers with (ISC)2 CBK Security Domains
- Moved certifications into new domains when applicable
- Adjusted rankings based on research and feedback
- Added Identity Management Institute certifications: CIMP, CIAM, CIGE, CIST, CAMS, CIPA, CIMP, and CRFS
- Added EXIN Privacy certifications: EPDPP, EPDPF, and EPDPE
- Added ISACA certification: CDPSE
- Added DRI certifications: DCCRP, DCRMP, DACRP, DCBCLA, and DCBCA
- Added QAI certification: CSBA
- Added APMG certifications: 20000P, 20000A, and 20000F
- Added Cisco certifications: DevNet Pro, and DevNet Associate
- Added Pentester Academy certifications: CRTP, CRTE, and PACES

### September 2020:
- Removed GIAC GCUX – indefinitely unobtainable
- Corrected price on SABSA courses for North America ($400 lower)
- Removed MCSA and MCSE retiring in Jan 2021
- Removed Windows sub-domain migrating remaining certs to other appropriate sub-domains
- Named Linux sub-domain as "*nix" to reflect inclusion of Unix based certifications
- Added Microsoft 365 EAE
- Added Microsoft Azure Fundamentals

### July 2020:
- Added description of certification categories
- Added static chart for mobile and small screen users
- Added description and link to "Programming Languages"
- Fixed cert name spacing issues
- Moved OSCP up one rung due to 2020 refresh
- Added IIBA Certificate Cybersecurity Analysis
- Added AWS Security Specialist
- Added TUV Certified Operational Technology Cybersecurity Professional
- Added TUV Cybersecurity Specialist
- Added TUV Cybersecurity Awareness
- Added TUV Internal Auditor ISO 27001:2013, Information Security Management Systems
- Added TUV IT Security Auditor
- Added TUV IT Security Manager
- Added TUV Mobile Security Analyst
- Added Excida CACS
- Added Excida CACE
- Added GIAC Enterprise Vulnerability Assessor
- Added GIAC Battlefield Forensics and Acquisition
- Added GIAC Cloud Security Automation
- Added GIAC Open Source Intelligence
- Added Pentester Academy Certified Red Team Professional
- Added Pentester Academy Certified Red Team Expert

### March 2020:
- Migrated from PowerPoint image to HTML/CSS5 interactive chart
- Added mouse over information for exam price and if a course is required
- Added link to certification websites
- Included 324 certifications

### December 2019:
See roadmap here: https://www.pauljerimy.com/OC/Security%20Certification%20Progression%20Chart%20v6.2.png
- Changes towers from job types to security domains
- Added many certifications
- Moved some certifications up or down
- Moved categories so engineering and architecture are side by side due to their relation
- Changed Security Engineering to Security Implementation
- Marked Sec+, SSCP, GSEC, Programming languages, CASP, CISSP, GSE as core certifications with a gradient & note
- Added a version, date, and author
- Removed the self explanatory key
- Removed the color for "software"
- Minor formatting changes

### November 2018:
See roadmap here: https://www.pauljerimy.com/OC/Security%20Certification%20Progression%20Chart%20v5.2.png
- Rebuilt roadmap from old image
- Added many certifications
- Removed DoD 8570.01M indicators
- Condensed certifications for easier viewing

### July 2015 by Drackar of www.techexams.net:
See roadmap here: https://www.pauljerimy.com/OC/Security%20Certification%20Progression%20Chart%20v4.0.png
- Added Malware Analysis
- Added IT Security Auditor
- Added additional certifications
- Changed rankings

### November 2014 by Drackar of www.techexams.net:
See roadmap here: https://www.pauljerimy.com/OC/Security%20Certification%20Progression%20Chart%20v3.0.png
- Color coded domains
- Indicated DoD 8570 alignment
- Added key
- Added certifications
- Rearranged ranking
