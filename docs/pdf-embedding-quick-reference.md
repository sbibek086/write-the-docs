# PDF Embedding Quick Reference

Quick reference for embedding PDFs in blog posts.

## Quick Start

### 1. Add your PDF
Place your PDF file in `docs/pdfs/your-file.pdf`

### 2. Embed in your blog post

**Basic iframe (recommended):**
```html
<iframe src="{{ site.baseurl }}/pdfs/your-file.pdf" width="100%" height="600px">
    <a href="{{ site.baseurl }}/pdfs/your-file.pdf">Download PDF</a>
</iframe>
```

**With styling:**
```html
<iframe src="{{ site.baseurl }}/pdfs/your-file.pdf" 
        width="100%" 
        height="600px" 
        style="border: 1px solid #ccc; border-radius: 5px;">
    <a href="{{ site.baseurl }}/pdfs/your-file.pdf">Download PDF</a>
</iframe>
```

### 3. Add download link
```markdown
[Download PDF]({{ site.baseurl }}/pdfs/your-file.pdf)
```

## All Methods

| Method | Code |
|--------|------|
| **iframe** | `<iframe src="{{ site.baseurl }}/pdfs/file.pdf" width="100%" height="600px"></iframe>` |
| **object** | `<object data="{{ site.baseurl }}/pdfs/file.pdf" type="application/pdf" width="100%" height="600px"></object>` |
| **embed** | `<embed src="{{ site.baseurl }}/pdfs/file.pdf" type="application/pdf" width="100%" height="600px">` |
| **Google Viewer** | `<iframe src="https://docs.google.com/viewer?url=URL&embedded=true"></iframe>` |

## Complete Example

```markdown
---
layout: default
title: My Document
---

# My Document

View the document below:

<iframe src="{{ site.baseurl }}/pdfs/my-doc.pdf" 
        width="100%" 
        height="600px" 
        style="border: 1px solid #ccc;">
    <a href="{{ site.baseurl }}/pdfs/my-doc.pdf">Download PDF</a>
</iframe>

[Download PDF]({{ site.baseurl }}/pdfs/my-doc.pdf)
```

## Checklist

- [ ] PDF added to `docs/pdfs/` folder
- [ ] Filename is lowercase with hyphens
- [ ] File size is reasonable (< 25MB)
- [ ] Embed code added to blog post
- [ ] Download link provided
- [ ] Tested on desktop browser
- [ ] Tested on mobile browser

## Resources

- [Complete Guide](how-to-embed-pdf-in-blog-post.md)
- [Example Post](2026-01-05-pdf-embedding-example.md)
- [PDFs Directory](pdfs/README.md)
