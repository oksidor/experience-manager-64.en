---
title: Request Analysis Script
seo-title: Request Analysis Script
description: null
seo-description: The request analysis script is made to ease the analysis of the access.log files producing a readable report for later processing
uuid: 4c11ec42-a305-4840-8720-be08eaf6cb06
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: testing
content-type: reference
discoiquuid: 0a322026-6b80-460e-b298-ce933fdccdc3
isreadyforlocalization: false
index: y
internal: n
snippet: y
---

# Request Analysis Script{#request-analysis-script}

## Download {#download}

[This script is made to ease the analysis of the access.log files producing a readable report for later processing.](assets/analyse-access.sh)

## Description {#description}

This script is made to ease the analysis of the access.log files producing a readable report for later processing.

It produces the overall requests number, GET vs POST, Request distribution over time and more.

The output will be in Markdown syntax therefore it will be easier to convert it to PDFs with tools like pandoc or showing it in a browser with plugins like markdown viewer.

It can analyse as well custom path provided on the command line.

Taking from the comment within the file that will tell you how to run it:

Analyse CQ access.log extrapolating various informations and producing a MarkDown output on stdout

## Usage {#usage}

# ./analyse-access.sh access.log.2013-&#42;

#

# you can provide additional custom paths to analyse on the command line

# ./analyse-access.sh access.log.2013-&#42; /my/custom/path/1 /my/custom/path/2

#

# you can save the output by a simple piping

# ./analyse-access.sh access.log.2013-&#42; | tee yr2013.md