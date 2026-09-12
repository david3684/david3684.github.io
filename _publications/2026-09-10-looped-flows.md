---
layout: single
title: "Thinking with Looped Flows"
collection: preprints
date: 2026-09-10 22:21:59 +00:00
categories: research
author: "Chanhyuk Lee"
authors: "Ayhan Suleymanzade, <u>Chanhyuk Lee</u>, Floor Eijkelboom, Nicholas M. Boffi, İsmail İlkan Ceylan†, Jinwoo Kim†"
venue: "Preprint"
under_review: true
arxiv: https://arxiv.org/abs/2609.11801
arxiv_id: "2609.11801"
code:
project:
paperurl:
bibtexurl:
citation:
note:
abstract: "Humans and machines often solve harder problems by spending more time on computation. In deep learning, looped models implement this idea during inference by recurrently updating a hidden state. In practice, however, their training backpropagates through only one or a few updates, making it hard to train early updates to support future ones. We propose looped flows, an approach that sidesteps this issue by training the recurrence with local denoising objectives. By imposing temporal association across denoising objectives through progressively decreasing noise levels and shared noise, the model is incentivized to learn recurrent states that transfer useful computation over time, even when gradients cover only a few updates. We then formulate inference as integrating the velocity of a probability flow parameterized by the learned denoiser, coupled with recurrent states. This allows solving harder problems by spending more computation through a finer temporal grid and enables multiple valid predictions from different initial noise samples. Across six reasoning benchmarks including two multi-solution benchmarks, looped flows outperform prior state-of-the-art looped models overall, achieving 58.8% test accuracy on ARC-AGI-1 and 12.2% on ARC-AGI-2."
---
