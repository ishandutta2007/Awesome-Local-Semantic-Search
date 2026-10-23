# Awesome-Local-Semantic-Search

## Top Local Semantic Search Ecosystem



**Curated List of SaaS Products & Open-Source GitHub Projects**  

*Focused on On-Device File Retrieval, Multimodal Embeddings & Self-Hosted Search Pipelines*  

**Last updated: October 2026**



This repository tracks notable **SaaS platforms** and **open-source projects** for **Local Semantic Search**. These tools enable users to find files on their own machine by describing what's inside them—not by remembering filenames or folder locations—using embedding models that map text, images, audio, and video into a shared vector space, with everything running locally and privately.



**Examples** include Glean, Notion AI, Hebbia, Coveo, and DigUp (the category leaders in their respective domains).



**Open-source emphasis**: This section is heavily expanded with every major active project for self-hosting, avoiding cloud document indexing, and retaining full control over personal data. The open-source landscape shifted dramatically in **October 2026** when Google DeepMind released **EmbeddingGemma 2** (Apache 2.0, 740M parameters), a multimodal embedding model small enough to run on a laptop . This triggered a wave of local search applications. The current open-source landscape is anchored by **DigUp** (the macOS/Linux/Windows multimodal search app built on EmbeddingGemma 2), **Recall** (the Linux equivalent with OCR and code search), and a growing ecosystem of Python libraries like **cairnsearch**, **vstash**, and **LSS** that provide hybrid BM25 + semantic retrieval for personal document collections.



Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.



## Table of Contents

- [Sector Overview & Market Dynamics](#sector-overview--market-dynamics)

- [SaaS/Hosted Platforms](#saas-hosted-platforms)

- [Open-Source GitHub Projects](#open-source-github-projects)

- [How to Contribute](#how-to-contribute)

- [Disclaimer](#disclaimer)



## Sector Overview & Market Dynamics

The global enterprise and cognitive search market is estimated at **$5.5B–$7.5B in 2025/2026** and projected to surpass **$14B+ by the early 2030s** at an 8–10% CAGR (with generative AI and semantic retrieval sub-segments growing above 15%). The sector is **moderately fragmented**: cloud hyper-scalers (Microsoft, Google, AWS) capture broad corporate infrastructure workloads, but independent AI search engines and vertical cognitive specialists maintain enduring moats around complex multi-source connectors, zero-retention enterprise privacy, and high-precision financial/legal knowledge retrieval rather than tilting into a single "winner-take-all" monopoly.



## SaaS/Hosted Platforms

| Platform | Company Scale (Valuation / Revenue) | Pricing (Starting Tier) | Free Tier / Trial Limits | Description |
| :--- | :--- | :--- | :--- | :--- |
| **[Notion AI](https://www.notion.com/product/ai)** | **~$11B–$12B valuation** (~$600M ARR) | **$20/member/month** (billed annually on Business plan) or $24/member/month (monthly) | **20 complimentary one-time AI responses** across workspace on Free/Plus tiers; no perpetual free AI allowance | AI layer for Notion workspaces covering Enterprise Search, meeting notes, research, and Q&A. Limited to workspace-connected knowledge. |
| **[Glean](https://www.glean.com/)** | **$7.2B valuation** (~$300M ARR) | **~$45/user/month** (estimated starting core seat license; contracts start at $25,000–$50,000/year minimum) | **No self-service free tier or trial**; vendor evaluations require sales-gated custom proof-of-concept (POC) demos | Cloud enterprise search and workplace assistant connecting across Slack, Google Drive, Jira, and enterprise apps. |
| **[Hebbia](https://www.hebbia.ai/)** | **$700M valuation** (~$30M–$48M ARR) | **$3,000/seat/year** (~$250/month, starting Lite/Consumer tier; Pro analyst tier at ~$10,000/seat/year) | **No self-service free tier or public trial**; pre-contract access strictly limited to negotiated sales pilots | AI research and matrix analysis platform tailored for finance, private equity, and legal document workflows. |
| **[Coveo](https://www.coveo.com/)** | **~$250M CAD market cap** (~$148M–$160M ARR) | **~$600/month** (estimated entry Base plan; standard ecosystem packages start at ~$990/month) | **14-day free trial** (desktop web setup, no credit card required); no ongoing perpetual free tier | AI relevance and search platform connecting multi-cloud, intranet, and enterprise systems at scale. |



## Open-Source GitHub Projects



- **[DigUp](https://github.com/ARahim3/DigUp)**  

  **The leading multimodal local search app.** Built on Google DeepMind's **EmbeddingGemma 2**, which maps text, images, audio, and video into one shared embedding space . **Platforms**: macOS (0.6.1, Apple Silicon), with Windows and Linux betas (0.7.0-beta.1) . **What it reads**: pictures and screenshots (by content and OCR text on Mac), PDFs page-by-page (up to 5,000 pages), documents (txt, md, docx, odt, html), audio in 30-second windows, and video (frame per shot plus soundtrack) . **Code search**: optional, finds functions by description (`code: retry a failed call with backoff`) or name, opens in your editor at the line . **Privacy**: everything runs locally; goes online only for the 865 MB model download and an optional update check . **MIT licensed**. **Caveats**: Windows/Linux beta lacks screenshot OCR, old .doc files, RAW photos, and SVG support ; first indexing pass can take hours for large photo libraries on CPU-only machines . Best for users wanting a polished, free, multimodal search app with no cloud dependency.



- **[Recall (pdstn12)](https://github.com/pdstn12/Recall)**  

  **The Linux equivalent with OCR and broader document support.** Also built on EmbeddingGemma 2 via llama.cpp . **Adds over DigUp**: OCR for scanned PDFs and screenshots, slide decks (pptx with speaker notes), spreadsheets (xlsx row-by-row), and code search. **Opens results at the match**: PDFs at the page (Evince, Okular, Zathura), videos at the moment (VLC, mpv), code in your editor . **No LLM**—it uses embedding vectors only, so it never generates content and has nothing to hallucinate. **Status**: Linux-only, recently released, smaller community than DigUp. Best for Linux users wanting OCR and broader format support in a local semantic search tool.



- **[cairnsearch](https://github.com/pdstn12/cairnsearch)**  

  **The research-backed hybrid search and local RAG system.** Published in SoftwareX, with a Zenodo release . **Architecture**: SQLite FTS5 BM25 + dense embeddings (nomic-embed-text via Ollama) fused with weighted max-normalized scoring (0.7 dense / 0.3 lexical) . **RAG engine**: local LLM (default llama3.1:8b via Ollama) answers questions from your documents with citations back to specific chunks . **Features**: PII detection (12 classes), optional AES-256 encryption, audit logging, quarantine for failed documents, async job queue . **Interfaces**: FastAPI REST, web UI, Typer CLI. **Performance**: tested on MacBook Pro M4 with 16 GB RAM for 100 mixed-format documents . Best for users wanting search plus local RAG with a research-grade architecture and strong privacy safeguards.



- **[vstash](https://github.com/stffns/vstash)**  

  **The lightweight document memory with hybrid search.** Uses FastEmbed (ONNX Runtime) for embeddings and sqlite-vec for vector storage—single .db file, zero dependencies . **Hybrid ranking**: BM25 (FTS5) + semantic via Reciprocal Rank Fusion. **Ask mode**: optional local LLM (Ollama) or fast cloud inference (Cerebras). **Multilingual**: search in any language with cross-lingual similarity . **Install**: `pip install vstash`. Best for users wanting a simple CLI-first tool for document Q&A with minimal setup.



- **[LSS (Local Semantic Search)](https://pypi.org/project/local-semantic-search/)**  

  **The hybrid BM25 + embeddings CLI with optional offline mode.** Default uses OpenAI embeddings if `OPENAI_API_KEY` is set; `pip install 'local-semantic-search[local]'` switches to bge-small-en-v1.5 (384d, ~125 MB) for fully offline operation . **Features**: file watching (`lss-sync`), filters by extension and regex, MMR for result diversity. **Formats**: 40+ code extensions, PDFs, docx, xlsx, pptx, csv. **Performance**: 0.91 NDCG@10 on a golden set . Best for developers wanting a scriptable semantic search over code and documents with offline capability.



- **[DeskSearch](https://pypi.org/project/desksearch/)**  

  **The desktop app with system tray and global hotkey.** Combines BM25 (tantivy) + dense retrieval (FAISS) via RRF . **Platforms**: macOS (dmg), Windows (exe), Linux (AppImage), plus pip CLI. **Features**: 30+ file formats, background daemon with file watching, plugins for parsers and rerankers. **Performance**: BM25 <10ms, semantic <200ms; ~500 files/min indexing on M1 . Best for users wanting a GUI-first desktop experience similar to DigUp but with broader platform support from day one.



- **[PKMRAG](https://pypi.org/project/pkmrag/)**  

  **The knowledge-graph-boosted hybrid search and MCP server.** Combines LanceDB vector engine, Tantivy BM25, and LadybugDB property graph for graph-proximity boosting . **MCP server**: exposes retrieval to AI agents (Claude Code, Cursor) without raw filesystem mutation risks. **Features**: semantic gap discovery (finds unlinked notes with high similarity), Obsidian wikilink resolution . Best for Obsidian users and developers wanting graph-aware search over personal knowledge bases.



### Additional Strong Open-Source Options



- **vectile** — Desktop search engine connecting Obsidian vaults, Calibre libraries, code repos, and Git history. Hybrid FTS5 + vector search with MCP server for AI assistants . Best for power users wanting one search across multiple knowledge sources.

- **semanticsearch (Go)** — Go library for embedding-based document search with SQLite or PostgreSQL+pgvector backends. Uses Gemma 300M, Nomic 768, or E5 Large 1024 models . Best for Go developers building custom local search into applications.

- **vstash** and **LSS** cover the Python CLI niche; **DeskSearch** and **DigUp** cover the GUI niche; **Recall** covers Linux-native needs; **PKMRAG** and **vectile** cover knowledge-graph and multi-source scenarios.

- **Frameworks for building custom systems**: Use **DigUp** for the most polished multimodal experience on macOS/Windows/Linux. Use **Recall** on Linux when OCR is required. Use **cairnsearch** when you want local RAG with citations. Use **vstash** or **LSS** for CLI-first document search. Use **PKMRAG** or **vectile** for Obsidian vaults and knowledge graphs.



## How to Contribute



1. Fork the repo.

2. Add/edit entries in `README.md` (follow existing format).

3. Include: name, link, 1–2 sentence description, and whether it's SaaS or open-source.

4. Submit PR with a short explanation.



Star the repo if you find it useful!



## Disclaimer



- This is a **community-curated** list — not exhaustive and not an endorsement.

- **"Local" means the search index and embeddings stay on your machine**: model downloads (EmbeddingGemma 2 is 865 MB), update checks, and optional cloud inference (vstash's Cerebras mode, LSS's default OpenAI embeddings) are separate network activities. Inspect your complete workflow before claiming privacy.

- **EmbeddingGemma 2 is the enabling technology for most recent local multimodal apps**: DigUp and Recall both build on it . Its Apache 2.0 license and 740M parameter size (small enough for laptops) made this category possible .

- **Platform support varies significantly**: DigUp's Windows/Linux builds are beta and lack some macOS features (screenshot OCR, RAW, SVG) ; Recall is Linux-only ; DeskSearch claims three-platform support . Verify your target platform before committing.

- **First indexing pass can be slow**: DigUp warns that a large photo library on CPU-only hardware can take hours . GPU acceleration reduces this but is not guaranteed on all systems.



---



**Made for privacy-conscious users, researchers, and anyone who believes finding a file shouldn't require remembering what it was called.**  

Let's make local semantic search more open, multimodal, and accessible.
