---
name: hwpx-export
description: Converts final markdown business plan to hwpx (Hangul) file. Responds to: hwpx, 한글, 변환, export, 제출 파일, 최종 문서.
argument-hint: "[markdown file path] (default: final/사업계획서.md)"
---

# hwpx Conversion Workflow

## Overview
`final/사업계획서.md` → 한글변환기 sub-agent → `final/사업계획서.hwpx`

## Prerequisites
- `final/사업계획서.md` must exist (run 문서통합자 agent first)
- hwpx MCP server must be running (registered in `.mcp.json`)
- Install: `pip install hwpx-mcp-server` or `uvx hwpx-mcp-server`

## Workflow

### Step 1: Source Verification
Read `final/사업계획서.md` to understand content and structure.

### Step 2: Invoke 한글변환기 Agent
Pass to the sub-agent:
- Full markdown content
- Format specs from project.yaml `document.format`
- Output path: `final/사업계획서.hwpx`

### Step 3: Verification
Verify the generated hwpx file:
1. `get_document_info` — check metadata
2. `get_document_outline` — verify section structure
3. `get_document_text` — check for missing content

### Step 4: Completion
- Report file path
- Remind: manual verification in Hangul program needed (font, line spacing)

## Format Specs
Refer to project.yaml `document.format`:

| Item | Value |
|------|-------|
| Font | project.yaml `document.format.font_hwpx` |
| Size | project.yaml `document.format.font_size` |
| Line spacing | project.yaml `document.format.line_spacing` |
| Margins | project.yaml `document.format.margins` |
| Summary | 1 page (page break before body) |

## hwpx MCP Tool Mapping

### Document Creation Order
1. `copy_document` — start from blank template
2. `create_custom_style` — create body/heading styles (per project.yaml format)
3. `add_heading` — add section titles
4. `add_paragraph` — add body text (with style)
5. `add_table` — add tables
6. `set_table_cell_text` — fill table cells
7. `format_table` — format tables
8. `add_page_break` — page break between summary and body

### Markdown → hwpx Element Mapping
| Markdown | hwpx Tool |
|----------|-----------|
| `# Title` | `add_heading` (level=1) |
| `## Subtitle` | `add_heading` (level=2) |
| Plain text | `add_paragraph` |
| `\| table \|` | `add_table` + `set_table_cell_text` |
| `---` (divider) | `add_page_break` (summary/body separator) |
| **bold** | `format_text` (bold) |

## Notes
- hwpx MCP is stateless — `filename` required in every tool call
- Large content additions may timeout — add in section-sized chunks
- Font name must match exact system-installed name
- Final verification must be done visually in Hangul program

## Incremental Update (/한글수정)
If an hwpx file already exists, apply only changes instead of full regeneration:
- `/한글수정` detects md changes and applies incremental updates to hwpx
- MCP tools used: `search_and_replace`, `batch_replace`, `delete_paragraph`, `insert_paragraph`
- Preserves existing styles — faster and safer than full regeneration
