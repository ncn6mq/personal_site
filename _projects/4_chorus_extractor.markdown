---
layout: page
title: Chorus Extractor
image: chorus_extractor.jpg
description: Chorus Extractor
source: http://github.com/aerlinger/chorus_extractor
technologies: ["Ruby/Rubygems"]
---

A Ruby gem to extract chorus from lyrics by finding consecutive matching lines of text in a file.

To find patterns, each line is assigned a "diff score" based on the percentage of similar lines that exist within the same file computed via the McIlroy-Hunt Longest Common Subsequence (LCS) algorithm) Groups of consecutive lines with a high score are marked as being chorus lines.
