---
title: "<meter>: The HTML Meter element"
slug: Web/HTML/Reference/Elements/meter
page-type: html-element
browser-compat: html.elements.meter
sidebar: htmlsidebar
---

The **`<meter>`** [HTML](/en-US/docs/Web/HTML) element represents either a scalar value within a known range or a fractional value.

{{InteractiveExample("HTML Demo: &lt;meter&gt;", "tabbed-shorter")}}

```html interactive-example
<label for="fuel">Fuel level:</label>

<meter id="fuel" min="0" max="100" low="33" high="66" optimum="80" value="50">
  at 50/100
</meter>
```

```css interactive-example
label {
  padding-right: 10px;
  font-size: 1rem;
}
```

## Attributes

This element includes the [global attributes](/en-US/docs/Web/HTML/Reference/Global_attributes).

- `value`
  - : The current numeric value. This must be between the minimum and maximum values (`min` attribute and `max` attribute) if they are specified. If unspecified or malformed, the value is `0`. If specified, but not within the range given by the `min` attribute and `max` attribute, the value is equal to the nearest end of the range.

    > [!NOTE]
    > Unless the `value` attribute is between `0` and `1` (inclusive), the `min` and `max` attributes should define the range so that the `value` attribute's value is within it.

- [`min`](/en-US/docs/Web/HTML/Reference/Attributes/min)
  - : The lower numeric bound of the measured range. This must be less than the maximum value (`max` attribute), if specified. If unspecified, the minimum value is `0`.
- [`max`](/en-US/docs/Web/HTML/Reference/Attributes/max)
  - : The upper numeric bound of the measured range. This must be greater than the minimum value (`min` attribute), if specified. If unspecified, the maximum value is `1`.
- `low`
  - : The upper numeric bound of the low end of the measured range. This must be greater than the minimum value (`min` attribute), and it also must be less than the high value and maximum value (`high` attribute and `max` attribute, respectively), if any are specified. If unspecified, or if less than the minimum value, the `low` value is equal to the minimum value.
- `high`
  - : The lower numeric bound of the high end of the measured range. This must be less than the maximum value (`max` attribute), and it also must be greater than the low value and minimum value (`low` attribute and `min` attribute, respectively), if any are specified. If unspecified, or if greater than the maximum value, the `high` value is equal to the maximum value.
- `optimum`
  - : This attribute indicates the optimal numeric value. It must be within the range (as defined by the `min` attribute and `max` attribute). When used with the `low` attribute and `high` attribute, it gives an indication where along the range is considered preferable. For example, if it is between the `min` attribute and the `low` attribute, then the lower range is considered preferred. The browser may color the meter's bar differently depending on whether the value is less than or equal to the optimum value.

## Examples

### Basic Example

#### HTML

```html
<p>Battery level: <meter min="0" max="100" value="75">75%</meter></p>
```

#### Result

{{EmbedLiveSample("Basic_example", 300, 60)}}

### High and low range example

Note that in this example the [`min`](#min) attribute is omitted. This is allowed, as it will default to `0`.

#### HTML

```html
<p>
  Student's exam score:
  <meter min="0" low="50" high="80" max="100" value="84">84%</meter>
</p>
```

#### Result

{{EmbedLiveSample("High_and_Low_range_example", 300, 60)}}

## Technical Summary

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories"
          >Content categories</a
        >
      </th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content"
          >Flow content</a
        >,
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content"
          >phrasing content</a
        >, labelable content, palpable content.
      </td>
    </tr>
    <tr>
      <th scope="row">Permitted content</th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content"
          >Phrasing content</a
        >, but there must be no <code>&#x3C;meter></code> element among its
        descendants.
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
          ><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/structural_roles#structural_roles_with_html_equivalents">meter</a
          ></code
        >
      </td>
    </tr>
    <tr>
      <th scope="row">Permitted ARIA roles</th>
      <td>No <code>role</code> permitted</td>
    </tr>
    <tr>
      <th scope="row">DOM interface</th>
      <td>{{domxref("HTMLMeterElement")}}</td>
    </tr>
  </tbody>
</table>

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [Creating vertical form controls](/en-US/docs/Web/CSS/CSS_writing_modes/Vertical_controls)
- {{HTMLElement("progress")}}
- {{cssxref("::-webkit-meter-bar")}}, {{cssxref("::-webkit-meter-inner-element") }}, {{cssxref("::-webkit-meter-even-less-good-value")}}, {{cssxref("::-webkit-meter-optimum-value")}}, {{cssxref("::-webkit-meter-suboptimum-value")}}: non-standard pseudo-elements
