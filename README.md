eipw
====

The [EIP] validator that's one more than `eipv`.

```
USAGE:
    eipw [OPTIONS] [SOURCES]...

ARGS:
    <SOURCES>...    Files and/or directories to check

OPTIONS:
        --format <FORMAT>     Output format [default: text] [possible values: text, json]
    -h, --help                Print help information
        --lints <LINTS>       Additional lints to enable
        --list-lints          List all available lints
        --no-default-lints    Do not enable the default lints
```

[EIP]: https://eips.ethereum.org/

## Demo

### Example EIP

```markdown
---
eip: 2
description: A really short example of an EIP.
title: Sample of an EIP
author: Sam Wilson (@SamWilsn)
discussions-to: https://example.com/
status: Living
type: Meta
created: 2022-06-30
---

## Specification

Implementers of this EIP must...

## Abstract

This is an abstract!
```

### Output

```
error[markdown-order-section]: section `Specification` must come after `Motivation`
  --> /tmp/demo.md
   |
12 | ## Specification
   |
error[preamble-order]: preamble header `description` must come after `title`
 --> /tmp/demo.md
  |
3 | description: A really short example of an EIP.
  |
```

## Lints

| id                                  | Description                                                                                   |
|-------------------------------------|-----------------------------------------------------------------------------------------------|
| `markdown-link-first`               | First mention of an EIP must be a link.                                                       |
| `markdown-order-section`            | There are no extra sections and the sections are in the correct order.                        |
| `markdown-re-eip-dash`              | Other EIPs are referenced using EIP-X, not EIPX or EIP X.                                     |
| `markdown-re-eip-not-erc`           | Other EIPs are referenced using EIP-X, not ERC-X.                                             |
| `markdown-rel-links`                | All URLs in the page are relative.                                                            |
| `preamble-author`                   | The author header is correctly formatted, and there is at least one GitHub user listed.       |
| `preamble-date-created`             | The `created` header is a date.                                                               |
| `preamble-date-last-call-deadline`  | The `last-call-deadline` header is a date.                                                    |
| `preamble-discussions-to`           | The `discussions-to` header is a valid URL.                                                   |
| `preamble-eip`                      | The `eip` header is a non-negative integer.                                                   |
| `preamble-enum-category`            | The `category` header is a recognized value.                                                  |
| `preamble-enum-status`              | The `status` header is a recognized value.                                                    |
| `preamble-enum-type`                | The `type` header is a recognized value.                                                      |
| `preamble-file-name`                | The file name reflects the EIP number.                                                        |
| `preamble-len-description`          | The `description` header isn't too long.                                                      |
| `preamble-len-title`                | The `title` header isn't too long.                                                            |
| `preamble-list-author`              | The `author` header is a correctly formatted comma-separated list.                            |
| `preamble-list-requires`            | The `requires` header is a correctly formatted comma-separated list.                          |
| `preamble-no-dup`                   | There are no duplicate headers.                                                               |
| `preamble-order`                    | The preamble headers are in the correct order.                                                |
| `preamble-re-description`           | The description doesn't contain "standard" or similar words.                                  |
| `preamble-re-description-eip-dash`  | EIPs referenced in the `description` header use a dash.                                       |
| `preamble-re-description-erc`       | ERCs referenced in the `description` header use the `EIP-X` format.                           |
| `preamble-re-discussions-to`        | The `discussions-to` header points to Ethereum Magicians                                      |
| `preamble-re-title`                 | The title doesn't contain "standard" or similar words.                                        |
| `preamble-re-title-eip-dash`        | EIPs referenced in the `title` header use a dash.                                             |
| `preamble-re-title-erc`             | ERCs referenced in the `title` header use the `EIP-X` format.                           |
| `preamble-req`                      | All required preamble headers are present.                                                    |
| `preamble-req-category`             | The `category` header is present only when required.                                          |
| `preamble-req-last-call-deadline`   | The `last-call-deadline` header is present only when required.                                |
| `preamble-req-withdrawal-reason`    | The `withdrawal-reason` header is present only when required.                                 |
| `preamble-requires-status`          | EIPs listed in `requires` have statuses further along than the current proposal.              |
| `preamble-trim`                     | There is no extra whitespace around preamble fields.                                          |
| `preamble-uint-requires`            | The `requires` header is a sorted list of non-negative integers.                              |

## JavaScript / WebAssembly

`eipw-lint-js` packages `eipw` as an npm package, for use in JavaScript / TypeScript.

You can find the [package on npm](https://www.npmjs.com/package/eipw-lint-js).

### Building & Publishing

```bash
cd eipw-lint-js
wasm-pack test --node
wasm-pack build -t nodejs
wasm-pack publish -t nodejs
```
