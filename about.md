---
layout: page
title: About
description: Course policies and information.
---

# About
{:.no_toc}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

{% assign overview = site.slides | where: "title", "Overview" | first %}
{{ overview.content }}

Administrative questions
: Pim Lustig <cse143@uw.edu>

Prerequisites
: CSE 142 or equivalent

Optional textbook
: Reges/Stepp, *Building Java Programs (5th Edition)*

## Values
{% assign values = site.slides | where: "title", "Values" | first %}
{{ values.content }}

## Deliberate practice
{% assign practice = site.slides | where: "title", "Deliberate practice" | first %}
{{ practice.content }}

## Academic honesty
{% assign honesty = site.slides | where: "title", "Academic honesty" | first %}
{{ honesty.content }}

## Grading
{% assign grading = site.slides | where: "title", "Grading" | first %}
{{ grading.content }}

## Access and accommodations

It is the policy and practice of the University of Washington to create inclusive and accessible learning environments consistent with federal and state law. If you have already established accommodations with [Disability Resources for Students](https://depts.washington.edu/uwdrs/) (DRS), activate your accommodations via myDRS so we can discuss how they will be implemented in this course.

If you have not yet established services through DRS, but have a temporary health condition or permanent disability that requires accommodations (conditions include but not limited to; mental health, attention-related, learning, vision, hearing, physical or health impacts), contact DRS directly to set up an Access Plan. DRS facilitates the interactive process that establishes reasonable accommodations.

## Extenuating circumstances

We recognize that our students come from varied backgrounds and can have widely-varying circumstances. If you have any unforeseen or extenuating circumstances that arise during the course, do not hesitate to contact the instructor by [appointment](https://kevinl.info/meet/), via email, or private post to discuss your situation. The sooner we are made aware, the more easily these situations can be resolved. Extenuating circumstances include work-school balance, familial responsibilities, religious observations, military duties, unexpected travel, or anything else beyond your control that may negatively impact your performance in the class.

Washington state law requires that UW develop a policy for accommodation of student absences or significant hardship due to reasons of faith or conscience, or for organized religious activities. The UW's policy, including more information about how to request an accommodation, is available at [Religious Accommodations Policy](https://registrar.washington.edu/staffandfaculty/religious-accommodations-policy/). Accommodations must be requested within the first two weeks of this course using the [Religious Accommodations Request form](https://registrar.washington.edu/students/religious-accommodations-request/).

## Inclusive community

This course welcomes all students of all backgrounds. The computer science and computer engineering industries have significant lack of diversity. This is due to a lack of sufficient past efforts by the field toward even greater diversity, equity, and inclusion. The Allen School seeks to create a more diverse, inclusive, and equitable environment for our community and our field. You should expect and demand to be treated by your classmates and the course staff with respect. If any incident occurs that challenges this commitment to a supportive, diverse, inclusive, and equitable environment, please let the instructor know so the issue can be addressed. Should you feel uncomfortable bringing up an issue with the instructor directly, submit [anonymous feedback](https://feedback.cs.washington.edu) or contact the [Office of the Ombud](https://www.washington.edu/ombud/).

*[IPL]: Introductory Programming Lab
