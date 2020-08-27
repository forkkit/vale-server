---
id: languages
title: Languages
---

Vale Server's extensibility and flexibility isn't just limited to creating
English rules&mdash;most of its features are largely language-agnostic,
allowing for entire styles to be created in other languages.

## English-only

A few of Vale's extension points were designed to specifically work for English
and therefore can't be easily extended to other languages:

- [`readability`](style#readability): This extension point relies on formulas
  that are specifically designed to work on English text.

- [`capitalization`](style#capitalization): This extension point involves
  changing the case of headings to match English style guides.

- [`sequence`](style#sequence-v170): This extension point depends on a natural
  language processing library that currently only supports English.

## English by default

The following extension points require that non-English rules specify
`nonword: true` in order to disable the use of default word boundaries (`\b`):

- [`existence`](style#existence)

- [`substitution`](style#substitution)

- [`consistency`](style#consistency)

    For example,

    ```yaml
    extends: existence
    message: 'Avoid using "%s"'
    nonword: true # <-- This is required
    level: suggestion
    tokens:
      - '根据'
    ```

The [`spelling`](style#spelling) extension point requires the user to provide
their own Hunspell-compatible dictionary.

## Other extension points

[`occurrence`](style#occurrence), [`repetiton`](style#repetition), and
[`conditional`](style#conditional) should all work out-of-the-box with most
languages.