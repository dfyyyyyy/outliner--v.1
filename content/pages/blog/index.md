---
title: Blog
slug: /blog
numOfPostsPerPage: 12
enableSearch: true
topSections:
  - title:
      text: Featured Post
      color: text-dark
      type: TitleBlock
    subtitle: This is the subtitle
    posts:
      - content/pages/blog/top-ten-lessons-we-learned.md
    showThumbnail: true
    showExcerpt: true
    showDate: true
    showAuthor: true
    variant: big-list
    colors: bg-light-fg-dark
    styles:
      self:
        padding:
          - pt-28
          - pb-0
          - pl-4
          - pr-4
        justifyContent: flex-start
    type: FeaturedPostsSection
    hoverEffect: move-up
styles:
  title:
    textAlign: center
seo:
  metaTitle: Blog - Demo site
  metaDescription: >-
    This is the blog of the demo site where we post about technology, product,
    and design.
  socialImage: /images/img-placeholder.svg
  type: Seo
type: PostFeedLayout
bottomSections: []
postFeed:
  type: PagedPostsSection
  title: null
  subtitle: null
  showThumbnail: true
  showExcerpt: true
  showDate: true
  showAuthor: true
  actions: []
  elementId: null
  variant: three-col-grid
  colors: bg-light-fg-dark
  hoverEffect: move-up
---
<!DOCTYPE html>

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Markdown Editor Tool</title>
    <link href="https\://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css" rel="stylesheet">
    <link href="https\://fonts.googleapis.com/css2?family=Roboto:wght\@400;500;700\&display=swap" rel="stylesheet">
    <style>
        /\* Basic Reset \*/
        \* {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        /* Body Styling */
        body {
            font-family: 'Roboto', sans-serif;
            background-color: #ffffff;
            color: #333;
            padding: 20px;
            height: 100%;
            display: flex;
            justify-content: center;
            align-items: center;
            text-align: left;
        }

        /* Container Styling */
        .container {
            width: 100%;
            max-width: 1065px;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
            height: 100%;
            background: linear-gradient(to right, #E95EB1, #9A85F8);
            border-radius: 10px;
            padding: 20px;
        }

        /* Header Styling */
        header {
            text-align: center;
            margin-bottom: 20px;
        }
        header h1 {
            font-size: 36px;
            color: #fff;
        }
        header p {
            font-size: 16px;
            color: #ccc;
        }

        /* Editor Container */
        .editor-container {
            display: flex;
            flex-direction: row;
            gap: 30px;
            margin-bottom: 20px;
            height: 70%;
        }

        /* Editor and Preview Areas */
        .editor, .preview {
            flex: 1;
            border: 1px solid #DEDEDE;
            border-radius: 8px;
            height: 100%;
        }

        /* Textarea for Input */
        textarea {
            width: 100%;
            height: 100%;
            font-family: 'Courier New', monospace;
            font-size: 16px;
            padding: 20px;
            border: none;
            border-radius: 8px;
            background-color: #ffffff;
            resize: none;
            outline: none;
            transition: all 0.3s ease;
        }

        textarea:focus {
            border: 2px solid #ffffff;
            box-shadow: 0 0 5px rgba(255, 255, 255, 0.5);
        }

        /* Preview Area */
        .preview {
            background-color: #fff;
            padding: 20px;
            overflow-y: auto;
            height: 100%;
            border: 1px solid #ddd;
            border-radius: 8px;
            min-height: 250px;
            line-height: 1.5;
        }

        /* Buttons and Controls */
        .controls {
            display: flex;
            justify-content: center;
            margin-top: 20px;
        }

        button {
            padding: 10px 15px;
            background-color: #ffffff;
            color: #E95EB1;
            border: none;
            border-radius: 8px;
            font-weight: bold;
            cursor: pointer;
            transition: background-color 0.3s, transform 0.2s;
        }

        button:hover {
            background-color: #f1f1f1;
            transform: scale(1.05);
        }

        /* Styling for Markdown Headings, Lists, etc. */
        .preview h1, .preview h2, .preview h3, .preview h4, .preview h5, .preview h6 {
            margin: 20px 0;
            color: #333;
        }

        .preview p {
            margin: 10px 0;
        }

        .preview ul, .preview ol {
            margin: 10px 0;
            padding-left: 20px;
        }

        .preview blockquote {
            margin: 20px 0;
            padding: 10px;
            background-color: #f9f9f9;
            border-left: 4px solid #E95EB1;
        }

        .preview hr {
            margin: 20px 0;
            border: none;
            border-top: 2px solid #ddd;
        }

        /* Responsive Design */
        @media (max-width: 600px) {
            .editor-container {
                flex-direction: column;
            }

            textarea {
                height: 150px;
            }

            button {
                width: 100%;
            }
        }
    </style>

</head>
<body>
    <div class="container">
        <header>
            <h1>Markdown Editor</h1>
            <p>Type your Markdown on the left, see the preview on the right.</p>
        </header>
        <div class="editor-container">
            <!-- Markdown Input Area -->
            <div class="editor">
                <textarea id="markdown-input" placeholder="Write Markdown here..." autofocus></textarea>
            </div>
            <!-- Preview Area -->
            <div class="preview" id="markdown-output" contenteditable="true">
                Your live preview will appear here.
            </div>
        </div>
        <div class="controls">
            <button id="clear-btn">Clear</button>
        </div>
    </div>

    <script>
        // Adding functionality to handle markdown input and live preview
        document.getElementById('markdown-input').addEventListener('input', function () {
            const markdownText = this.value.replace(/\*(\w+(\s\w+){0,3})\*/g, '<strong>$1</strong>');
            const outputElement = document.getElementById('markdown-output');

            // Update the output only when there is content
            if (markdownText.trim() !== "") {
                outputElement.innerHTML = markdownToHTML(markdownText);
            } else {
                outputElement.innerHTML = 'Your live preview will appear here.';
            }
        });

        document.getElementById('clear-btn').addEventListener('click', function () {
            document.getElementById('markdown-input').value = '';
            document.getElementById('markdown-output').innerHTML = 'Your live preview will appear here.';
        });

        // Simple Markdown to HTML converter (updated to handle Horizontal Rules and Tables)
        function markdownToHTML(markdown) {
            let html = markdown;

            // Headings
            html = html.replace(/###### (.*?)$/gm, '<h6>$1</h6>');
            html = html.replace(/##### (.*?)$/gm, '<h5>$1</h5>');
            html = html.replace(/#### (.*?)$/gm, '<h4>$1</h4>');
            html = html.replace(/### (.*?)$/gm, '<h3>$1</h3>');
            html = html.replace(/## (.*?)$/gm, '<h2>$1</h2>');
            html = html.replace(/# (.*?)$/gm, '<h1>$1</h1>');

            // Bold Text
            html = html.replace(/\*\*(.*?)\*\*/gm, '<strong>$1</strong>');
            html = html.replace(/__(.*?)__/gm, '<strong>$1</strong>');

            // Strikethrough
            html = html.replace(/~~(.*?)~~/gm, '<del>$1</del>');

            // Blockquotes
            html = html.replace(/^> (.*?)$/gm, '<blockquote>$1</blockquote>');
            
            // Lists (Ordered and Unordered)
            const orderedListRegex = /^(\d+)\. (.*)$/gm;

            html = html.replace(orderedListRegex, (match, p1, p2) => {
                return `<ol><li>${p2}</li></ol>`;
            });

            const unorderedListRegex = /^[-*] (.*)$/gm;

            html = html.replace(unorderedListRegex, (match, p1) => {
                return `<ul><li>${p1}</li></ul>`;
            });

            // Checkboxes
            const checkboxRegex = /^- \[x\] (.*)$/gm;

            html = html.replace(checkboxRegex, (match, p1) => {
                return `<ul><li><input type="checkbox" checked disabled>${p1}</li></ul>`;
            });

            const uncheckedCheckboxRegex = /^- \[ \] (.*)$/gm;

            html = html.replace(uncheckedCheckboxRegex, (match, p1) => {
                return `<ul><li><input type="checkbox" disabled>${p1}</li></ul>`;
            });

            // Links & Images
            html = html.replace(/\[([^\]]+)\]\((https?:\/\/[^\)]+)\)/g,
                (match, p1, p2) => { return `<a href="${p2}" target="_blank">${p1}</a>`; });
            html = html.replace(/\!\[([^\]]+)\]\((https?:\/\/[^\)]+)\)/g,
                (match, p1, p2) => { return `<img src="${p2}" alt="${p1}" style="max-width:100%;">`; });

            // Code Blocks
            html = html.replace(/```([\s\S]*?)```/g,
                (match,p1) => { return `<pre><code>${p1}</code></pre>`; });
            
            // Inline Code
            html=html.replace(/`([^`]+)`/g,'<code>$1</code>');

            // Horizontal Rules (--- , ***, ___)
            html=html.replace(/(^|\n)---($|\n)/g,'<hr/>');
            html=html.replace(/(^|\n)___($|\n)/g,'<hr/>');
            html=html.replace(/(^|\n)\*\*\*($|\n)/g,'<hr/>');

            return(html);
        }
    </script>

</body>
</html>



