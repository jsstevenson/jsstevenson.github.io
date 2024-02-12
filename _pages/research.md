---
layout: page
title: research
permalink: /research/
description: ""
nav: true
nav_order: 3
horizontal: false

---
<p><span style="font-weight: bold;">Therapy concept normalization.</span> Explored referential ambiguity for drug and therapy terms in biomedical databases and literature. Performed in support of the <a href="https://cancervariants.org/projects/integration/">Knowledgebase Integration project</a> of the Variant Interpretation for Cancer Consortium (VICC).</p>

<ul style="list-style-type: none; padding-left: 10px; ">
  <li>
    {% assign item_link = site.research | where:"title", "TheraPy @ CGC 2022" | first %}
    <a href="{{ item_link.url }}"
      ><i class="fa-solid fa-chart-area list-dot" style="padding-right: 11px;"></i>CGC 2022: Normalizing therapy concepts</a
    >
  </li>
  <li>
    {% assign item_link = site.research | where:"title", "TheraPy @ CGC 2023" | first %}
    <a href="{{ item_link.url }}"
      ><i class="fa-solid fa-person-chalkboard list-dot" style="padding-right: 7px;"></i>CGC 2023: Challenges in semantic alignment of therapeutic knowledge</a
    >
  </li>
  <li>
    <a href="https://academic.oup.com/jamiaopen/article/6/4/ooad093/7388192"
      ><i class="fa-solid fa-file-alt list-dot" style="padding-right: 15px;"></i>JAMIA Open 6.4 (2023): Normalization of drug and therapeutic concepts with Thera-Py</a
    >
  </li>
  <li>
    <a href="https://academic.oup.com/nar/advance-article/doi/10.1093/nar/gkad1040/7416371"
      ><i class="fa-solid fa-file-alt list-dot" style="padding-right: 15px;"></i>Nucleic Acids Research (2024): DGIdb 5.0: rebuilding the drug–gene interaction database for precision medicine and drug discovery platforms</a
    >
  </li>
</ul>
