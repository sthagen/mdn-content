---
title: "ARIA: aria-readonly attribute"
short-title: aria-readonly
slug: Web/Accessibility/ARIA/Reference/Attributes/aria-readonly
page-type: aria-attribute
spec-urls: https://w3c.github.io/aria/#aria-readonly
sidebar: accessibilitysidebar
---

The `aria-readonly` attribute indicates that the element is not editable, but is otherwise operable.

## Description

When you want to indicate that an interactive element works but is not editable, set `aria-readonly="true"`. This indicates to the user that an interactive element that would normally be focusable and copyable has been placed in a read-only (not disabled) state.

When `aria-readonly` is set to `true`, it means the user can read but not set the value of the widget. Read-only elements are still relevant to the user, so you should not prevent the user from navigating to the element or its focusable descendants or copying the value.

Examples include:

- Form elements which should not be changed.
- Row and column headers in a spreadsheet.
- The total value in a shopping cart.

If the non-changeable value shouldn't be able to receive focus, use [`aria-disabled`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-disabled) instead.

> [!NOTE]
> When using semantic HTML form controls, if you set the `readonly` attribute, you don't need to include `aria-readonly="true"`.

> [!NOTE]
> The value of `<input type="checkbox">` can not be edited making `readonly` not relevant. However, when creating checkboxes with `role="checkbox"` the `aria-readonly` attribute _is_ supported.

## Values

- `true`
  - : The element is readonly.
- `false` (default)
  - : The element is not readonly.

## Associated interfaces

- {{domxref("Element.ariaReadOnly")}}
  - : The [`ariaReadOnly`](/en-US/docs/Web/API/Element/ariaReadOnly) property, part of the {{domxref("Element")}} interface, reflects the value of the `aria-readonly` attribute.
- {{domxref("ElementInternals.ariaReadOnly")}}
  - : The [`ariaReadOnly`](/en-US/docs/Web/API/ElementInternals/ariaReadOnly) property, part of the {{domxref("ElementInternals")}} interface, reflects the value of the `aria-readonly` attribute.

## Associated roles

Used in roles:

- [`checkbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/checkbox_role)
- [`combobox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/combobox_role)
- [`grid`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/grid_role)
- [`gridcell`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/gridcell_role)
- [`listbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/listbox_role)
- [`radiogroup`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/radiogroup_role)
- [`slider`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/slider_role)
- [`spinbutton`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/spinbutton_role)
- [`textbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/textbox_role)

Inherited into roles:

- [`columnheader`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/columnheader_role)
- [`rowheader`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/rowheader_role)
- [`searchbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/searchbox_role)
- [`switch`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/switch_role)
- [`treegrid`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/treegrid_role)

## Specifications

{{Specifications}}

## See also

- [HTML `readonly` attribute](/en-US/docs/Web/HTML/Reference/Attributes/readonly)
- [`aria-disabled`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-disabled)
