---
id: forms-element-library-datetime
title: Datetime
description: A form element to read and edit date and time data
---

A component allowing the user to read and edit date and time data.

![Form Datetime Symbol](/img/form-icons/form-datetime.svg)

### Configurable properties

- **Date label**: Label displayed besides the date input field.
- **Time label**: Label displayed besides the time input field.
- **Field description**: Description provided below the checkbox.
- **Key**: Binds the field to a form variable, see [data binding docs](../configuration/forms-config-data-binding.md).
- **Subtype**: Selects the type of the datetime component. This can either be _Date_, _Time_ or _Date & Time_.
- **Use 24h**: Enables 24 hours time format.
- **Disabled**: Disables the checkbox, for use during development.
- **Hide if**: [Expression](../../feel/language-guide/feel-expressions-introduction.md) to hide the datetime component.
- **Time format**: Defines the time data format. This can either be _UTC offset_, _UTC normalized_ or _No timezone_.
- **Time interval**: Defines the steps of time that can be selected in the time input field.
- **Disallow past dates**: Enables the restriction to not allow past dates.
- **Validation**: Given that one of the following properties is set, the form will only submit when the respective condition is fulfilled. Otherwise, a validation error will be displayed.
  - **Required**: Datetime component must contain a value.

### Datatypes

Datetime components can be bound to data of the `string` type.
