# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Tags File Priority

Upon initialization, **always check for an existing tags file** before performing extensive codebase analysis.

### Discovery Locations

Check for tags files in this order:
1. Project root: `tags`, `.tags`, `TAGS`
2. Tags directory: `/tags/tags`, `/tags/.tags`, `/tags/TAGS`

### Initialization Behavior

**When tags file exists:**
1. Parse the tags file to extract codebase structure
2. Build an index of:
   - Function and method definitions
   - Class and type declarations
   - Module and namespace boundaries
   - File locations and relationships
3. Use this index as the primary source of codebase context
4. Only read specific files when detailed implementation context is needed

**When tags file is missing:**
- Proceed with standard file-by-file analysis as needed
- Consider suggesting the user generate tags for better performance

### Fallback Strategy

Use direct file reading when:
- Tags file is outdated or incomplete
- Need to understand implementation details beyond signatures
- Working with dynamically generated code not captured in tags
- User explicitly requests file-level analysis

### Benefits

- **10-100x faster** codebase context acquisition
- Reduced token usage during initialization
- Lower latency for first response
- Leverage existing developer tooling
- More efficient for large codebases (1000+ files)

### Supported Formats

- **Ctags**: Universal Ctags, Exuberant Ctags (most common)
- **Etags**: Emacs tags format
- Both formats provide: symbol name, file path, line number, kind (function/class/variable)

### Tags File Generation

If no tags file exists, users can generate one with:
```bash
# Universal Ctags (recommended)
ctags -R .

# With additional options for better coverage
ctags -R --fields=+iaS --extras=+q .
```

---

*Note: This repository is currently empty. This file will be updated with project-specific commands, architecture, and structure once code is added.*
