---
title: Building CSV-powered tools for social sciences
sub_title: csv,conf,v9 2025 in Bologna
authors:
  - Guillaume Plique (aka @Yomguithereal)
  - médialab SciencesPo, Paris
theme:
  name: catppuccin-latte
  override:
    intro_slide:
      title:
        colors:
          foreground: palette:red
    slide_title:
      alignment: left
      colors:
        foreground: palette:red
    headings:
      h1:
        colors:
          foreground: palette:red
    inline_code:
      colors:
        foreground: palette:red
---

The médialab
===

The `médialab` is a social sciences research lab gathering:

- Researchers
- Engineers
- Designers

---

We have been building **Open-Source** tools geared towards social sciences & civil society at large for 10 years now!

Check out: [https://github.com/medialab/](https://github.com/medialab/)

<!-- end_slide -->

A CSV-shaped question
===

# Most of our tools/research use some kind of CSV data

We love CSV so much we wrote a ♥Love Letter♥ !

https://github.com/medialab/xan/blob/master/docs/LOVE_LETTER.md

---

# Why though?

Because CSV can be seen as a `lingua franca` in our line of work.

<!-- end_slide -->

Affordances of tabular data (1/2)
===

Everybody is familiar with tabular data, at least through spreadsheets:

<!-- new_line -->
<!-- alignment: center -->

| name      | surname | age |
| --------- | ------- | --- |
| Guillaume | Plique  | 35  |
| Lucy      | Miller  | 37  |
| Marina    | Spring  | 45  |

<!-- new_line -->
<!-- alignment: left -->

<!-- end_slide -->

Affordances of tabular data (2/2)
===

Less so with nested or hierarchical data structures like the ones found in JSON:

```json
{
  "people": [
    {
      "name": "Guillaume",
      "surname": "Plique",
      "age": 35,
      "friends": ["lucy", "marina"]
    }
  ]
}
```

<!-- speaker_note: You can ask anybody to produce/edit tabular data. The same cannot be said of hierarchical data.  -->

<!-- end_slide -->

CSV is simple
===

The specification holds in its title: **C**omma **S**eparates **V**alues!

*(Everyone here knows it's a lie, sure you need to quote values with newlines and double your quotes, but you see the point...)*

---

In any case: it can be explained to anybody in mere **minutes**.

---

Even more so: the format is so simple you might invent it **yourself**.

*(Or at least I did at the beginning of my engineering career. I thought I was soooo clever...)*

<!-- end_slide -->

CSV is free (1/2)
===

**Nobody** owns the CSV format.

It is and will always be a free and open collective idea.

It is so free it has **no real specification** either.

*(Don't force me to rant about RFC 4180, pretty please)*

---

It is so free some disciplines have their own CSV **dialects**:

- bioinformatics: `.vcf`, `.gff`, `.gtf` etc.
- web archives: `.cdx` etc.

<!-- end_slide -->

CSV is free (2/2)
===

You don't need **proprietary** software to process/read/write CSV data.

---

As a cheeky counterpoint, let's open an Excel file:

> vim data.xls

```txt
ÐÏ^Qà¡±^Zá^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@;^@^C^@þÿ     ^@^F^@^@^@^@^@^@^@^@^@^@^@^A^@^@^@^H^@^@^@^@^@^@^@^@^P^@^@^B^@^@^@^A^@^@^@þÿÿÿ^@^@^@^@^@^@^@^@ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿýÿÿÿÿÿÿÿþÿÿÿ^D^@^@^@^E^@^@^@^F^@^@^@^G^@^@^@þÿÿÿ  ^@^@^@þ
~
```

<!-- end_slide -->

CSV is just text
===

You can **write** it yourself, to some degree.

You can **read** it yourself, to some degree.

You will probably still be able to do so it in 50 years.

<!-- end_slide -->

CSV is a bridge
===

CSV can be handled by both **researchers**, **students** and **engineers** alike.

CSV is a good solution for a **tiny** data problem.

CSV is a good solution for a **big** data problem.

<!-- end_slide -->

An ethos of sobriety
===

Altough not exactly a chosen one ;)

---

* We don't have access to powerful hardware.
* Most of our users (students, researchers, civil society) don't have access to powerful hardware neither.

<!-- end_slide -->

CSV is naturally succinct
===

1. Headers are only written once
2. Strings are optimally represented (except for quotes)
3. Numbers could be lighter, but no order of magnitude to gain

<!-- end_slide -->

CSV is efficient
===

<!-- end_slide -->

CSV rewards clever engineering
===

<!-- end_slide -->

Conclusion
===

![flowchart](./img/database-flowchart.png)

<!-- end_slide -->

Thank you for your time !
===

Some CSV-relevant links:

* `médialab's Open Source`: https://github.com/medialab/
* `xan`: https://github.com/medialab/xan
* `minet`: https://github.com/medialab/minet
* `casanova`: https://github.com/medialab/casanova
* `table2net`: https://medialab.github.io/table2net/
* `takoyaki`: https://yomguithereal.github.io/takoyaki/
* `pelote`: https://github.com/medialab/pelote/