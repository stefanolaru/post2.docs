# Form Setup

## Getting Started

The POST2 can be used with any HTML form, to get started you need to [sign in](https://app.post2.io) into your account and create a handler.

Once the form handler was created, we have an unique ID and ready to implement.

## Basic Setup

All you have to do is replace the **action** attribute of your form with the unique POST2 handler URL, i.e. _https://api.post2.io/FORM_ID_

> **NOTE** Set the **method** attribute to **POST**. If not set the default method on HTML forms is GET.
> POST2 only accepts HTTP POST requests.

```html
<!-- This is a sample email capture form -->
<form method="POST" action="https://api.post2.io/post2-early-access">
    <!-- your form code remains unchanged -->
    <input type="email" name="email" placeholder="your@email.com" required />
</form>
```

> **NOTE** Only form elements with a **name** attribute will have their values passed when submitting a form.
