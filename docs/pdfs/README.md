# PDFs Directory

This directory is for storing PDF files that you want to embed in your blog posts.

## How to Add a PDF

1. Place your PDF file in this directory
2. Reference it in your blog post using one of these methods:

### Using iframe (Recommended)
```html
<iframe src="{{ site.baseurl }}/pdfs/your-file.pdf" width="100%" height="600px">
    <a href="{{ site.baseurl }}/pdfs/your-file.pdf">Download PDF</a>
</iframe>
```

### Using object tag
```html
<object data="{{ site.baseurl }}/pdfs/your-file.pdf" type="application/pdf" width="100%" height="600px">
    <a href="{{ site.baseurl }}/pdfs/your-file.pdf">Download PDF</a>
</object>
```

## Important Notes

- **File Size:** Keep PDFs under 25MB for best performance
- **File Names:** Use lowercase with hyphens (e.g., `my-document.pdf`)
- **Repository Size:** Be mindful of total repository size (GitHub recommends < 1GB)
- **Always Include Download Link:** Not all browsers support inline PDF viewing

## Examples

See these files for examples:
- [How to Embed PDF Files Guide](../how-to-embed-pdf-in-blog-post.md)
- [PDF Embedding Example Post](../2026-01-05-pdf-embedding-example.md)

## Alternative Hosting

For large PDFs or many files, consider:
- GitHub Releases
- Google Drive
- Dropbox
- AWS S3
- Other cloud storage services

Then use the external URL in your embed code.
