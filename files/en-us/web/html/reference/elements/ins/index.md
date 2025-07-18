---
title: "<ins>: The Inserted Text element"
slug: Web/HTML/Reference/Elements/ins
page-type: html-element
browser-compat: html.elements.ins
sidebar: htmlsidebar
---

The **`<ins>`** [HTML](/en-US/docs/Web/HTML) element represents a range of text that has been added to a document. You can use the {{HTMLElement("del")}} element to similarly represent a range of text that has been deleted from the document.

{{InteractiveExample("HTML Demo: &lt;ins&gt;", "tabbed-standard")}}

```html interactive-example
<p>&ldquo;You're late!&rdquo;</p>
<del>
  <p>&ldquo;I apologize for the delay.&rdquo;</p>
</del>
<ins cite="../how-to-be-a-wizard.html" datetime="2018-05">
  <p>&ldquo;A wizard is never late &hellip;&rdquo;</p>
</ins>
```

```css interactive-example
del,
ins {
  display: block;
  text-decoration: none;
  position: relative;
}

del {
  background-color: #fbb;
}

ins {
  background-color: #d4fcbc;
}

del::before,
ins::before {
  position: absolute;
  left: 0.5rem;
  font-family: monospace;
}

del::before {
  content: "−";
}

ins::before {
  content: "+";
}

p {
  margin: 0 1.8rem 0;
  font-family: Georgia, serif;
  font-size: 1rem;
}
```

## Attributes

This element includes the [global attributes](/en-US/docs/Web/HTML/Reference/Global_attributes).

- `cite`
  - : This attribute defines the URI of a resource that explains the change, such as a link to meeting minutes or a ticket in a troubleshooting system.
- `datetime`
  - : This attribute indicates the time and date of the change and must be a valid date with an optional time string. If the value cannot be parsed as a date with an optional time string, the element does not have an associated timestamp. For the format of the string without a time, see [Format of a valid date string](/en-US/docs/Web/HTML/Guides/Date_and_time_formats#date_strings). The format of the string if it includes both date and time is covered in [Format of a valid local date and time string](/en-US/docs/Web/HTML/Guides/Date_and_time_formats#local_date_and_time_strings).

## Accessibility

The presence of the `<ins>` element is not announced by most screen reading technology in its default configuration. It can be made to be announced by using the CSS {{cssxref("content")}} property, along with the {{cssxref("::before")}} and {{cssxref("::after")}} pseudo-elements.

```css
ins::before,
ins::after {
  clip-path: inset(100%);
  clip: rect(1px, 1px, 1px, 1px);
  height: 1px;
  overflow: hidden;
  position: absolute;
  white-space: nowrap;
  width: 1px;
}

ins::before {
  content: " [insertion start] ";
}

ins::after {
  content: " [insertion end] ";
}
```

Some people who use screen readers deliberately disable announcing content that creates extra verbosity. Because of this, it is important to not abuse this technique and only apply it in situations where not knowing content has been inserted would adversely affect understanding.

- [Short note on making your mark (more accessible) | The Paciello Group](https://www.tpgi.com/short-note-on-making-your-mark-more-accessible/)
- [Tweaking Text Level Styles | Adrian Roselli](https://adrianroselli.com/2017/12/tweaking-text-level-styles.html)

## Examples

```html
<ins>This text has been inserted</ins>
```

### Result

{{EmbedLiveSample("Examples")}}

## Technical summary

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories"
          >Content categories</a
        >
      </th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content"
          >Phrasing content</a
        >,
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content"
          >flow content</a
        >.
      </td>
    </tr>
    <tr>
      <th scope="row">Permitted content</th>
      <td>
        <a
          href="/en-US/docs/Web/HTML/Guides/Content_categories#transparent_content_model"
          >Transparent</a
        >.
      </td>
    </tr>
    <tr>
      <th scope="row">Tag omission</th>
      <td>None, both the starting and ending tag are mandatory.</td>
    </tr>
    <tr>
      <th scope="row">Permitted parents</th>
      <td>
        Any element that accepts
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content"
          >phrasing content</a
        >.
      </td>
    </tr>
    <tr>
      <th scope="row">Implicit ARIA role</th>
      <td>
        <code
          ><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/structural_roles#structural_roles_with_html_equivalents">insertion</a
          ></code
        >
      </td>
    </tr>
    <tr>
      <th scope="row">Permitted ARIA roles</th>
      <td>Any</td>
    </tr>
    <tr>
      <th scope="row">DOM interface</th>
      <td>{{domxref("HTMLModElement")}}</td>
    </tr>
  </tbody>
</table>

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{HTMLElement("del")}} element for marking deletion into a document
