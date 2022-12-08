---
id: forms-element-library-textarea
title: Text area
description: A form element to read and edit multiline textual data
---

A text area allowing the user to read and edit multiline textual data.

![Form Textarea Symbol](/img/form-icons/form-textArea.svg)

### Configurable properties

- **Field label**: Label displayed on top of the text area.
- **Field description**: Description provided below the text area.
- **Key**: Binds the field to a form variable, see [data binding docs](../configuration/forms-config-data-binding.md).
- **Default value**: Provides a default value for the text area in case no input data exists for the given key.
- **Disabled**: Disables the text area, for use during development.
- **Hide if**: [Expression](../../feel/language-guide/feel-expressions-introduction.md) to hide the text area.
- **Validation**: Given that one of the following properties is set, the form will only submit when the respective condition is fulfilled. Otherwise, a validation error will be displayed.
  - **Required**: Text area must contain a value.
  - **Minimum length**: Text area must have at least `n` characters.
  - **Maximum length**: Text area must not have more than `n` characters.
  - **Regular expression pattern**: Text area value must match the provided [RegEx](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions/Cheatsheet) pattern.

### Datatypes

Text area can be bound to `boolean`, `string`, and `number` data, but will cohere the data into a string, which will lead the data to be written back to the process as a `string` when the form is submitted.
