---
title: "Dense Retrievers Know More Than They Can Express"
url: "https://www.mixedbread.com/blog/latent-terms"
date: "2026-06-02"
author: "Mixedbread Team, Benjamin Clavie, Sean Lee, Rui Huang"
feed_url: "https://www.mixedbread.com/blog"
---
This research challenges conventional thinking about neural retrieval models, demonstrating that dense retrievers learn richer information than their standard scoring mechanisms can express. Using Sparse AutoEncoders, the team extracts Latent Terms — a sparse vocabulary hidden within dense retrievers that follows a natural language-like Zipfian distribution and works effectively with traditional lexical approaches like BM25. Combining these latent terms with BM25 produces competitive retrieval performance, even outperforming some specialized sparse methods like SPLADE-v3, without additional training.
