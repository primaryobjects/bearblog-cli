# BearBlog CLI

A simple (unofficial) command-line interface for managing your BearBlog posts. Create, list, and delete posts without needing the web dashboard.

> **Note:** This tool works with the free BearBlog plan. Publish, update, and unpublish operations are not available on the free plan.

## Features

- ✅ List all blog posts with IDs and titles
- ✅ Create new posts from markdown files
- ✅ Delete posts by ID
- ✅ Lightweight, single Python script
- ✅ No Web UI dependency

## Installation

1. Clone or download this repository
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Configure your BearBlog credentials by creating a `.bearblog` file in the project root:
   ```bash
   EMAIL=your-email@example.com
   PASSWORD=your_password
   BLOG_NAME=your-subdomain
   ```
   You can find your blog name in your BearBlog dashboard URL (e.g., `https://bearblog.dev/your-subdomain`).

## Usage

```
usage: bearcli.py [-h] {list,new,load,delete} ...

BearBlog CLI (Free Plan)

Examples:
  bearcli list
  bearcli new "My Post Title" --file post.md
  bearcli load abc123xyz
  bearcli delete abc123xyz

Note: publish, unpublish, and update are disabled on the free plan.

positional arguments:
  {list,new,load,delete}
    list                List all posts in your Bear Blog dashboard.
    new                 Create a new post from a markdown file.
    load                Load a post by ID and print its header + body.
    delete              Delete a post by ID.

options:
  -h, --help            show this help message and exit
```

### List posts

```bash
python bearcli.py list
```

Output:
```json
[
  {
    "id": "abc123",
    "title": "My Post Title",
    "href": "/your-subdomain/dashboard/posts/abc123/"
  },
  ...
]
```

### Create a new post

```bash
python bearcli.py new "Post Title" --file post.md
```

The markdown file should contain the full post content. Front matter is optional—if omitted, the title and current date will be added automatically.

Example `post.md`:
```markdown
---
title: My Post Title
date: 2026-02-22
---

This is the content of my blog post.
```

### Load a post

```bash
python bearcli.py load POST_ID
```

Returns the content for a post.

### Delete a post

```bash
python bearcli.py delete POST_ID
```

The post will be permanently deleted. Use with caution.

## Examples

Create a new post from a file:
```bash
python bearcli.py new "My NES Gaming Setup" --file nes-setup.md
```

List all posts:
```bash
python bearcli.py list
```

Delete a draft you no longer need:
```bash
python bearcli.py delete abc123xyz
```

---

## License

MIT License. See LICENSE file for details.

## Credits

Created for the BearBlog community. BearBlog is a privacy-focused blogging platform at [bearblog.dev](https://bearblog.dev).

**Note:** This CLI is designed to work with OpenClaw, allowing automated blog post creation and management from the OpenClaw assistant.
