---
layout: page
title: "Project"
description: ""
group: navigation
---
{% include JB/setup %}

# Research Assistant Projects

- Falls Prevention Project

	On October 1, 2008, Medicare implemented a policy denying incremental payment for eight hospital-acquired conditions, also known as ‘never events’. Prior to this time quality incentives were almost uniformly formulated to reward specific behavior and outcomes rather than punish undesirable ones. Since adoption of this policy, other negative incentives have been put into place, most notably penalties for readmissions.

	We explored the impact of Medicare’s nonpayment policy for hospital-acquired condition, such as hospital-acquired pressure ulcers (HAPUs), injurious inpatient falls,  central line-associated blood stream infections (CLABSIs), and catheter-associated urinary tract infections (CAUTIs).

	We fit negative binomial models to detect changes in both the rate level (intercept) as well as changes in the time trend before/after the CMS policy change (slope). Because our paper is still under review, I can not put more details here.

	This project is led by [Teresa M. Waters][teresa]. My advisor ([Dr. Mike Daniels][mike]) and I are the major data analysts and statistical consultants.

- [Effects of an Intervention to Increase Bed Alarm Use for Falls Prevention](http://annals.org/article.aspx?articleid=1392191)

	In this project, we aimed to investigate whether an intervention aimed at increasing bed alarm use decreases hospital falls and related events.

	We implemented a pair-matched negative binomial model with random effects for the cluster randomized design.

	This project was led by [Ronald Shorr, MD][ron]. My advisor ([Dr. Mike Daniels][mike]) and I are still the major data analysts and statistical consultants. And this work has been published on [Ann Intern Med 2012;157:692-699](http://annals.org/article.aspx?articleid=1392191).

# Intern Project

- Detection of Unusual Test Administrations Using a Linear Mixed Effects Model

	With an increase in the number of administrations of test forms, there is also an increase in the complexity of the quality assurance procedures needed to maintain the stability of the reported scores. Many traditional methods for quality control are not sufficient for detecting unusual scores in a rapid flow of administrations, for which new QC approaches have been proposed in recent years. In this study we investigate data from 15 consecutive administrations that follow a specific equating design (or braiding plan) and propose a linear mixed effect model for the detection of abnormal results. In this project we investigate the effects of the braiding plans and estimate the effects of several identified factors that influence the means and variances of the scale scores. This analysis is appropriate for tests with a continuous or almost continuous administration mode. The data are from a global standardized assessment of English skills. Reading and Listening sections of the English test were modeled separately. Test takers’ education level, major, years abroad, years of study, and whether they repeated the test turned out to have significant effects on the scores. In addition, a formula for a prediction interval for the scaled mean score of certain subgroups was proposed to detect unusual administrations.

	This paper is a joint work with my intern supervisor, Yi-Hsuan Lee and Alina von Davier. It has been presented on [IMPS 2012 conference](http://conferences.unl.edu/upcoming-programs/international-meeting-of-psychometric-society.aspx) and to be appeared as a chapter in *New Developments in Quantitative Psychology*.

# Course Projects

- [NBA Players Career Longevity](survival-report.pdf)

	In this project, we used information from [basketball-reference.com](http://www.basketball-reference.com/) to predict NBA players' mean residual life which means how long they can still play, and to find out which factors are important to improve players’ career lifespan.

	We use *weibull*, *log-logistic*, *lognormal*, and *coxph* model to fit the model with stepwise method. For each method, we check if the model is well fitted by Nelson-Aalen estimator and assess linearity, Cox-Snell residuals, deviance residuals, and score residuals. Proportional assumption is also verified.

	From our model, we are able to get an estimation of mean residual life. It will be a useful indicator for the team owners to offer contracts to players. Also the method may help players to decide their training plan, in order to extend their career length.

	This was a course project for *Survival Analysis* taught by *Dr. Mike Daniels*, a joint work with *Che-shun Chang* and *Xuan Luo*.

- [Relationship between Mental Health and Workforce](multi-report.pdf)

	In this project we tried to figure out the relationship between mental health and personal demographic, family and working information. Dataset was brought by a national study of United States in 2008. Multivariate regression, canonical correlation analysis, discrimination analysis and cluster analysis were adopted and reasonable interpretations were made by results from four methods. Some defects are also mentioned in the last section of the article.

	This was a course project for *Multivariate Data Analysis* taught by *Dr. Trevor Park*, a joint work with *Xuan Luo*.

- [Yao Ming’s Effect on Houston Rockets](cda-report.pdf)

	This project mainly uses binary generalized linear models to analyze the data from NBA players. By logistic model, the data from Yao Ming was used to predict odds to win. Results show certain covariates are selected to be significantly related to team victory. This model also presents how personal behaviors change game result and how odds ratio varies between various divisions. Those conclusions may help coach to design strategy for some particular player and particular opponents. Longitudinal perspective, link function test and overdispersion situation are also discussed in this article.

	This was a course project for *Categorical Data Analysis* taught by *Dr. Alan Agresti*.

# Personal Projects

- Bayesian Quantile Regression with Mixture of Polya Trees Prior (R package: [bqrpt](https://github.com/liuminzhao/bqrpt.git))

- Quantile Regression for Longitudinal Data with Monotone Missingness (R package: [qrmissing](https://github.com/liuminzhao/qrmissing))

- [scm_latexdiff](scm-latexdiff.html)

	A fork of Diff Tool for LaTeX and Git.

- [Project Euler](https://github.com/liuminzhao/eulerproject)

	This is my solution by Python for the first almost 100 problems on [Project Euler](http://projecteuler.net/),  also as an exercise to practice Python.

[teresa]: https://academic.uthsc.edu/faculty/facepage.php?netID=twaters1&personnel_id=132640
[mike]: http://www.sbs.utexas.edu/mjdaniels/index.html
[ron]: https://ufhealth.org/ronald-shorr
