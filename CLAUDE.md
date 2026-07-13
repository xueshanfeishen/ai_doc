# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This repository contains a single Python script that generates a Chinese-language PDF covering LLM (Large Language Model) and AI Agent development concepts, interview questions, and answers. It's a study/reference document generator.

## Commands

```bash
# Generate the PDF
python generate_llm_agent_pdf.py
```

Output is written to `C:\Users\Administrator\Desktop\大模型与Agent开发_概念及面试题集.pdf`.

## Architecture

`generate_llm_agent_pdf.py` — Self-contained PDF generator (~1500 lines):

- **`ChinesePDF` class** (extends `fpdf.FPDF`): Custom PDF renderer with Chinese font support using Windows Deng (等线) fonts. Provides methods for styled chapter titles, body text, interview questions/answers, key points, and a cover page with table of contents.
- **Content is organized into five parts**: (1) LLM core concepts (Transformer, RLHF, LoRA, RAG, quantization, etc.), (2) Agent development core concepts (ReAct, Function Calling, Planning, Memory, Multi-Agent, LangChain, etc.), (3) LLM interview Q&A, (4) Agent development interview Q&A, (5) Comprehensive scenario-based Q&A. An appendix provides a terminology reference table.
- **Auto-installs `fpdf2`** via pip if not already available.
- **Font dependency**: Requires `Deng.ttf`, `Dengb.ttf`, `Dengl.ttf` in `C:\Windows\Fonts\`. Falls back to the regular weight font if bold/light variants are missing.

## Modifying Content

Content is inline in the `generate_pdf()` function. To add or edit content:
- Add/reorder sections within the appropriate numbered part using `pdf.chapter_title()`, `pdf.body_text()`, `pdf.key_point()` calls
- Add new interview Q&A pairs using `pdf.question()` and `pdf.answer()` calls
- Add terminology entries to the `terms` list in the appendix section
