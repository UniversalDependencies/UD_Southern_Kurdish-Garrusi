# Summary

A dependency treebank in Universal Dependencies (UD) format, derived from narrative and questionnaire texts. This document gives an overview of the annotation scheme, linguistic features, and structural patterns seen in the data.
This treebank contains annotated sentences in an understudied Kurdish language variety called Garrusi (Indo-European), spoken in western regions of Iran (see Asadpour and Zarei, forthcoming). The data is formatted according to the Universal Dependencies (UD) guidelines (v2.11), with detailed morphosyntactic annotation and dependency structure. The language shows features such as verb serialization, possessive clitics, and light verb constructions.
Note: This README is based on the current state of the dataset, which includes 1,182 tokens. Some examples and tag distributions reflect larger internal versions of the corpus and might include sentences beyond the publicly released set.

# Introduction

## 1. Dataset Overview

| Property                    | Value                                              |
| --------------------------- | -------------------------------------------------- |
| **Language**                | Garrusi Kurdish                                    |
| **Data Type**               | Narrative, spoken-style discourse                  |
| **Total Sentences**         | 140                                                |
| **Total Tokens**            | 1,182                                              |
| **Multi-word Tokens (MWT)** | 48                                                 |
| **Annotation Level**        | POS, Morphology, Lemmas, Dependencies              |
| **Format**                  | CoNLL-U (Universal Dependencies)                   |

The dataset consists of descriptive narrative texts involving everyday actions, motion, and social interactions, providing insights into colloquial Garrusi syntax and discourse patterns.

---
# Linguistic Features
Garrusi exhibits several noteworthy syntactic phenomena:

Light Verb Constructions (LVCs): Productive noun + light verb combinations
Possessive Clitics: Systematic pronominal attachment patterns
Verb Serialization: Multiple verbs in sequence without overt coordination
Discourse Particles: Rich inventory of emphatic and discourse markers

## 2. Part-of-Speech (UPOS) Tagset

The treebank uses the standard UD POS tagset. Below is the full distribution:

| UPOS    | Count | Example(s)                                 |
| ------- | ----- | -------------------------------------------|
| 'VERB'  | 215   | dey 'give', kird 'do', bîn 'see'           |
| 'NOUN'  | 205   | kuř 'boy', duçerxe 'bicycle', timşa 'look' |
| 'PRON'  | 138   | y '3SG', ewe 'that', î 'his/her'           |
| 'ADP'   | 128   | we 'to/at', le 'from', naw 'in'            |
| 'ADV'   | 121   | red 'away', leyre 'there', temami 'all'    |
| 'DET'   | 67    | yê 'the', ew 'that'                        |
| 'PUNCT' | 58    | Sentence and quotation punctuation         |
| 'NUM'   | 52    | sê 'three', dane 'two'                     |

---

# Key Syntactic Patterns

## Light Verb Constructions
The most frequent pattern involves a semantically heavy noun combined with a light verb, annotated using compound:lvc:

sent_id = 92,

text = Kuřêş ki we duçerxewe řikab deygo.

### "The boy who pedals the bicycle."

5  řikab    řikab    NOUN  _  Number=Sing        6  compound:lvc  _  _

6  deygo    dagin    VERB  _  Mood=Ind|Tense=Pres  0  root         _  _

Structure: NOUN[compound:lvc] → VERB[root]

Meaning: řikab dey = "to pedal" (lit. "give pedal")


## Possessive Constructions
Possessive relationships use pronominal clitics marked with nmod:poss:

sent_id = 31,

text = Timşay bawkî kird.

### "(He) looked at his father."

3  bawk  bawk  NOUN  _  Number=Sing                    5  obl       _  _

4  î     î     PRON  _  Person=3|Number=Sing|Anim=Anim  3  nmod:poss _  _

Structure: NOUN ← PRON[nmod:poss]

Features: Possessive pronouns carry Person, Number, and Animacy


## Multi-word Tokens
Pronominal clitics are systematically separated from their hosts:

3-4  bawkî  _  _  _  _  _  _  _  _

3    bawk   bawk  NOUN  _  Number=Sing     5  obl       _  _  

4    î      î     PRON  _  Person=3|...    3  nmod:poss _  _

Policy: Pronominal clitics split; morphological affixes (definiteness, case) remain attached.


## Auxiliary Verbs ('AUX')
Only 4 instances of 'AUX' are annotated, all from the verb 'daştin' ("to be").

| Token  | Lemma    | Function                        | DEPREL | Sentence        |
| ------ | -------- | ------------------------------- | ------ | --------------- |
| 'dîrî' | 'daştin' | Progressive aspect ("is doing") | 'aux'  | #79, #146, #182 |
| 'e'    | 'e'      | Existential/copular "be"        | 'cop'  | #82, #88        |


#### Example:
sent_id = 79,

text = Yê dane kuř dîrî we duçerxi’o lewre řed dû 

→ "A boy is passing by there on a bike."

---

# Discourse Markers
Garrusi employs various particles for emphasis and discourse organization:

## Particles ('PART')

The PART tag is used for discourse particles and emphatic words.

| Token  | POS    | Sentence | Function                  | Example Context
| ------ | ------ | -------- | ------------------------- | ------------------------- |
| 'erî'  | PART   | #115     | "each", "every"           | Distributive meaning      | 
| 'he'   | PART   | #95      | emphatic "just", "really" | Verb modification         |
| 'xodi' | PART   | #208     | "hey!", "listen!"         | Attention-getting         |
| 'ewse' | PART   | #73, #82 | "that's it", "exactly"    | Sentence-initial emphasis |

1  Ewse    Ewse  PART  _  _  4  discourse  _  _

2  nişan   nişan NOUN  _  _  4  compound:lvc _  _  

4  dey     dan   VERB  _  _  0  root       _  _

# "That's it, (he) shows (it)."

---

## 3. Morphological Features (FEATS)

These are the morphological features used in the annotation, along with their values and notes.

| **Feature** | **Possible Values**   | **Notes**                                     |
| ----------- | --------------------- | --------------------------------------------- |
| 'Person'    | '1', '2', '3'         | Marks person on verbs and pronouns            |
| 'Number'    | 'Sing', 'Plur'        | Seen on verbs, nouns, and pronouns            |
| 'Tense'     | 'Past', 'Pres', 'Fut' | Verb tense categories                         |
| 'Mood'      | 'Ind', 'Sub', 'Imp'   | Indicative, Subjunctive, Imperative           |
| 'VerbForm'  | 'Fin'                 | Only finite forms in current dataset          |
| 'Voice'     | 'Act', 'Pass', 'Cau'  | Active, Passive, and Causative voice          |
| 'Aspect'    | 'Perf', 'Imp'         | Perfective and Imperfective aspects           |
| 'Definite'  | 'Def', 'Ind', 'Spec'  | For definiteness and specificity              |
| 'Animacy'   | 'Hum', 'Anim', 'Inan' | Used on pronouns and nouns                    |
| 'ExtPos'    | 'ADP'                 | External POS used for MWTs (e.g. in 'we ban') |

There are no non-finite verbs (Inf, Part) in the current dataset, but that may change in larger releases.

---

# Annotation Guidelines

## Tokenization and Segmentation
### Basic Principles:

Words segmented based on whitespace and punctuation boundaries
Pronominal clitics separated as individual tokens
Morphological affixes (case, definiteness) remain attached to host
Multi-word tokens (MWT) used for clitic-host combinations

#### Clitic Treatment:
| **Clitic Type** | **Segmentation Rule**     | **Example**             | **Annotation**          |
| --------------- | ------------------------- | ----------------------- | ----------------------- |
| 'Pronominal'    | Always separated          | mîveganî → mîvegan + î  | 3-4 mîveganî            |
| 'Prepositional' | Separated if grammatical  | kirde → kird + e        | 1-2 kirde               |
| 'Postpositional'| Host-attached             | we desmalo → we desmalo | Single tokens           |

#### Multi-Word Token (MWT) Format:
3-4  bawkî     _  _  _  _  _  _  _  _

3    bawk      bawk  NOUN  _  Number=Sing     5  obl       _  _

4    î         î     PRON  _  Person=3|...    3  nmod:poss _  _

## Lemmatization Standards

### Verbal Lemmas:

Infinitive form where available: dey → dan, kird → kirdin

Root form for irregular verbs: bî → bun

Light verbs maintain semantic form: dey → dan (not reduced)

### Nominal Lemmas:

Singular, indefinite form: kuřan → kuř

Base form without possessive markers: bawkî → bawk

Compound nouns as single lemma: duçerxe → duçerxe

## Dependency Relations

#### Core Relations:

compound:lvc: Noun-to-verb in light verb constructions

nmod:poss: Possessive pronoun modifying noun

discourse: Sentence-level particles (ewse, xodi)

fixed: Multi-word adpositions (we ban)

#### Light Verb Constructions:

Direction: NOUN[compound:lvc] → VERB[head]

Features: Noun carries semantic content; verb grammaticalized

#### Possessive Constructions:

Direction: NOUN ← PRON[nmod:poss]

Features: Pronoun marked for Person|Number|Animacy|Definite


## Morphological Annotation

### Feature Assignment:

Verbs: Person, Number, Tense, Mood, Voice, Aspect

Pronouns: Person, Number, Animacy, Definiteness

Nouns: Number, Definiteness (when overt)

### Consistency Rules:

Possessive clitics always carry full pronominal features

Light verbs retain full verbal morphology

Discourse particles minimally specified

---

# 4. Syntactic Dependencies (DEPREL)

Dependency relations annotated in the treebank:

| **DEPREL**     | **Count** | **Description**                                          |
| -------------- | --------- | -------------------------------------------------------- |
| 'root'         | 140       | Root of the sentence                                     |
| 'conj'         | 106       | Coordination (verbs, clauses)                            |
| 'obl'          | 98        | Oblique nominal (often with ADPs like 'we', 'le', 'naw') |
| 'compound:lvc' | 88        | Light verb construction ('NOUN' + 'VERB')                |
| 'nmod:poss'    | 68        | Possessive modifier (e.g., 'his', 'my')                  |
| 'case'         | 62        | Case/adposition marker                                   |
| 'nsubj'        | 68        | Nominal subject                                          |
| 'obj'          | 35        | Direct object                                            |
| 'parataxis'    | 32        | Independent clauses (e.g., in direct speech)             |
| 'advmod'       | 32        | Adverbial modifier                                       |
| 'det'          | 45        | Determiner                                               |
| 'punct'        | 58        | Punctuation                                              |
| 'discourse'    | 14        | Discourse markers ('xodi', 'erî', 'ewse')                |
| 'mark'         | 11        | Subordinators (like 'ki')                                |
| 'nummod'       | 24        | Numerical modifiers                                      |
| 'aux'          | 4         | Auxiliary verb ('dîrî')                                  |
| 'cop'          | 2         | Copula ('e')                                             |
| 'advcl'        | 18        | Adverbial clause (time, reason)                          |
| 'advmod:emph'  | 2         | Emphatic adverb ('he')                                   |
| 'fixed'        | 6         | Fixed multi-word expressions ('we ban', 'naw danî')      |
| 'dep'          | 1         | Unclear or default relation (e.g., 'her' → 'kanî')       |

Some edge cases need review — like dep, or where fixed was not accepted by the annotation tool.

### root — Sentence Root
Marks the main verb or clause head.

sent_id = 79,  
text = Yê dane kuř dîrî we duçerxi’o lewre řed dû. 
dû (pass/go) is the root of the sentence.

### nsubj — Nominal Subject
The syntactic subject of the sentence.

3	kuř	kuř	NOUN	_	...	9	nsubj	_	_.
kuř (boy) is the subject of the verb dû.

### obj — Direct Object
Marks the direct object of a verb.

sent_id = 31,  
text = Timşay bawkî kird.  
bawk (father) is the object of kird (looked), though indirectly due to possession.

### obl — Oblique Argument
Used for arguments introduced by adpositions.

6	duçerxi’o	duçerxe	NOUN	_	...	9	obl	_	_.
The phrase "on the bike" functions as an oblique argument of motion.

### case — Case Marker / Adposition
Attached to the noun or pronoun it modifies.

5	we	we	ADP	_	_	6	case	_	_.
we (to) marks the case on duçerxi’o (bike).

### compound:lvc — Light Verb Construction
Marks the noun part of a light verb construction.

sent_id = 92,
text = Kuřêş ki we duçerxewe řikab deygo.
5	řikab	řikab	NOUN	_	...	6	compound:lvc	_	_.
řikab (pedal) + deygo (give) = "to pedal".

### nmod:poss — Possessive Modifier
Marks a possessive relationship, often with clitics.

4	î	î	PRON	_	...	3	nmod:poss	_	_.
î (his) modifies bawk (father) → “his father”.

### parataxis — Side-by-side Clauses
Used when clauses are joined without clear subordination.

8	dey	dan	VERB	_	...	1	parataxis	_	_.
Second verb in a sentence without a conjunction or subordinator.

### advmod — Adverbial Modifier
Used for adverbs that modify verbs or other modifiers.

7	lewre	lewre	ADV	_	_	9	advmod	_	_.
lewre (there) modifies the verb.

### advmod:emph — Emphatic Adverb
Special emphatic use, e.g. he.

Token: he → Tagged as 'PART', DEPREL: 'advmod:emph'
Used to emphasize an action or statement.

### aux — Auxiliary Verb
Used for progressive/aspectual verbs.

4	dîrî	daştin	AUX	_	...	9	aux	_	_.
Progressive auxiliary before the main verb.

### cop — Copula
Link between subject and predicate in a copular clause.

3	e	e	AUX	_	...	1	cop	_	_.
In “Ayda hûz e da”, e is the copula for "Ayda is a village".

### fixed — Fixed Multi-Word Expressions
Used when multiple tokens act as a single grammatical unit.

Example: 'we ban',
'ban' is 'fixed' to 'we', 
Used for fixed adpositional phrases.

### discourse — Discourse Element
Covers interjections and emphasis/discourse markers.

1	Ewse	Ewse	PART	_	_	4	discourse	_	_.
Marks things like ewse (that’s it), xodi (hey!), erî.

### mark — Subordinator
Used for subordinating conjunctions or relative markers.

2	ki	ki	PRON	_	_	6	mark	_	_.
ki introduces a relative clause or subordination.

### det — Determiner
Modifiers like yê, ew.

1	Yê	yê	DET	_	...	3	det	_	_.
Marks definiteness and specificity.

### nummod — Numeric Modifier
Number words attached to nouns.

2	dane	dane	NUM	_	_	3	nummod	_	_
“two boys” → dane modifies kuř.

### dep — Unspecified/Other
Used in unclear or unresolved cases.

her → kanî → dep,
Might need to be reclassified as discourse or advmod.


---

## 5. Notes on Annotation Decisions and Future Review
The following points highlight areas where annotation choices may be revisited in future updates. These do not impact overall usability but are shared here for transparency and reference.

| **Issue**                                             | **Description**                                       | **Recommendation**                                                                           |
| ----------------------------------------------------- | ----------------------------------------------------- | -------------------------------------------------------------------------------------------- |
| 'ewse' tagged as both 'PART' and 'INTJ'               | Same token used with inconsistent UPOS tags           | Standardize 'ewse' to 'PART' when it functions as a discourse marker                         |
| 'her' tagged as 'PART' but linked with 'dep' relation | Usage unclear; might not be a true particle           | Change relation from 'dep' to 'discourse' or 'advmod'                                        |
| Use of 'ExtPos=ADP' on 'we', 'naw'                    | Used to indicate multi-word adpositional phrases      | Clarify annotation policy or remove if not used consistently                                 |
| No non-finite verb forms present                      | Only 'VerbForm=Fin' appears in data                   | Add 'VerbForm=Inf' and 'Part' if non-finite forms are added later                            |
| 'dep' relation used for unclear cases                 | Used as a placeholder where no specific DEPREL fits   | Review all 'dep' cases and relabel with more precise relations ('discourse', 'advmod', etc.) |
| MWT boundaries not fully consistent                   | Some clitics treated as part of word, others split    | Review MWT segmentation rules for pronominal vs. non-pronominal clitics                      |
| Definite marker '-ege' treated inconsistently         | Sometimes stays attached; other times unclear         | Provide clear guideline: treat '-ege' as part of host word consistently                      |
| Arobator platform rejects some 'fixed' relations      | Affects certain clitic combinations like 'we desmalo' | Consider workaround tagging or flagging limitations in documentation                         |

---

# Data Quality

The treebank has been manually annotated and reviewed for:

Morphosyntactic consistency

UD guideline compliance

Cross-linguistic comparability

Internal structural coherence

---

# Contact & License

- **Lead Maintainer**: Hiwa Asadpour — overall coordination, main annotation, and releases
- **Contributors**: Luigi Talamo, Annemarie Verkerk, Helena Vaz
- **Email**: [asadpourhiwa@gmail.com]
- **License**: [CC-BY 4.0]

You are free to share and adapt this work with proper attribution.

---

# Acknowledgments

We thank the contributors and native speakers who assisted in the creation of this dataset. We also acknowledge Masoumeh Zarei for her help during the early stages, before the main work began. This dataset supports the documentation and computational modeling of understudied languages.

---

## References

Asadpour, Hiwa and Masoumeh Zarei. Forthcoming. Passive Construction in Garrusi Kurdish. In Paul Noorlander and Hiwa Asadpour (eds.), Passivization in Semitic, Iranian, Armenian and Beyond: A Typological Overview, series Cambridge Semitic Languages and Cultures. Cambridge: University of Cambridge, Faculty of Asian and Middle Eastern Studies and Open Book Publishers.

---

## Sync check: updated at 17:06 CEST


# Changelog

* 2025-11-15 v2.17
  * Initial release in Universal Dependencies.


<pre>
=== Machine-readable metadata (DO NOT REMOVE!) ================================
Data available since: UD v2.17
License: CC BY-SA 4.0
Includes text: yes
Genre: grammar-examples
Lemmas: manual native
UPOS: manual native
XPOS: not available
Features: manual native
Relations: manual native
Contributors: Talamo, Luigi; Asadpour, Hiwa; Verkerk, Annemarie; Vaz, Helena
Contributing: here
Contact: luigi.talamo@uni-saarland.de
===============================================================================
</pre>

