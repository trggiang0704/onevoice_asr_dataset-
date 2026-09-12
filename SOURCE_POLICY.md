# OneVoice Dataset — Source & Rights Policy

**Dataset:** OneVoice ASR Dataset
**Scope:** English and Mandarin (普通话 / zh-CN)
**Current Dataset Version:** v1.0
**Policy Status:** Active
**Last Updated:** 2026-09-09

---

## 1. Purpose

This document defines the policy for selecting, evaluating, collecting, processing, and releasing audio data for the **OneVoice ASR Dataset**.

The purpose of this policy is to ensure that every audio asset included in the dataset has:

1. a traceable source;
2. an identifiable rights holder or source organization where applicable;
3. a documented license or legal basis for use;
4. evidence supporting the stated rights;
5. a clear status regarding commercial use and redistribution;
6. no unresolved third-party copyright restrictions that would prevent inclusion in the intended dataset release.

This document defines the **source and rights policy** only.

Rules concerning audio preprocessing, segmentation, transcription, annotation, QC, train/dev splitting, and dataset release procedures are defined separately in `DATA_GUIDELINE.md`.

---

# 2. Core Principles

OneVoice follows the following principles when collecting source data.

### 2.1. Traceability

Every dataset asset must be traceable to its original source.

At minimum, the provenance chain should allow:

```text
Dataset Clip
    ↓
Asset / Episode
    ↓
Official Source
    ↓
Rights Holder / Source Organization
    ↓
License / Legal Basis
    ↓
License Evidence
```

Each released asset must have sufficient metadata to reconstruct this chain.

---

### 2.2. Rights must be checked before collection

A publicly accessible audio or video file is **not automatically permitted** to be downloaded, redistributed, converted into a dataset, or used for model training.

The fact that content is available on:

* YouTube;
* a public website;
* a podcast page;
* a public media repository;
* a page with subtitles or transcripts;

does not by itself establish the right to include the content in OneVoice.

Rights checking must therefore be performed **before an asset is accepted into the dataset**.

---

### 2.3. Official sources are preferred

Whenever possible, OneVoice should obtain the asset from:

1. the official website of the source organization;
2. an official dataset repository;
3. an official asset or episode page;
4. another distribution method explicitly authorized by the rights holder.

Third-party copies, re-uploads, mirrors, and scraped copies should not be used when an official source is available.

---

### 2.4. YouTube is primarily a discovery/reference source

YouTube may be used to:

* discover relevant content;
* identify an official channel;
* identify an episode or video;
* cross-reference the original content.

However:

> **The existence of a video on YouTube does not by itself establish permission to use the content in OneVoice.**

The preferred workflow is:

```text
Official YouTube channel
        ↓
Identify video / episode
        ↓
Locate official asset or source page
        ↓
Check rights and license
        ↓
Collect from official or authorized source
        ↓
Record provenance and rights evidence
```

Downloading a video from YouTube and using it directly for training is not considered sufficient rights verification.

---

# 3. Accepted Rights Categories

OneVoice categorizes source rights into the following groups.

## 3.1. Public Domain

Public-domain content may be included in the core dataset when:

* the public-domain status is supported by an authoritative source;
* no third-party copyrighted component creates an unresolved restriction;
* the specific asset has passed the Rights Gate.

Public-domain status should be documented in `rights_manifest.csv`.

---

## 3.2. Creative Commons — CC BY

Content released under **CC BY** may be included in the core dataset when:

* the license applies to the specific asset;
* attribution requirements can be satisfied;
* no third-party component is excluded from the license;
* redistribution is permitted under the applicable license terms;
* the intended use of the dataset complies with the license;
* evidence of the license is preserved.

For CC BY assets, the following information must be recorded:

```text
rights_holder
license_type
license_evidence_path
commercial_use_status
redistribution_status
source_url
collection_date
```

The OneVoice dataset must provide appropriate attribution for CC BY sources in its attribution documentation.

---

## 3.3. Explicit Permission

A source may be included when the rights holder or authorized organization explicitly grants permission for the intended use.

The permission must be documented and stored as evidence.

Examples of acceptable evidence include:

* written permission;
* official license statement;
* institutional data-use agreement;
* official repository terms explicitly allowing the intended use.

The evidence must be referenced from `rights_manifest.csv`.

---

## 3.4. CC BY-NC and Other Non-Commercial Licenses

Content licensed under **CC BY-NC** or another license that restricts commercial use must **not be included in the core dataset intended for commercial-compatible use**.

Such content may only be maintained in a separate research/non-commercial branch if the project explicitly permits this use and all license requirements are followed.

Recommended separation:

```text
onevoice/
└── core/
    └── commercial-compatible data

onevoice_rnd_noncommercial/
└── CC BY-NC or other non-commercial data
```

Non-commercial data must never be silently mixed into the core dataset.

---

# 4. Rejected or Restricted Sources

The following sources or assets must not be included in the core OneVoice dataset unless an appropriate additional permission or license is obtained.

## 4.1. Unclear Rights

Reject assets when:

* the rights holder cannot be identified;
* the license cannot be determined;
* the source provides no usable rights information;
* contradictory rights statements exist and cannot be resolved;
* the asset appears to be a third-party upload with unclear ownership.

Status:

```text
REJECTED
```

---

## 4.2. Standard YouTube License Alone

A video being published under the standard YouTube license is **not treated as sufficient authorization for inclusion in the OneVoice core training dataset**.

This means:

```text
YouTube public
≠
dataset redistribution permission
≠
training-data permission
```

An asset discovered on YouTube must be traced to an official source or an explicit permission/license that supports the intended use.

---

## 4.3. Third-Party News or Media Content

Assets containing material from third-party organizations must be excluded unless the rights to use those components are explicitly established.

Examples include:

* AP;
* Reuters;
* AFP;
* third-party television networks;
* commercial media organizations;
* licensed footage;
* third-party interviews or recordings.

For example, an otherwise acceptable source may still be rejected if a selected clip contains an embedded third-party news segment for which OneVoice does not have the necessary rights.

---

## 4.4. Commercial Music

Audio containing significant commercial music should not be included in the core dataset unless appropriate rights are established.

Background music should also be reviewed because it may constitute third-party copyrighted material.

---

## 4.5. Re-uploaded or Unofficial Content

Do not use:

* unofficial YouTube re-uploads;
* fan channels;
* compilation channels;
* mirrored content with unclear ownership;
* edited copies whose original rights cannot be established.

---

## 4.6. Automatically Generated or Unverified Captions

Captions are not themselves a rights issue, but they must not be treated as verified ground-truth transcription.

The following must not be used directly as ground truth:

* YouTube auto-generated captions;
* automatically translated captions;
* machine-generated transcripts without human verification;
* transcripts from third-party re-uploaded videos.

Such material may only be used as a transcription **seed** and must be reviewed against the actual audio.

---

# 5. Current Approved English Sources

The current OneVoice English dataset uses the following three source organizations.

## 5.1. VOA Learning English

**Language:** English
**Variant:** American English

**YouTube channel:**

`https://www.youtube.com/@voalearningenglish`

**Official website:**

`https://learningenglish.voanews.com/`

**Typical content:**

* Learning English lessons;
* podcasts;
* English-learning programs;
* scripted or semi-scripted speech;
* relatively clean recordings.

**Primary role in OneVoice:**

* clean English ASR;
* clear pronunciation;
* baseline ASR evaluation;
* audio-text alignment;
* relatively controlled speech conditions.

### Rights policy

VOA-produced material identified as public domain may be considered for the core dataset, subject to asset-level verification.

Third-party material must be excluded unless its rights are independently established.

The following must therefore be checked before accepting an asset:

```text
[ ] Official VOA source identified
[ ] Asset ownership identified
[ ] Rights/license status verified
[ ] Third-party material checked
[ ] Transcript/source text identified
[ ] Rights evidence saved
```

The original source-selection document identifies VOA Learning English as a high-priority English source and notes that VOA-produced content should be distinguished from AP, Reuters, AFP, or other third-party material.

---

## 5.2. U.S. Department of State — Department Press Briefings

**Language:** English
**Content type:**

* press briefings;
* question-and-answer sessions;
* spontaneous speech;
* multi-speaker conversations.

**YouTube channel:**

`https://www.youtube.com/@StateDept`

**Official asset source:**

`https://www.state.gov/department-press-briefings`

**Copyright information:**

`https://www.state.gov/copyright-information`

### Primary role in OneVoice

This source is used primarily to increase diversity in:

* spontaneous speech;
* turn-taking;
* question-answer interactions;
* speaker changes;
* non-native English accents;
* names, numbers, abbreviations, and domain-specific vocabulary.

### Rights policy

Assets must be checked individually.

The dataset must not assume that every element appearing on a government website or channel automatically has identical rights.

Before acceptance:

```text
[ ] Official Department of State asset identified
[ ] Applicable rights information checked
[ ] Third-party material checked
[ ] Selected audio belongs to an acceptable rights category
[ ] Rights evidence saved
```

The source document identifies the Department of State press briefing archive and copyright information as the relevant official references for rights verification.

---

## 5.3. DVIDS — Defense Visual Information Distribution Service

**Language:** Primarily English

**YouTube channel:**

`https://www.youtube.com/user/dvidshub`

**Official asset website:**

`https://www.dvidshub.net/`

**Copyright information:**

`https://www.dvidshub.net/about/copyright`

### Primary role in OneVoice

DVIDS is used to introduce more challenging acoustic conditions, including:

* field interviews;
* outdoor speech;
* background noise;
* equipment noise;
* far-field speech;
* operational instructions;
* technical vocabulary.

### Rights policy

DVIDS assets must be checked **at the individual asset level**.

For the current OneVoice policy, an asset should only be accepted into the core dataset when the rights status is explicitly compatible with the intended dataset use.

The preferred acceptance condition is:

```text
PUBLIC DOMAIN
AND
official DVIDS asset
AND
no unresolved third-party copyrighted material
AND
no conflicting usage restriction
```

The source-selection document explicitly recommends asset-level checking for DVIDS and requires that selected assets be marked as `PUBLIC DOMAIN` and free of unresolved copyrighted material.

---

# 6. Current Approved Mandarin Source

## 6.1. Mozilla Data zh-CN-beijing

The current Mandarin data source represented in the OneVoice metadata is:

```text
source_id:
src_001

source_organization:
Mozilla Data zh-CN-beijing

official_asset_url:
https://mozilladatacollective.com/datasets/cmruwsbag00c8md07lk1n7i1e

license_type:
CC BY

language:
zh

language_variant:
zh-CN

accent_region:
Mainland China
```

The source is therefore classified as:

```text
Language: Mandarin
Variant: zh-CN
Region: Mainland China
License: CC BY
Commercial use: Allowed, subject to applicable CC BY terms
Redistribution: Allowed, subject to applicable CC BY terms
```

### Primary role in OneVoice

This source provides Mandarin speech data for:

* Mandarin ASR;
* Chinese character transcription;
* clean/scripted speech;
* speaker-level metadata;
* development of the Mandarin portion of the OneVoice dataset.

---

## 6.2. Rights Requirements for Mozilla Data

For each selected asset, OneVoice must preserve the source information necessary to establish the provenance of the data.

At minimum:

```text
source_id
source_organization
official_asset_url
rights_holder
license_type
license_evidence_path
collection_date
commercial_use_status
redistribution_status
```

For the current source, the expected license classification is:

```text
license_type = CC BY
commercial_use_status = Allowed (Based on CC BY)
redistribution_status = Allowed (Based on CC BY)
```

However, the dataset must still retain the relevant license evidence and attribution information rather than relying only on the text stored in the metadata.

---

# 7. Asset-Level Rights Gate

Every asset must pass the Rights Gate before entering the processing pipeline.

The minimum workflow is:

```text
SOURCE IDENTIFICATION
        ↓
RIGHTS HOLDER IDENTIFICATION
        ↓
LICENSE / LEGAL BASIS CHECK
        ↓
THIRD-PARTY CONTENT CHECK
        ↓
COMMERCIAL USE CHECK
        ↓
REDISTRIBUTION CHECK
        ↓
EVIDENCE PRESERVATION
        ↓
RIGHTS DECISION
```

Each asset receives one of the following statuses:

### `APPROVED`

The asset satisfies the rights requirements and may proceed to processing.

### `REVIEW`

The asset may be usable, but additional verification is required.

Examples:

* unclear third-party component;
* incomplete license evidence;
* ambiguous rights statement;
* permission document requires further verification.

### `REJECTED`

The asset does not satisfy the core dataset rights requirements.

Examples:

* unclear ownership;
* incompatible license;
* Standard YouTube License without additional permission;
* significant third-party copyrighted material;
* commercial music without permission;
* non-commercial-only license for the core dataset.

---

# 8. Required Rights Evidence

Every approved source must have evidence supporting its rights classification.

Evidence may include:

* official license page;
* official copyright statement;
* official dataset license;
* official asset page;
* permission document;
* archived copy/screenshot/PDF of the applicable rights statement;
* other authoritative documentation supporting the rights decision.

The evidence should be stored in a dedicated directory, for example:

```text
licenses/
├── voa/
├── state_department/
├── dvids/
└── mozilla/
```

Recommended naming:

```text
licenses/
└── <source_id>/
    ├── license_evidence.pdf
    ├── source_page.pdf
    └── notes.txt
```

The exact evidence path must be recorded in:

```text
license_evidence_path
```

inside `rights_manifest.csv`.

---

# 9. Required Rights Metadata

The rights information for each source/asset must be recorded in `rights_manifest.csv`.

The minimum rights-related fields are:

```text
asset_id
source_id
source_organization
source_program
official_asset_url
youtube_reference_url
rights_holder
license_type
license_evidence_path
collection_date
third_party_content
commercial_use_status
redistribution_status
dataset_version
```

The following fields should also be retained where applicable:

```text
publication_date
source_country
source_language
notes
reviewer_id
rights_check_status
rights_check_date
```

---

# 10. Relationship Between Source, Asset, and Clip

OneVoice distinguishes between:

### Source

The organization or dataset from which the content originates.

Example:

```text
src_001
Mozilla Data zh-CN-beijing
```

### Asset

A source-level recording, episode, video, podcast, or dataset item.

### Clip

A segmented portion of an asset used as an individual ASR sample.

The provenance relationship should therefore be:

```text
source_id
    ↓
asset
    ↓
clip_id
```

For example:

```text
source_id = src_001
        ↓
asset
        ↓
clip_id = zh_000669
```

The rights status of a clip must be inherited from its source/asset only when the clip does not introduce additional third-party material or other rights restrictions.

---

# 11. Third-Party Content Policy

Third-party content must be explicitly checked.

Examples include:

* news agency clips;
* television footage;
* commercial advertisements;
* copyrighted music;
* external interviews;
* third-party recordings;
* copyrighted recordings embedded in an otherwise acceptable source.

Metadata should contain:

```text
third_party_content = Yes
```

when relevant.

An asset containing third-party content is not automatically approved.

The rights reviewer must determine whether:

1. the third-party content is covered by the source's license;
2. the third-party rights are separately established;
3. the content can be safely removed;
4. the asset must be rejected.

If rights cannot be established, the asset must be marked:

```text
rights_check_status = REJECTED
```

---

# 12. Attribution Policy

All sources that require attribution must be properly acknowledged.

For CC BY sources, attribution must be maintained in the dataset documentation.

Attribution records should include, where applicable:

```text
Source organization
Dataset / asset name
Original source URL
License
Rights holder
Relevant attribution statement
Dataset version
```

The final dataset should maintain a separate:

```text
ATTRIBUTION.md
```

file containing the consolidated attribution information.

---

# 13. Commercial-Use Classification

Each source must have an explicit classification regarding commercial use.

Recommended values:

```text
Allowed
Allowed with conditions
Research only
Not allowed
Unknown
```

The value must not be inferred merely from the fact that the source is publicly accessible.

For example:

| License / Rights Status                              | Core Dataset                              |
| ---------------------------------------------------- | ----------------------------------------- |
| Public Domain                                        | Allowed, subject to asset-level checks    |
| CC BY                                                | Allowed, subject to license compliance    |
| Explicit commercial permission                       | Allowed, subject to permission scope      |
| CC BY-NC                                             | Not allowed in commercial-compatible core |
| Research-only permission                             | Not allowed in core                       |
| Unknown                                              | Reject / Review                           |
| Standard YouTube License only                        | Not sufficient                            |
| Third-party copyrighted material with unclear rights | Reject                                    |

---

# 14. Redistribution Policy

The OneVoice dataset may only redistribute audio assets when the applicable rights explicitly permit redistribution or otherwise provide a sufficient legal basis.

Therefore:

```text
Publicly accessible
        ≠
Redistributable
```

The following must be checked independently:

```text
Can OneVoice use the data for training?
Can OneVoice redistribute the processed audio?
Can OneVoice redistribute the transcript?
Can OneVoice distribute metadata?
Can OneVoice use the dataset commercially?
```

These permissions must be reflected in `rights_manifest.csv`.

---

# 15. YouTube-Specific Policy

When a source is discovered through YouTube, the following information should be recorded:

```text
youtube_reference_url
official_asset_url
source_organization
rights_holder
license_type
license_evidence_path
```

Example:

```text
youtube_reference_url:
https://www.youtube.com/...

official_asset_url:
https://official-source.example/...

license_type:
Public Domain / CC BY / Explicit Permission
```

If an official asset URL cannot be identified and the only evidence is the YouTube page itself, the asset should not automatically be approved.

It must instead enter:

```text
REVIEW
```

until sufficient rights evidence is available.

---

# 16. Rights Review Responsibilities

Rights checking is part of the three-person dataset workflow.

The person collecting or processing an asset should not be the only person responsible for final rights approval when the workflow requires independent review.

The project should maintain:

```text
rights_checked_by
rights_reviewed_by
rights_check_date
rights_check_status
```

for auditable decisions.

Any uncertain case should be escalated to a second reviewer rather than silently approved.

---

# 17. Separation of Rights and Data Quality

Passing the Rights Gate does not mean that an asset is automatically suitable for the dataset.

Each asset must pass separate gates:

```text
Rights Gate
     ↓
Technical / Audio Gate
     ↓
Transcript Gate
     ↓
Annotation Gate
     ↓
QC Gate
     ↓
Split / Leakage Gate
     ↓
Release Gate
```

For example:

```text
CC BY
    +
valid license evidence
    +
official source
```

means the asset may be legally eligible, but it may still be rejected because of:

* poor audio quality;
* excessive silence;
* unusable transcript;
* excessive overlap;
* clipping;
* language mismatch;
* duplicate content;
* speaker leakage;
* other dataset-quality problems.

---

# 18. Current Source Inventory

The current OneVoice source inventory is:

## English

| Source ID | Source                   | Primary Use                      | Rights Handling                        |
| --------- | ------------------------ | -------------------------------- | -------------------------------------- |
| `src_*`   | VOA Learning English     | Clean English / scripted speech  | Asset-level rights verification        |
| `src_*`   | U.S. Department of State | Press briefing / spontaneous Q&A | Asset-level rights verification        |
| `src_*`   | DVIDS                    | Field / noisy / technical speech | Asset-level public-domain verification |

## Mandarin

| Source ID | Source                     | Language         | License | Primary Use  |
| --------- | -------------------------- | ---------------- | ------- | ------------ |
| `src_001` | Mozilla Data zh-CN-beijing | zh-CN / Mandarin | CC BY   | Mandarin ASR |

The actual `source_id` values for the three English sources must be assigned and maintained consistently in `rights_manifest.csv`.

---

# 19. Example: Approved Mandarin Asset

An asset based on the current Mozilla Data source may have rights metadata such as:

```text
source_id:
src_001

source_organization:
Mozilla Data zh-CN-beijing

official_asset_url:
https://mozilladatacollective.com/datasets/cmruwsbag00c8md07lk1n7i1e

rights_holder:
Mozilla Data zh-CN-beijing

license_type:
CC BY

commercial_use_status:
Allowed (Based on CC BY)

redistribution_status:
Allowed (Based on CC BY)

third_party_content:
No
```

The corresponding clip may then be represented as:

```text
clip_id:
zh_000669

language:
zh

language_variant:
zh-CN

accent_region:
Mainland China

source_id:
src_001
```

This establishes:

```text
zh_000669
    ↓
src_001
    ↓
Mozilla Data zh-CN-beijing
    ↓
CC BY
    ↓
official dataset URL
    ↓
license evidence
```

The example metadata supplied for the current Mandarin data follows this provenance model.

---

# 20. Rights Manifest Requirement

`rights_manifest.csv` is the authoritative structured record of rights decisions for the dataset.

Every asset included in a release must have a corresponding rights record.

At minimum, the record must allow the team to answer:

```text
Where did this data come from?
Who owns it?
What license applies?
Where is the license evidence?
Can it be used for training?
Can it be redistributed?
Can it be used commercially?
Was third-party content present?
Who checked the rights?
When was it checked?
```

No asset should enter `RELEASED` without a corresponding rights record.

---

# 21. Release Blocking Conditions

A dataset asset must be blocked from release if any of the following applies:

* rights status is unknown;
* license evidence is missing when required;
* source ownership is unresolved;
* commercial-use status is incompatible with the intended release;
* redistribution permission is unavailable where redistribution is intended;
* significant third-party copyrighted content has unresolved rights;
* the asset is an unofficial re-upload;
* the only rights basis is the standard YouTube license;
* required attribution information cannot be provided;
* the rights reviewer has marked the asset `REVIEW` or `REJECTED`.

The release status must be:

```text
BLOCKED
```

until the issue is resolved.

---

# 22. Final Rights Checklist

Before an asset is included in a released OneVoice version:

```text
[ ] Source organization identified
[ ] Original/official asset identified
[ ] Rights holder identified
[ ] License or legal basis identified
[ ] License evidence saved
[ ] Commercial-use status determined
[ ] Redistribution status determined
[ ] Third-party content checked
[ ] No unresolved copyright restriction
[ ] YouTube is not being treated as the rights basis by itself
[ ] Attribution requirements recorded
[ ] source_id assigned
[ ] asset_id assigned
[ ] rights record added to rights_manifest.csv
[ ] Rights reviewer identified
[ ] Rights check date recorded
[ ] Dataset version recorded
```

Only after all applicable checks are passed may the asset proceed to the next stage of the OneVoice data pipeline.

---

# 23. Policy Summary

The OneVoice source policy can be summarized as:

```text
OFFICIAL / AUTHORIZED SOURCE
          +
CLEAR RIGHTS BASIS
          +
LICENSE EVIDENCE
          +
THIRD-PARTY CONTENT CHECK
          +
COMMERCIAL / REDISTRIBUTION CHECK
          +
PROVENANCE RECORD
          ↓
      RIGHTS APPROVED
          ↓
   DATA PROCESSING
```

The current source strategy is:

```text
English
├── VOA Learning English
├── U.S. Department of State
└── DVIDS

Mandarin
└── Mozilla Data zh-CN-beijing
    └── CC BY
```

The fundamental rule is:

> **No dataset asset is considered releasable solely because it is publicly accessible. Every asset must have a traceable source, an acceptable rights basis, documented evidence, and a recorded rights decision.**
