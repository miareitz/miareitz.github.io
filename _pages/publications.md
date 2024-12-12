---
layout: page
permalink: /publications/
title: Publications
description: Publications by categories and years in reversed chronological order.
sections:
  - bibquery: "@article"
    text: "Journal Articles"
  - bibquery: "@inproceedings"
    text: "Conference and Workshop Articles"
  - bibquery: "@conference"
    text: "Posters and Extended Abstracts"
  - bibquery: "@phdthesis"
    text: "Dissertation"
  - bibquery: "@misc"
    text: "Other"
nav: true
nav_order: 2
years: [2025, 2024, 2023, 2022, 2021, 2020, 2019, 2018]
---

<!-- _pages/publications.md -->

<!-- Bibsearch Feature -->

{% include bib_search.liquid %}

<div class="publications">

{%- for section in page.sections %}
  <a id="{{section.text}}"></a>
  <h1>{{section.text}}</h1>
  {%- for y in page.years %}

    {%- comment -%}  Count bibliography in actual section and year {%- endcomment -%}
    {%- capture citecount -%}
    {%- bibliography_count -f {{site.scholar.bibliography}} -q {{section.bibquery}}[year={{y}}] -%}
    {%- endcapture -%}

    {%- comment -%} If exist bibliography in actual section and year, print {%- endcomment -%}
    {%- if citecount !="0" %}

      {% bibliography -f {{site.scholar.bibliography}} -q {{section.bibquery}}[year={{y}}] %}

    {%- endif -%}

  {%- endfor %}

{%- endfor %}

</div>
