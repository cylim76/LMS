# KnowledgeTag Analysis

## Executive Summary

`KnowledgeTag` is already a hierarchical knowledge-point tree and is a good candidate basis for an LMS knowledge taxonomy, but the coverage is uneven across subjects.

## Key Findings

- Total tags: 1794
- Subjects present: biology, chemistry, chinese, english, geography, history, math, physics, politics
- Orphan nodes: 0
- Duplicate sibling groups: 0

### Subject Coverage

- `biology`: total 250, roots 8, max depth 3, avg depth 2.752, disconnected 0
- `chemistry`: total 204, roots 7, max depth 3, avg depth 2.775, disconnected 0
- `chinese`: total 8, roots 8, max depth 1, avg depth 1, disconnected 0
- `english`: total 276, roots 12, max depth 3, avg depth 2.725, disconnected 0
- `geography`: total 8, roots 8, max depth 1, avg depth 1, disconnected 0
- `history`: total 8, roots 8, max depth 1, avg depth 1, disconnected 0
- `math`: total 737, roots 17, max depth 4, avg depth 3.445, disconnected 0
- `physics`: total 295, roots 9, max depth 3, avg depth 2.766, disconnected 0
- `politics`: total 8, roots 8, max depth 1, avg depth 1, disconnected 0

### Junior / Senior Coverage for Requested Subjects

- `math`: Yes. Root nodes span primary school through junior high and senior high, with deeper subtrees under those stages.
- `physics`: Yes, but only junior high and senior high. There are no primary-school roots.
- `chemistry`: Yes, but only junior high and senior high. There are no primary-school roots.
- `english`: Yes. Root nodes span primary school through junior high and senior high.

### Structural Observations

- `math` is the deepest tree in the dataset and looks the most mature for LMS reuse.
- `physics`, `chemistry`, and `english` all have a consistent grade-band root layout, which is usable for an LMS.
- `chinese`, `geography`, `history`, and `politics` are only single-level roots in this dump, so they look incomplete as a detailed knowledge tree.
- No orphan nodes were found, so parent-child integrity appears intact.
- No duplicate sibling groups were found under the same subject/parent/name key, so the tree is clean from a sibling-duplication perspective.

### Migration Suitability

This dataset is suitable as a knowledge-point tree base for an LMS if you want a subject-oriented taxonomy with grade-stage roots and hierarchical detail. The main caveat is uneven completeness by subject, so you will likely want a normalization pass before migration:

- unify stage naming across subjects (`一年级`, `七年级上`, `高一上`, etc.)
- decide whether `subject` should remain a string enum or become a foreign key to `Subject`
- keep `KnowledgeTag` as the taxonomy table and map learner content via a many-to-many relation
- preserve `parentId`, `order`, and `isSystem` during migration

## Risks / Gaps

- Some subjects are very sparse, which means the tree is not uniformly production-ready across the whole catalog.
- The current schema stores `subject` as free text, so migration should validate canonical subject codes.
- `KnowledgeTag.userId` is nullable, which mixes global/system tags and user tags in one table.

## Duplicate / Orphan Check

- Orphans: 0
- Duplicate sibling groups: 0

## Notes on the Export

The accompanying `knowledge_tags.json` is a flat export of every `KnowledgeTag` row, and `knowledge_tree.md` renders the hierarchical tree per subject.
