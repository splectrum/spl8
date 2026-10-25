# Natural language as the authoritative form

Status: **agreed in discussion** (2026-10-25)

## Principle

Natural language is primary wherever people or agents read. The software still
uses structured data, bound to a version; transformers map natural language to
it.

## The wrapper

A document is natural-language text that can contain structured blocks
verbatim: tables, CSV, JSON, log excerpts, AVRO records. The text around each
block says what it is (its format, units, schema version if known), and says it
in natural language.

So there is no separate metadata format and no meta-language above the content.
The reading that interprets the content also interprets what the content is.

The parallel is an AVRO container file: a header describing the schema,
followed by data blocks. Here the header is prose.

## Authority

The natural-language document is the authoritative copy and the cold-storage
form. Structured forms are projections of it, regenerated when needed.

## Projection and compliance

- **Blocks are copied, prose is interpreted.** Embedded blocks map exactly;
  only the wrapping text needs interpretation.
- **One text, many schemas.** As with AVRO reader schemas, one text can map to
  several schemas, each taking what is relevant to it. A requirement can be read
  as a task, as test cases, as a page.
- **Compliance is mappability.** A text complies with a version when it can be
  mapped to it. There are three outcomes: it maps cleanly, it maps with stated
  assumptions, or it does not map.
- **A version change produces its own migration report.** Re-map against the
  new version; the texts that no longer map show where the meaning no longer
  fits.
- **Projections are committed.** Each projection is stored next to its source,
  tagged with the schema version, the transformer version and a hash of the
  source text. Re-mapping happens only when one of those changes. The gate
  checks that committed projections are valid for their version.

## Where structure stays primary

Structure stays primary for what the running system or the gate reads
directly: git objects, URI and XPath, event logs, test commands and their exit
codes, and the projected configuration the nodes act on.

Prose has a few fixed points where agents must act consistently, for example a
task's status line.

## Fit with starting from git

At the git-only stage every document is a blob, so natural-language documents
need nothing beyond git. XPath over git reaches the document. Drilling into the
blocks inside it follows when AVRO arrives.

## Open

- Reconcile with the settled authority split (git authoritative for structure,
  the stream authoritative for data). Natural language becomes the authority
  for meaning.
- The form of the transformer, and how it is versioned.
