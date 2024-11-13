---
title: Home
slug: /
sections:
  - type: GenericSection
    title:
      text: Unblock your team boost your time to production
      color: text-dark
      type: TitleBlock
    subtitle: Subtitle goes here
    text: |+
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

    actions:
      - label: Get started
        altText: ''
        url: /
        showIcon: false
        icon: arrowRight
        iconPosition: right
        style: secondary
        elementId: ''
        type: Button
      - label: See Tutorials
        altText: ''
        url: /
        showIcon: true
        icon: arrowRight
        iconPosition: right
        style: primary
        elementId: ''
        type: Link
    media:
      altText: Unblock your team boost your time to production preview
      elementId: ''
      type: ImageBlock
    badge:
      label: This is a badge
      color: text-primary
      type: Badge
    elementId: ''
    colors: bg-light-fg-dark
    styles:
      self:
        alignItems: center
        flexDirection: row
        padding:
          - pt-16
          - pl-16
          - pb-16
          - pr-16
  - type: FeaturedItemsSection
    title:
      text: Key Benefits
      color: text-dark
      styles:
        self:
          textAlign: center
      type: TitleBlock
    subtitle: Subtitle goes here
    items:
      - type: FeaturedItem
        title: 500k
        subtitle: Numbers Done
        text: >-
          Sed ut perspiciatis unde omnis iste natus error sit voluptatem
          accusantium doloremque laudantium, totam rem aperiam, eaque ipsa quae.
          explicabo.
        actions: []
        elementId: null
        colors: bg-neutralAlt-fg-dark
        styles:
          self:
            padding:
              - pt-8
              - pl-8
              - pb-8
              - pr-8
            borderRadius: x-large
            flexDirection: row
            justifyContent: center
            textAlign: left
        image:
          type: ImageBlock
          altText: Lightning bolt symbol on red background
          elementId: ''
          url: /images/icon1.svg
          styles:
            self:
              borderRadius: x-large
      - title: 20x
        subtitle: The Job Stuff
        text: |+


        image:
          url: /images/icon2.svg
          altText: Featured icon two
          elementId: ''
          type: ImageBlock
        actions: []
        colors: bg-neutralAlt-fg-dark
        styles:
          self:
            padding:
              - pt-8
              - pl-8
              - pb-8
              - pr-8
            borderRadius: x-large
            flexDirection: row
            textAlign: left
            justifyContent: center
        type: FeaturedItem
      - title: 200%
        subtitle: Faster
        text: >-
          Sed ut perspiciatis unde omnis iste natus error sit voluptatem
          accusantium doloremque laudantium, totam rem aperiam, eaque ipsa quae.
          explicabo.
        image:
          url: /images/icon3.svg
          altText: Featured icon three
          elementId: ''
          type: ImageBlock
        actions: []
        colors: bg-neutralAlt-fg-dark
        styles:
          self:
            padding:
              - pt-8
              - pl-8
              - pb-8
              - pr-8
            borderRadius: x-large
            flexDirection: row
        type: FeaturedItem
    actions:
      - label: Get started
        altText: ''
        url: /
        showIcon: false
        icon: arrowRight
        iconPosition: right
        style: primary
        elementId: ''
        type: Button
    badge:
      label: This is a badge
      color: text-primary
      styles:
        self:
          textAlign: center
      type: Badge
    elementId: ''
    variant: three-col-grid
    colors: bg-neutral-fg-dark
    styles:
      self:
        padding:
          - pb-16
          - pt-16
          - pl-16
          - pr-16
        justifyContent: center
      subtitle:
        textAlign: center
  - subtitle: Award winning enterprises trust us
    images:
      - url: /images/empathy-logo.svg
        altText: Empathy logo
        type: ImageBlock
      - url: /images/wellster-logo.svg
        altText: Wellster logo
        type: ImageBlock
      - url: /images/vise-logo.svg
        altText: Vise logo
        type: ImageBlock
      - url: /images/telus-logo.svg
        altText: Telus logo
        type: ImageBlock
      - url: /images/contenful-logo.svg
        altText: Contentful logo
        type: ImageBlock
      - url: /images/sanity-logo.svg
        altText: Sanity logo
        type: ImageBlock
      - url: /images/rangle-logo.svg
        altText: Rangle logo
        type: ImageBlock
    motion: move-to-left
    colors: bg-light-fg-dark
    styles:
      self:
        justifyContent: center
      subtitle:
        textAlign: center
    type: ImageGallerySection
  - posts:
      - content/pages/blog/case-study-1.md
      - content/pages/blog/case-study-2.md
      - content/pages/blog/case-study-3.md
    showThumbnail: true
    showDate: true
    showAuthor: true
    variant: three-col-grid
    colors: bg-light-fg-dark
    styles:
      self:
        padding:
          - pt-16
          - pl-16
          - pb-16
          - pr-16
        justifyContent: center
    type: FeaturedPostsSection
    hoverEffect: move-up
  - title: Divider
    colors: bg-light-fg-dark
    styles:
      self:
        padding:
          - pt-7
          - pl-7
          - pb-7
          - pr-7
    type: DividerSection
  - title:
      text: Grow your business 10x faster
      color: text-dark
      styles:
        self:
          textAlign: center
      type: TitleBlock
    subtitle: This is a subtitle
    text: |-
      Aenean eros ipsum, interdum quis dignissim non, sollicitudin vitae nisl.
      Aenean vel aliquet elit, at blandit ipsum. Sed eleifend felis sit amet
      erat molestie, hendrerit malesuada justo ultrices. Nunc volutpat at erat
      vitae interdum. Ut nec massa eget lorem blandit condimentum et at risus.
    media:
      title: Title of the video
      url: /images/placeholder-video.mp4
      controls: false
      aspectRatio: '16:9'
      styles:
        self:
          padding:
            - pt-2
            - pb-2
            - pl-2
            - pr-2
          borderColor: border-dark
          borderStyle: solid
          borderWidth: 1
          borderRadius: large
      type: VideoBlock
      autoplay: true
      loop: true
      muted: true
    badge:
      label: Key Benefits
      color: text-primary
      styles:
        self:
          textAlign: center
      type: Badge
    colors: bg-light-fg-dark
    styles:
      self:
        flexDirection: col
        justifyContent: center
      subtitle:
        textAlign: center
    type: GenericSection
  - type: GenericSection
    title:
      text: Generic section with a video
      color: text-dark
      styles:
        self:
          textAlign: left
      type: TitleBlock
    subtitle: Section with a video subtitle
    text: |-
      Aenean eros ipsum, interdum quis dignissim non, sollicitudin vitae nisl.
      Aenean vel aliquet elit, at blandit ipsum. Sed eleifend felis sit amet
      erat molestie, hendrerit malesuada justo ultrices. Nunc volutpat at erat
      vitae interdum. Ut nec massa eget lorem blandit condimentum et at risus.
    actions: []
    media:
      title: Title of the video
      url: /images/placeholder-video.mp4
      autoplay: true
      loop: true
      muted: true
      controls: false
      aspectRatio: '16:9'
      styles:
        self:
          padding:
            - pt-2
            - pb-2
            - pl-2
            - pr-2
          borderColor: border-dark
          borderStyle: solid
          borderWidth: 1
          borderRadius: large
      type: VideoBlock
    elementId: null
    colors: bg-light-fg-dark
    styles:
      self:
        flexDirection: row
        justifyContent: center
      subtitle:
        textAlign: left
  - title:
      text: Social Media Management
      color: text-dark
      type: TitleBlock
    subtitle: Increase your reach
    text: >
      A service that helps businesses to manage their social media accounts and
      posts.
    actions:
      - label: Get started
        url: /
        icon: arrowRight
        iconPosition: right
        style: secondary
        type: Button
      - label: See Tutorials
        url: /
        showIcon: true
        icon: arrowRight
        iconPosition: right
        style: primary
        type: Link
    media:
      url: /images/hero2.svg
      altText: Fun feature preview
      type: ImageBlock
    badge:
      label: This is a badge
      color: text-primary
      type: Badge
    colors: bg-light-fg-dark
    styles:
      self:
        alignItems: center
    type: GenericSection
  - title:
      text: Business Consulting
      color: text-dark
      type: TitleBlock
    subtitle: Be in good company
    text: >
      A service that provides advice and guidance to startups and small
      businesses.
    actions:
      - label: Get started
        url: /
        icon: arrowRight
        iconPosition: right
        style: secondary
        type: Button
      - label: See Tutorials
        url: /
        showIcon: true
        icon: arrowRight
        iconPosition: right
        style: primary
        type: Link
    media:
      url: /images/hero3.svg
      altText: Dope design preview
      type: ImageBlock
    badge:
      label: This is a badge
      color: text-primary
      type: Badge
    colors: bg-light-fg-dark
    styles:
      self:
        alignItems: center
        flexDirection: row-reverse
    type: GenericSection
  - title: Divider
    colors: bg-light-fg-dark
    styles:
      self:
        padding:
          - pt-7
          - pl-7
          - pb-7
          - pr-7
    type: DividerSection
  - type: CarouselSection
    title: null
    subtitle: What our customers say about us
    items:
      - title: >-
          “A designer knows he has achieved perfection not when there is nothing
          left to add, but when there is nothing left to take away.”
        tagline: Testimonial 1
        subtitle: 'Maria Walters, Company'
        text: >-
          Sed ut perspiciatis unde omnis iste natus error sit voluptatem
          accusantium doloremque laudantium, totam rem aperiam, eaque ipsa quae.
          explicabo.
        image:
          url: /images/person-placeholder-light.png
          altText: Maria Walters
          styles:
            self:
              borderRadius: full
          type: ImageBlock
        actions: []
        colors: bg-neutralAlt-fg-dark
        styles:
          self:
            padding:
              - pt-9
              - pb-9
              - pl-9
              - pr-9
            textAlign: left
            borderRadius: large
            flexDirection: row
            justifyContent: center
        type: FeaturedItem
      - title: >-
          "Design is a plan for arranging elements in such a way as best to
          accomplish a particular purpose."
        tagline: Testimonial 2
        subtitle: 'John Doe, Company'
        text: >-
          Sed ut perspiciatis unde omnis iste natus error sit voluptatem
          accusantium doloremque laudantium, totam rem aperiam, eaque ipsa quae.
          explicabo.
        image:
          url: /images/person-placeholder-light.png
          altText: John Doe
          styles:
            self:
              borderRadius: full
          type: ImageBlock
        actions: []
        colors: bg-neutralAlt-fg-dark
        styles:
          self:
            padding:
              - pt-9
              - pb-9
              - pl-9
              - pr-9
            textAlign: left
            borderRadius: large
            flexDirection: row
            justifyContent: center
        type: FeaturedItem
      - title: >-
          "Design is how it works, how it functions. Good design doesn't just
          make a product aesthetically pleasing, it makes it a pleasure to use."
        tagline: Testimonial 3
        subtitle: 'Maria Walters, Company'
        text: >-
          Sed ut perspiciatis unde omnis iste natus error sit voluptatem
          accusantium doloremque laudantium, totam rem aperiam, eaque ipsa quae.
          explicabo.
        image:
          url: /images/person-placeholder-light.png
          altText: Maria Walters
          styles:
            self:
              borderRadius: full
          type: ImageBlock
        actions: []
        colors: bg-neutralAlt-fg-dark
        styles:
          self:
            padding:
              - pt-9
              - pb-9
              - pl-9
              - pr-9
            textAlign: left
            borderRadius: large
            flexDirection: row
            justifyContent: center
        type: FeaturedItem
      - title: >-
          “A designer knows he has achieved perfection not when there is nothing
          left to add, but when there is nothing left to take away.”
        tagline: Testimonial 4
        subtitle: 'Maria Walters, Company'
        text: >-
          Sed ut perspiciatis unde omnis iste natus error sit voluptatem
          accusantium doloremque laudantium, totam rem aperiam, eaque ipsa quae.
          explicabo.
        image:
          url: /images/person-placeholder-light.png
          altText: Maria Walters
          styles:
            self:
              borderRadius: full
          type: ImageBlock
        actions: []
        colors: bg-neutralAlt-fg-dark
        styles:
          self:
            padding:
              - pt-9
              - pb-9
              - pl-9
              - pr-9
            textAlign: left
            borderRadius: large
            flexDirection: row
            justifyContent: center
        type: FeaturedItem
      - title: >-
          "Design can be art. Design can be aesthetics. Design is so simple,
          that's why it is so complicated."
        tagline: Testimonial 5
        subtitle: 'Jane Walters, Company'
        text: >-
          Sed ut perspiciatis unde omnis iste natus error sit voluptatem
          accusantium doloremque laudantium, totam rem aperiam, eaque ipsa quae.
          explicabo.
        image:
          url: /images/person-placeholder-light.png
          altText: Maria Walters
          styles:
            self:
              borderRadius: full
          type: ImageBlock
        actions: []
        colors: bg-neutralAlt-fg-dark
        styles:
          self:
            padding:
              - pt-9
              - pb-9
              - pl-9
              - pr-9
            textAlign: left
            borderRadius: large
            flexDirection: row
            justifyContent: center
        type: FeaturedItem
      - title: >-
          “Quote from some important person goes right here. I love using
          Netlify Create.”
        tagline: Testimonial 6
        subtitle: 'Jane Doe, Company'
        text: >-
          Sed ut perspiciatis unde omnis iste natus error sit voluptatem
          accusantium doloremque laudantium, totam rem aperiam, eaque ipsa quae.
          explicabo.
        image:
          url: /images/img-placeholder-dark.png
          altText: Jane Doe
          styles:
            self:
              borderRadius: full
          type: ImageBlock
        actions: []
        colors: bg-dark-fg-light
        styles:
          self:
            padding:
              - pt-9
              - pb-9
              - pl-9
              - pr-9
            textAlign: left
            borderRadius: large
            flexDirection: row
            justifyContent: center
        type: FeaturedItem
    elementId: null
    variant: next-prev-nav
    colors: bg-light-fg-dark
    styles:
      self:
        justifyContent: center
      subtitle:
        textAlign: center
  - title:
      text: List of features here
      color: text-primary
      styles:
        self:
          textAlign: center
      type: TitleBlock
    subtitle: Featured items section subtitle
    items:
      - title: Feature Item One
        tagline: This is the tagline
        subtitle: This is the item subtitle
        text: |
          Follow the tutorial to build your first Netlify Create site.
        image:
          url: /images/abstract-feature1.svg
          altText: Placeholder Image
          styles:
            self:
              borderRadius: x-large
          type: ImageBlock
        colors: bg-light-fg-dark
        styles:
          self:
            padding:
              - pt-8
              - pl-8
              - pb-8
              - pr-8
            borderRadius: x-large
            flexDirection: col
        type: FeaturedItem
      - title: Feature Item Two
        tagline: This is the tagline
        subtitle: This is the item subtitle
        text: |
          Follow the tutorial to build your first awesome Netlify Create site.
        image:
          url: /images/abstract-feature2.svg
          altText: Placeholder image
          styles:
            self:
              borderRadius: x-large
          type: ImageBlock
        colors: bg-light-fg-dark
        styles:
          self:
            padding:
              - pt-8
              - pl-8
              - pb-8
              - pr-8
            borderRadius: x-large
            flexDirection: col
        type: FeaturedItem
      - title: Feature Item Three
        tagline: This is the tagline
        subtitle: This is the item subtitle
        text: >
          Learn from the tutorial and build your first awesome Netlify Create
          site.
        image:
          url: /images/abstract-feature1.svg
          altText: Placeholder image
          styles:
            self:
              borderRadius: x-large
          type: ImageBlock
        colors: bg-light-fg-dark
        styles:
          self:
            padding:
              - pt-8
              - pl-8
              - pb-8
              - pr-8
            borderRadius: x-large
            flexDirection: col
        type: FeaturedItem
    variant: three-col-grid
    colors: bg-neutral-fg-dark
    styles:
      self:
        padding:
          - pt-16
          - pl-8
          - pb-16
          - pr-8
        justifyContent: center
      subtitle:
        textAlign: center
    type: FeaturedItemsSection
  - title:
      text: Generic Section With A Form
      color: text-dark
      type: TitleBlock
    subtitle: Section with a form subtitle
    text: |-
      Aenean eros ipsum, interdum quis dignissim non, sollicitudin vitae nisl.
      Aenean vel aliquet elit, at blandit ipsum. Sed eleifend felis sit amet
      erat molestie, hendrerit malesuada justo ultrices. Nunc volutpat at erat
      vitae interdum. Ut nec massa eget lorem blandit condimentum et at risus.
    media:
      fields:
        - name: name
          label: Name
          hideLabel: true
          placeholder: Your name
          isRequired: true
          width: full
          type: TextFormControl
        - name: email
          label: Email
          hideLabel: true
          placeholder: Your email
          isRequired: true
          width: full
          type: EmailFormControl
        - name: message
          label: Message
          hideLabel: true
          placeholder: Your message
          width: full
          type: TextareaFormControl
      elementId: contact-form
      styles:
        self:
          padding:
            - pt-6
            - pb-6
            - pl-6
            - pr-6
          borderColor: border-dark
          borderStyle: solid
          borderWidth: 1
          borderRadius: large
      type: FormBlock
      submitButton:
        type: SubmitButtonFormControl
        label: Submit
        showIcon: false
        icon: arrowRight
        iconPosition: right
        style: primary
        elementId: null
    badge:
      label: Contact Us
      color: text-primary
      type: Badge
    colors: bg-light-fg-dark
    type: GenericSection
type: PageLayout
---
