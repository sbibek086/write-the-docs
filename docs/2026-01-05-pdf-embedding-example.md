---
layout: default
title: Example - Embedding PDF in Blog Post
category: Tutorial
tags: [Example, PDF, Tutorial]
---

# Example: Embedding PDF in Blog Post

This is an example blog post that demonstrates how to embed PDF files.

## Introduction

This post shows you practical examples of embedding PDF documents in your blog posts. You can use any of the methods described in the [How to Embed PDF Files guide](how-to-embed-pdf-in-blog-post.md).

## Method 1: Using iframe

Here's an example using the `iframe` tag to embed a PDF:

```html
<iframe src="{{ site.baseurl }}/pdfs/your-document.pdf" 
        width="100%" 
        height="600px" 
        style="border: 1px solid #ccc;">
    This browser does not support PDFs. 
    <a href="{{ site.baseurl }}/pdfs/your-document.pdf">Download PDF</a>
</iframe>
```

**Note:** To see this in action, you need to add a PDF file named `your-document.pdf` to the `docs/pdfs/` folder.

## Method 2: Using object tag

Here's the same PDF embedded using the `object` tag:

```html
<object data="{{ site.baseurl }}/pdfs/your-document.pdf" 
        type="application/pdf" 
        width="100%" 
        height="600px">
    <p>Your browser does not support PDFs. 
    <a href="{{ site.baseurl }}/pdfs/your-document.pdf">Download the PDF</a>.</p>
</object>
```

## Method 3: Embedding External PDF

If your PDF is hosted externally (e.g., on Google Drive), you can use Google Docs Viewer:

```html
<iframe src="https://docs.google.com/viewer?url=https://example.com/your-file.pdf&embedded=true" 
        width="100%" 
        height="600px" 
        frameborder="0">
</iframe>
```

## Download Link

Always provide a direct download link for users:

[Download the sample document]({{ site.baseurl }}/pdfs/your-document.pdf)

## Tips for Your Own Posts

1. **Replace the path:** Change `/pdfs/your-document.pdf` to your actual PDF filename
2. **Adjust dimensions:** Modify `width` and `height` to suit your content
3. **Add styling:** Use inline CSS or add classes for better appearance
4. **Test on mobile:** Check how it looks on different devices

## Step-by-Step: Adding Your PDF

1. Create the `pdfs` folder if it doesn't exist:
   ```
   docs/pdfs/
   ```

2. Add your PDF file to the folder:
   ```
   docs/pdfs/my-research-paper.pdf
   ```

3. Create your blog post (e.g., `2026-01-05-my-research.md`):
   ```markdown
   ---
   layout: default
   title: My Research Paper
   ---
   
   # My Research Paper
   
   <iframe src="{{ site.baseurl }}/pdfs/my-research-paper.pdf" 
           width="100%" 
           height="600px">
   </iframe>
   
   [Download PDF]({{ site.baseurl }}/pdfs/my-research-paper.pdf)
   ```

4. Commit and push:
   ```bash
   git add docs/pdfs/my-research-paper.pdf
   git add docs/2026-01-05-my-research.md
   git commit -m "Add research paper with embedded PDF"
   git push
   ```

5. Wait 2-3 minutes for GitHub Pages to rebuild

6. View your post!

## Conclusion

Embedding PDFs in blog posts is straightforward. Choose the method that works best for your needs, and always provide a download link as a fallback option.

For more details, see the complete [PDF Embedding Guide](how-to-embed-pdf-in-blog-post.md).
