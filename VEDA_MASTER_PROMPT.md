# ═══════════════════════════════════════════════════════════════════
#  VEDA AyurMind AI — MASTER EXTRACTION & JSON CONVERSION PROMPT
#  Version: 2.0  |  Use this prompt for ALL Ayurvedic text chunks
# ═══════════════════════════════════════════════════════════════════

## ──────────────────────────────────────────────────────────────────
## PART A — EXTRACTION PROMPT (Use First on Any New PDF/Image Chunk)
## ──────────────────────────────────────────────────────────────────

You are the AI co-builder of VEDA (AyurMind AI).
Your task is to extract ALL Ayurvedic knowledge from the uploaded
pages of [TEXT_NAME] into clean structured text, then convert to
JSON following the VEDA schema exactly.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
STEP 1 — VISUAL SCAN
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Read EVERY page carefully. Do not skip any page. For each page:
- Note the page number
- Identify which VEDA section the content belongs to
- Extract ALL content, not just summaries

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
STEP 2 — SECTION DETECTION
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Identify which of these sections appear in this chunk and
extract all data found under each section:

SECTION 1 — PRAKRITI & DOSHA DATA
Extract: Physical/mental traits of each prakṛti; Digestive
characteristics; Sleep patterns; Disease tendencies; 5 subtypes
of each doṣa (name, location, function); Signs of aggravated
and decreased vāta/pitta/kapha; 7 dhātus (functions, increase
signs, decrease signs); Ojas (definition, decrease signs).

SECTION 2 — DAILY ROUTINE (DINACHARYA)
Extract: Wake-up time; Each morning practice in exact sequence
with (name, method, duration, benefits, contraindications);
Tooth cleaning, tongue scraping, oil pulling (gaṇḍūṣa), nasal
drops (nasya), eye care (añjana), oil massage (abhyaṅga),
exercise (vyāyāma), bath; Night routine; Sadṿṛtta rules;
Sexual activity regimen.

SECTION 3 — SEASONAL PROTOCOLS (RITUCHARYA)
For EACH of the 6 seasons extract: Season name (Sanskrit +
English + months); Nature/characteristics; Doṣa aggravated;
Diet recommended (specific foods + tastes); Diet to avoid;
Lifestyle recommendations; Herbs recommended; Exercise guidance;
Sleep duration; Ṛtu sandhi (seasonal junction) rules.

SECTION 4 — FOOD DATABASE
For EACH food mentioned extract: Sanskrit + English name;
Category; Rasa; Guṇa; Vīrya; Vipāka; Doṣa effect; Therapeutic
uses; Contraindications; Best time/season.

SECTION 5 — HERB GROUPS (GAṆA)
For EACH group: Gaṇa name (Sanskrit + meaning); Therapeutic
purpose; Complete herb list; Doṣa addressed.

SECTION 6 — PANCHAKARMA PROTOCOLS
For EACH therapy: Name + definition; Indications;
Contraindications; Procedure steps in sequence; Dosage;
Signs of proper/insufficient/excessive application;
Post-therapy diet.

SECTION 7 — DISEASE & TREATMENT DATA
For EACH disease: Sanskrit + English name; Doṣa involved;
Causative factors; Signs and symptoms; Treatment principle;
Herbs/formulations; Dietary guidelines; Contraindicated
foods/activities.

SECTION 8 — HERB INDEX
If present: Every herb with page reference; Sanskrit name as
written in text.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
STEP 3 — PLAIN TEXT OUTPUT RULES
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
1. Extract ONLY what is present in these pages
2. Skip any section not covered in this chunk
3. Plain text output under section headings
4. Preserve all Sanskrit terms exactly as written
5. Flag any contradictions with text already in database
6. At end write:
   PAGES COVERED: [first–last]
   SECTIONS FOUND: [list]
   SECTIONS MISSING: [list — will be in next upload]


## ──────────────────────────────────────────────────────────────────
## PART B — JSON CONVERSION PROMPT (Use After Extraction)
## ──────────────────────────────────────────────────────────────────

You are the JSON architect for VEDA AyurMind AI.
Convert the extracted text above into a JSON file that EXACTLY
follows the VEDA schema below. This JSON will be merged into the
master VEDA knowledge base.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
MANDATORY JSON SCHEMA RULES
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

ROOT STRUCTURE (always include these top-level keys):
{
  "metadata": {
    "database_name": "VEDA AyurMind AI — [Text Name] Knowledge Base",
    "source_text": "[Full text name + sthāna]",
    "translator": "[Translator name]",
    "chunk_id": "[TEXT_ABBR]_[STHANA]_CHUNK_[NN]",
    "pages_covered": "[first–last]",
    "chapter_coverage": ["Chapter N: Name — COMPLETE/PARTIAL"],
    "extraction_date": "[YYYY-MM-DD]",
    "version": "1.0",
    "priority_in_veda": [1=Caraka, 2=AH, 3=Bhavaprakasha],
    "cross_reference_texts": ["list of texts cross-referenced"],
    "sections_found": ["SECTION_1", "SECTION_2", ...],
    "sections_pending_next_chunk": ["SECTION_3", ...]
  },

  "foundational_concepts": { ... },
  "dosha_system": { ... },
  "prakriti_system": { ... },
  "dhatu_system": { ... },
  "mala_system": { ... },
  "rasa_system": { ... },
  "virya_system": { ... },
  "vipaka_system": { ... },
  "guna_system": { ... },
  "dravya_classification": { ... },
  "disease_framework": { ... },
  "examination_methods": { ... },
  "treatment_framework": { ... },
  "dinacharya": { ... },
  "ritucharya": { ... },
  "food_database": { ... },
  "herb_groups": { ... },
  "panchakarma": { ... },
  "diseases": { ... },
  "herb_index": { ... },
  "text_structure": { ... },
  "flags_and_contradictions": [ ... ]
}

FIELD RULES:
- Include ONLY keys that have data from this chunk
- Never leave a field empty — omit it if no data exists
- All Sanskrit must be in IAST transliteration
- Botanical names in Latin, title case
- All page references preserved
- source_verse format: "AH Sū. [chapter]:[verse]"
- For herbs, always include fields:
  id, varga, names{sanskrit, hindi, english, latin, gujarati},
  rasa[], virya, vipaka, guna[], prabhava, dosha_effect{},
  benefits[], indications[], contraindications[], dosage{},
  anupana, formulations[], part_used[], active_compounds[],
  source_ref

FLAGS FORMAT (always append this array):
"flags_and_contradictions": [
  {
    "flag_id": "[TEXT_ABBR]_FLAG_[NNN]",
    "type": "SAFETY_WARNING | CONTRADICTION | CROSS_REF_NEEDED | INCOMPLETE_SECTION",
    "topic": "Short description",
    "detail": "Full explanation",
    "action": "VERIFY | MERGE | DO_NOT_DISPLAY | PRIORITIZE_CARAKA"
  }
]


## ──────────────────────────────────────────────────────────────────
## PART C — UPDATE/MERGE PROMPT (Use When Uploading New Chunks)
## ──────────────────────────────────────────────────────────────────

You are the database manager for VEDA AyurMind AI.
A new chunk of [TEXT_NAME] pages [X–Y] has been uploaded.
The existing JSON for this text is: [veda_ashtanga_hrdayam_chunk1.json]

Your task is to MERGE the new data into the existing JSON.
Follow these rules EXACTLY:

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
MERGE RULES
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

RULE 1 — EXTEND, NEVER OVERWRITE
If a section already exists in the JSON, ADD new data to it.
Do NOT delete or replace existing entries.
Example: If dinacharya already has danta_dhavana, and the new
chunk adds jihva_nirlekhana, append jihva_nirlekhana as a new
object inside dinacharya{}.

RULE 2 — MARK COMPLETIONS
If a section previously marked "status: PARTIAL" is now
complete, update its status to "COMPLETE" and remove it from
"sections_pending_next_chunk" in metadata.

RULE 3 — HANDLE CONTRADICTIONS
If new data contradicts existing data:
  a) Keep BOTH versions
  b) Add a flag in flags_and_contradictions[]
  c) Apply priority: Caraka (1) > AH (2) > Bhāvaprakāśa (3)
  d) Mark the lower-priority entry with
     "superseded_by": "[source]" if contradiction is confirmed

RULE 4 — UPDATE METADATA
Update these metadata fields in the merged file:
  - chunk_id → Use format: [TEXT_ABBR]_[STHANA]_MERGED_CHUNK[N]
  - pages_covered → "[original_start]–[new_end]"
  - chapter_coverage → Add new chapter entries
  - version → Increment by 0.1 (e.g. 1.0 → 1.1)
  - sections_found → Add newly completed sections
  - sections_pending_next_chunk → Remove completed, add new pending

RULE 5 — HERB DATA INTEGRITY
When adding new herbs or updating existing ones:
  - If herb already exists, UPDATE its fields with new info
  - Flag any property difference as a contradiction
  - Never create duplicate herb entries
  - Cross-reference botanical name as the unique identifier

RULE 6 — FOOD DATABASE
Each food item is uniquely identified by sanskrit name + category.
If a food entry already exists, merge additional properties.
Append new food items only.

RULE 7 — DISEASE ENTRIES
Unique identifier = Sanskrit disease name + doṣa combination.
Append new treatment options; do not replace existing ones.

RULE 8 — OUTPUT
Output the COMPLETE merged JSON file.
At the top of your response, show a MERGE SUMMARY:
  - New sections added: [list]
  - Sections completed: [list]
  - Contradictions found: [count + brief description]
  - New herbs added: [count]
  - New foods added: [count]
  - New diseases added: [count]


## ──────────────────────────────────────────────────────────────────
## PART D — CHUNK IDENTIFICATION CODES
## ──────────────────────────────────────────────────────────────────

Use these standard IDs across all VEDA files:

TEXT ABBREVIATIONS:
  CS  = Caraka Saṃhitā
  AH  = Aṣṭāṅga Hṛdayam
  SS  = Suśruta Saṃhitā
  BP  = Bhāvaprakāśa (Dhanvantarī)
  AS  = Aṣṭāṅga Saṅgraha

STHĀNA ABBREVIATIONS:
  SUTRA   = Sūtra Sthāna
  SARIRA  = Śārīra Sthāna
  NIDANA  = Nidāna Sthāna
  CHIKITS = Cikitsā Sthāna
  KALPA   = Kalpa Sthāna
  UTTARA  = Uttara Tantra
  PURVA   = Pūrva Khaṇḍa
  MADHY   = Madhyama Khaṇḍa
  UTTAR   = Uttara Khaṇḍa

CURRENT FILE: AH_SUTRA_CHUNK_01 → Pages 1–29 → v1.0
NEXT CHUNK:   AH_SUTRA_CHUNK_02 → Pages 30+ → will create v1.1


## ──────────────────────────────────────────────────────────────────
## PART E — PRIORITY & CONTRADICTION RESOLUTION RULES
## ──────────────────────────────────────────────────────────────────

When the same topic appears in multiple texts with different data:

PRIORITY ORDER (highest to lowest):
  1. Caraka Saṃhitā (CS) — PRIMARY authority
  2. Aṣṭāṅga Hṛdayam (AH) — SECONDARY authority
  3. Bhāvaprakāśa (BP) — TERTIARY authority

CONTRADICTION HANDLING:
  - Flag ALL contradictions with flag_id
  - Keep all versions in JSON under their source
  - VEDA UI will display Caraka's version by default
  - All versions available for practitioner/advanced mode

EXAMPLES OF KNOWN CONTRADICTION AREAS:
  - Rakta as 4th doṣa (some texts yes, AH says no)
  - Specific herb properties (rasa/vīrya may differ)
  - Dosage ranges (often text-specific)
  - Some formulation proportions
  - Duration of seasonal practices


## ──────────────────────────────────────────────────────────────────
## PART F — HERB JSON TEMPLATE (for herbs_database.json v1 parity)
## ──────────────────────────────────────────────────────────────────

Every herb extracted must match this exact schema:

{
  "id": "HERB_[NNN]",
  "varga": "[herb group/category]",
  "names": {
    "sanskrit": "",
    "hindi": "",
    "english": "",
    "latin": "",
    "gujarati": "",
    "tamil": "",
    "telugu": ""
  },
  "rasa": [],
  "virya": "",
  "vipaka": "",
  "guna": [],
  "prabhava": "",
  "dosha_effect": {
    "vata": "decreases | increases | neutral",
    "pitta": "decreases | increases | neutral",
    "kapha": "decreases | increases | neutral"
  },
  "benefits": [],
  "indications": [],
  "contraindications": [],
  "dosage": {
    "churna_g": "",
    "kwatha_ml": "",
    "swarasa_ml": "",
    "notes": ""
  },
  "anupana": "",
  "formulations": [],
  "part_used": [],
  "active_compounds": [],
  "source_ref": "[e.g. AH Sū. 2:2]",
  "safety_flag": null
}


## ──────────────────────────────────────────────────────────────────
## QUICK REFERENCE — HOW TO USE THIS PROMPT SYSTEM
## ──────────────────────────────────────────────────────────────────

WORKFLOW FOR EACH NEW UPLOAD:

STEP 1: Upload new PDF/image chunk
STEP 2: Paste PART A prompt → Get structured text extraction
STEP 3: Paste PART B prompt → Get new JSON for this chunk
STEP 4: Paste PART C prompt with existing JSON → Get merged JSON
STEP 5: Save merged JSON as updated version
STEP 6: Repeat for next chunk

FOR FIRST-TIME EXTRACTION (no existing JSON):
  Use PART A + PART B only → creates new JSON file

FOR SUBSEQUENT CHUNKS OF SAME TEXT:
  Use PART A + PART B + PART C → extracts + merges into existing

FOR NEW TEXT (e.g. switching from AH to Caraka):
  Use PART A + PART B with new text_abbreviation → new JSON file
  Then cross-reference contradictions with AH file manually

CURRENT DATABASE STATUS:
  File: veda_ashtanga_hrdayam_chunk1.json
  Version: 1.0
  Pages: 1–29
  Complete Sections: SECTION_1 (Dosha/Prakriti), SECTION_7 (partial)
  Partial Sections: SECTION_2 (Dinacharya — pages 26–29 only)
  Pending: SECTION_2 complete, SECTION_3, 4, 5, 6, 8
