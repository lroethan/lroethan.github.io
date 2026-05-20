---
permalink: /
title: "Zhicheng Pan"
author_profile: true
redirect_from: 
  - /about/
  - /about.html
---

I am an incoming postdoctoral fellow at <a href="https://www.cuhk.edu.hk/english/">The Chinese University of Hong Kong (CUHK)</a>, where I will work with <a href="https://www.se.cuhk.edu.hk/people/academic-staff/prof-wang-sibo/">Prof. Sibo Wang</a>. I received my Ph.D. from the School of Data Science and Engineering at <a href="https://english.ecnu.edu.cn/">East China Normal University (ECNU)</a>, advised by <a href="https://baike.baidu.com/en/item/Zhou%20Aoying/34989">Prof. Aoying Zhou</a> and <a href="https://ychengc.github.io/">Prof. Chengcheng Yang</a>. My current research interests center on the interaction between large language models and query optimizers.

I previously visited the Database Research Group at <a href="https://www.hkbu.edu.hk/">Hong Kong Baptist University (HKBU)</a>, where I collaborated with IEEE Fellow <a href="https://www.comp.hkbu.edu.hk/~xujl/">Prof. Jianliang Xu</a>. I have also worked as a research intern at Tencent with Huichao Duan, at PingCAP TiDB with Yuanjia Zhang, Terry Purcell, and Yu Dong, and at Alibaba Cloud with Yingying Zhang and Qingsong Wen. Earlier, I was a data development intern at Taobao, working with Huajun Deng.

## Selected Publications {#selected-publications}

> *<sup>#</sup> indicates co-first authors; <sup>*</sup> indicates corresponding authors.*

{% assign first_author_publications = site.publications | where: "category", "first_author" | sort: "date" | reverse %}
{% for publication in first_author_publications %}
* {{ publication.citation }}
{% endfor %}

{% assign coauthored_publications = site.publications | where: "category", "coauthored" | sort: "date" | reverse %}
{% for publication in coauthored_publications %}
* {{ publication.citation }}
{% endfor %}

## Awards and Grants {#awards-and-grants}

- Shanghai Outstanding Graduate, 2026. （上海市优秀毕业生）
- 1st Young Elite Scientists Sponsorship Program (Doctoral Program), China Association for Science and Technology (CAST). 3,226 nationwide. （中国科协青年人才托举工程博士生专项计划）
- Outstanding Student Honor, East China Normal University, 2024.
- ECNU Academic Innovation Promotion Program for Excellent Doctoral Students (YBNLTS2024-017).
- First Prize for Outstanding Student, VLDB Summer School, 2023 (1st Place).
- First Prize, Industry Scholarship, School of Data Science and Engineering, 2023 (1st Place).
- Postgraduate Research & Practice Innovation Program of Jiangsu Province (SJCX2_11342).
- Outstanding Graduate, Soochow University, 2019 & 2022.
- "Information technology-General spatiotemporal information application support platform-Reference architecture" (T/CIE 131-2022). Main Drafter.
