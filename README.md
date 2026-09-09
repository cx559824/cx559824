# Rodolfo Raquion

I build production systems where the failure cases matter more than the happy path -
AI agents that touch real tools, money paths that have to reconcile, and the accounting
and messaging plumbing underneath both.

Manila, working Australian hours. [raquion.com](https://raquion.com)

---

### What is worth looking at here

Most of my work belongs to the companies who paid for it. These two are mine, and they
are the ones I would judge me on.

**[invoice-relay](https://github.com/cx559824/invoice-relay)** - invoice ingestion, LLM
extraction and payment reconciliation, built around the cases demos skip. Two idempotency
keys, because one is not enough: a content hash catches the same file delivered twice, a
normalised supplier + invoice number catches a re-issue arriving as different bytes.
Every monetary amount is an integer number of minor units - never a float, never summed
as one. The audit log is append-only and hash-chained, with tests that prove an edit and
a deletion are both detected. Partial payments, overpayments, one payment spanning
several invoices, and payments matching nothing each have defined behaviour rather than
an exception. 58 tests, five dependencies, no build step.

**[raquion-gallery.com](https://raquion-gallery.com)** - Go on Lambda over DynamoDB and
S3. Uploads are presigned and multipart so nothing large passes through the API; objects
age into Glacier on a lifecycle rule and a cold file is restored before it opens. The
restore is idempotent, because a waiting user taps the button twice. 86 test files,
deployed by SAM and GitHub Actions, OIDC-federated with no stored keys. Source private,
site public.

### The rest of this account

A long tail of public repositories - Go, Rust, Python, TypeScript - much of it plainly
learning in the open, and labelled as such rather than dressed up as products. I would
rather you find it honestly described.

### Writing

[raquion.com/writing](https://raquion.com) - mostly failures that were quiet: things
that reported success while doing nothing, and tests that passed while the feature was
broken.
