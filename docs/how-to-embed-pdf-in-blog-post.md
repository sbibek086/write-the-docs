---
layout: default
title: How to Embed PDF Files in Blog Posts
category: Documentation
tags: [Tutorial, Jekyll, GitHub Pages]
---

# How to Embed PDF Files in Blog Posts

This guide shows you how to embed PDF files in your blog posts on this Jekyll/GitHub Pages blog.

## Methods to Embed PDFs

There are several ways to embed PDF files in your blog posts:

### Method 1: Using iframe (Recommended)

The `iframe` method is the most reliable and widely supported way to embed PDFs:

```html
<iframe src="/path/to/your-file.pdf" width="100%" height="600px">
    This browser does not support PDFs. Please download the PDF to view it: 
    <a href="/path/to/your-file.pdf">Download PDF</a>.
</iframe>
```

**Advantages:**
- Works in most modern browsers
- Allows scrolling through the PDF
- Responsive design possible
- Provides fallback link for unsupported browsers

### Method 2: Using object tag

The `object` tag is an HTML5 standard way to embed PDFs:

```html
<object data="/path/to/your-file.pdf" type="application/pdf" width="100%" height="600px">
    <p>Your browser does not support PDFs. 
    <a href="/path/to/your-file.pdf">Download the PDF</a>.</p>
</object>
```

**Advantages:**
- HTML5 standard
- Good browser support
- Can specify MIME type explicitly

### Method 3: Using embed tag

The `embed` tag is another option:

```html
<embed src="/path/to/your-file.pdf" type="application/pdf" width="100%" height="600px">
```

**Note:** This tag doesn't support fallback content as easily as `iframe` or `object`.

### Method 4: Using Google Docs Viewer

If your PDF is publicly accessible online, you can use Google Docs Viewer:

```html
<iframe src="https://docs.google.com/viewer?url=YOUR_PDF_URL&embedded=true" 
        width="100%" height="600px" frameborder="0">
</iframe>
```

Replace `YOUR_PDF_URL` with the full URL to your PDF file.

**Advantages:**
- Works even if browser doesn't have PDF support
- Provides Google's PDF viewer interface
- Good for publicly hosted PDFs

## Where to Store PDF Files

You have several options for storing your PDF files:

### Option 1: In the Repository (Recommended for small PDFs)

1. Create a `pdfs` or `assets` folder in your repository:
   - For example: `docs/pdfs/`
   
2. Add your PDF file to this folder

3. Reference it in your blog post:
   ```html
   <iframe src="{{ site.baseurl }}/pdfs/your-file.pdf" width="100%" height="600px"></iframe>
   ```

**Note:** Be mindful of repository size. GitHub recommends keeping repositories under 1GB.

### Option 2: Using GitHub Releases

1. Go to your repository's "Releases" section
2. Create a new release or use an existing one
3. Upload your PDF as a release asset
4. Copy the direct link to the PDF
5. Use that URL in your embed code

### Option 3: External Hosting

Host your PDF on:
- Google Drive (make sure it's publicly accessible)
- Dropbox
- AWS S3
- Any other web hosting service

Then use the full URL in your embed code.

## Complete Example

Here's a complete example of a blog post with an embedded PDF:

```markdown
---
layout: default
title: My Research Paper
category: Research
tags: [Academic, Paper]
---

# My Research Paper

Here's my latest research on topic XYZ.

## Abstract

This paper discusses...

## Full Paper

You can read the full paper below or [download it directly]({{ site.baseurl }}/pdfs/research-paper.pdf).

<iframe src="{{ site.baseurl }}/pdfs/research-paper.pdf" 
        width="100%" 
        height="600px" 
        style="border: 1px solid #ccc;">
    This browser does not support PDFs. Please download the PDF to view it: 
    <a href="{{ site.baseurl }}/pdfs/research-paper.pdf">Download PDF</a>.
</iframe>

## Conclusion

This research shows...
```

## Styling Tips

You can add CSS to make your embedded PDFs look better:

```html
<iframe src="{{ site.baseurl }}/pdfs/your-file.pdf" 
        width="100%" 
        height="600px" 
        style="border: 2px solid #333; border-radius: 5px; box-shadow: 0 2px 4px rgba(0,0,0,0.1);">
</iframe>
```

## Responsive Design

To make your PDF embed responsive on mobile devices:

```html
<div style="position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden;">
    <iframe src="{{ site.baseurl }}/pdfs/your-file.pdf" 
            style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; border: 0;">
    </iframe>
</div>
```

## Mobile Considerations

Keep in mind that:
- Some mobile browsers may not support inline PDF viewing
- Always provide a download link as a fallback
- Consider the file size - large PDFs may be slow to load on mobile networks
- Test your blog post on different devices

## Best Practices

1. **Always provide a download link** - Not all browsers support PDF embedding
2. **Set appropriate dimensions** - Usually 600px-800px height works well
3. **Test across browsers** - Check Chrome, Firefox, Safari, and Edge
4. **Optimize PDF size** - Compress PDFs to reduce loading time
5. **Add descriptive text** - Explain what the PDF contains
6. **Consider accessibility** - Provide alternative text and descriptions

## Troubleshooting

### PDF doesn't display
- Check the file path is correct
- Ensure the PDF file is committed to your repository
- Verify GitHub Pages has rebuilt your site (can take a few minutes)
- Try opening the direct PDF URL in your browser

### PDF shows in desktop but not mobile
- This is normal for some browsers
- Ensure you have a download link as fallback

### PDF is too large
- Compress your PDF using online tools
- Consider hosting it externally (Google Drive, Dropbox)
- Split large PDFs into smaller sections

## Example: Creating a PDF Blog Post

Let's create a complete example:

1. Create a `pdfs` folder in your `docs` directory:
   ```bash
   mkdir -p docs/pdfs
   ```

2. Add your PDF file to the folder

3. Create a new blog post `docs/2026-01-05-my-pdf-document.md`:

```markdown
---
layout: default
title: Important Document
category: Documents
tags: [PDF, Documentation]
---

# Important Document

This post contains an important PDF document.

## View Online

<iframe src="{{ site.baseurl }}/pdfs/important-doc.pdf" 
        width="100%" 
        height="600px" 
        style="border: 1px solid #ccc;">
    This browser does not support PDFs. 
    <a href="{{ site.baseurl }}/pdfs/important-doc.pdf">Download PDF</a>
</iframe>

## Download

[Download the PDF]({{ site.baseurl }}/pdfs/important-doc.pdf) to view offline.
```

4. Commit and push your changes
5. Wait for GitHub Pages to rebuild (2-3 minutes)
6. View your blog post!

## Summary

You can embed PDFs in your blog posts using:
- `<iframe>` tag (recommended)
- `<object>` tag
- `<embed>` tag
- Google Docs Viewer (for external PDFs)

Always provide a download link as fallback, and test on multiple devices!
