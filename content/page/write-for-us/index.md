---
title: "Write for Us"
description: "Become a contributor to the blog."
menu:
    main:
        weight: 3
        params:
            icon: "messages"
---

We welcome contributions from the community! Whether it's a technical tutorial, a deep dive into Swift/Go features, or a career advice piece, we'd love to host it.

## The Developer Way (GitHub Workflow)

Since this blog is open source, contributing is as simple as submitting a Pull Request (PR).

### 1. Fork & Clone
1.  Go to [our GitHub repo](https://github.com/ckdash-git/blogs) and click the **Fork** button in the top-right corner.
2.  Clone your fork locally:
    ```bash
    git clone https://github.com/<YOUR-USERNAME>/blogs.git
    cd blogs
    ```
3.  Create a new branch for your post:
    ```bash
    git checkout -b post/my-new-article
    ```

### 2. Create Your Post
We use **Page Bundles** to keep images and content organized.

1.  Create a new folder in `content/blogs/` with your slug (URL friendly name):
    ```bash
    mkdir content/blogs/my-awesome-post
    ```
2.  Create an `index.md` file inside that folder.
3.  Copy and paste the following **Front Matter** at the top of your `index.md` file:

    ```markdown
    ---
    title: "My Awesome Post Title"
    date: 2026-02-07
    description: "A short, catchy summary of your article."
    image: "hero-image.png" # Optional: Place image in the same folder
    authors: ["your-github-username"]
    tags: ["Swift", "Tutorial", "Beginner"]
    ---
    
    Start writing your content here...
    ```

### 3. Writing Content
*   **Images**: Place image files directly in your post folder (e.g., `content/blogs/my-awesome-post/screenshot.png`) and reference them simply by filename: `![Alt Text](screenshot.png)`.
*   **Code Blocks**: Use triple backticks with the language name for syntax highlighting:
    ```swift
    func hello() {
        print("Hello, World!")
    }
    ```

### 4. Submit Your Changes
1.  Commit your changes:
    ```bash
    git add .
    git commit -m "Add post: My Awesome Post"
    ```
2.  Push to your fork:
    ```bash
    git push origin post/my-new-article
    ```
3.  Go to the [original repository](https://github.com/ckdash-git/blogs) and click **Compare & pull request**.

## Style Guide

*   **Tone**: Friendly, professional, and educational.
*   **Formatting**: Use **bold** for key concepts and *italics* for emphasis.
*   **Headings**: Use `## H2` for main sections and `### H3` for subsections.
*   **Length**: Aim for 500-1500 words. Quality > Quantity.

We'll review your PR, suggest edits if needed, and merge it once it looks good. Happy writing!
