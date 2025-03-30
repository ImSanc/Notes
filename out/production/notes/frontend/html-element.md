# Inline vs Block Elements in HTML

### 1️⃣ Block Elements
- Always start on a new line and take up the full width available.
- Their width automatically expands to fill the entire parent container unless explicitly defined.
- They respect all margin and padding properties.


     Element            ||    Description
    <div>	            ||      Generic block container
    <p>	                ||       Paragraph block
    <h1> to <h6>        ||        Headings (titles)
    <ul> / <ol>         ||	Lists (unordered & ordered)
    <li>	            ||    List items (inside <ul> or <ol>)
    <section>           ||	Defines a section
    <article>           ||	Represents a self-contained article
    <header> /<footer>  ||	Header & footer of a document

### 2️⃣ Inline Elements

- Do not start on a new line, instead, they flow within the same line.
- They only take up as much width as necessary (do not expand the full width).
- Margins & padding only work horizontally, not vertically.


    Element             ||	Description
    <span>	            ||  Generic inline container
    <a>	                ||  Links   
    <b> / <strong>	    ||  Bold text
    <i> / <em>	        ||  Italicized text
    <u>	                ||  Underlined text
    <label>             ||	Labels for form inputs
    <img>	            ||  Image element
    <input>	            ||  Input field (although it behaves slightly like a block in some cases)

### 3️⃣ Inline-Block Elements

- Similar to inline elements but allow width and height adjustments.
- They respect margin & padding on all sides, unlike inline elements.
- Useful when you want elements to stay in the same line but still be sizable.


        Element	    ||  Description
        <button>    ||	Buttons
        <input>     ||	Input fields
        <select>    ||	Dropdown select menus
        <img>       ||	Images (technically inline-block)

### 4️⃣ How This Affects Your <label> or non Block elements

- Add block property

    <label className="block mb-44 text-sm font-medium text-gray-900">{label}</label>