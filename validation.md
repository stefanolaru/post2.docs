# Schema & Validation

POST2 provides a no code way to define your form schema, fields, validation rules and errors for your form inputs.

![Validation rules](img/validation.png)

## Form Schema

Defining a form schema is optional, but to use some of the features integrations or autoresponders you have to define it.

The form schema helps POST2 understand your data structure, add data validation or enhance email notification customization.

Let's take this sample form:

```html
<!-- This is a sample email capture form -->
<form method="POST" action="https://api.post2.io/replace-with-your-id">
    <!-- name field -->
    <input type="text" name="name_field" required />
    <!-- email field -->
    <input type="email" name="email_field" required />
    <!-- the rest of the form -->
</form>
```

If no schema is defined there's no specification how to label the fields, POST2 will simply _humanize_ the name attribute and the notification will look like:

> Name Field: John Doe
> Email Field: john@example.com

## Form Validation

**Backend validation is a MUST**. Frontend validation (browser native or javascript) can easily be bypassed, you can use it to improve the UX by providing instant feedback to your visitors.

When defining the form schema multiple validation rules can be attached to each field. Customizing error text is also possible.

```json
// sample response on validation errors
{
    "error": "Data validation failed.",
    "errors": {
        "email": "Please enter a non disposable email address."
    }
}
```

Enabling **strict schema** will exclude any additional fields not defined in the form schema.

## Validation Rules

| Rule               | Parameters | Description                                                                               |
| ------------------ | ---------- | ----------------------------------------------------------------------------------------- |
| required           | _none_     | Requires non-empty data. Checks for empty arrays and strings containing only whitespaces. |
| alphanumeric       | _none_     | Accepts only alphanumerics. (0-9, A-Z, a-z)                                               |
| email              | _none_     | Accepts valid email address format.                                                       |
| email (MX)         | _none_     | Accepts valid email address format + check if has MX records                              |
| email (disposable) | _none_     | Accepts valid email address format + check if the email is not disposable                 |
| url                | _none_     | Accepts only URLs.                                                                        |
| minLength          | min        | Requires the input to have a minimum specified length, inclusive.                         |
| manLength          | max        | Requires the input to have a maximum specified length, inclusive.                         |
| lengthBetween      | min, max   | Requires the input to have the length between specified min/max, inclusive.               |
| minValue           | min        | Requires input to have a specified minimum numeric value.                                 |
| manValue           | max        | Requires input to have a specified maximum numeric value.                                 |
| valueBetween       | min, max   | Requires the input to have the value between specified min/max, inclusive.                |
