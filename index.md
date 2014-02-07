---
layout: default
title: Minzhao Liu
---
{% include JB/setup %}

# [About Me](about.html)

# [Project](pages/project.html)

- Falls Prevention Project
- [Effects of an Intervention to Increase Bed Alarm Use for Falls Prevention](http://annals.org/article.aspx?articleid=1392191)
- Detection of Unusual Test Administrations Using a Linear Mixed Effects Model
- [NBA Players Career Longevity](pages/survival-report.pdf)
- [Relationship between Mental Health and Workforce](pages/multi-report.pdf)
- [Yao Ming’s Effect on Houston Rockets](pages/cda-report.pdf)
- Bayesian Quantile Regression with Mixture of Polya Trees Prior (R package: [bqrpt](https://github.com/liuminzhao/bqrpt.git))
- Quantile Regression for Longitudinal Data with Monotone Missingness (R package: [qrmissing](https://github.com/liuminzhao/qrmissing))
- [scm_latexdiff](pages/scm-latexdiff.html)
- [Project Euler](https://github.com/liuminzhao/eulerproject)


# Recent Notes

<ul class="posts">
{% for post in site.posts limit:5 %}
<li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
{% endfor %}
</ul>
