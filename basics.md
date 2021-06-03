# Form Setup

## Getting Started

The POST2 can be used with any HTML form, to get started you need to [sign in](https://app.post2.io) into your account and create a handler.

Once the form handler was created, we have an unique ID and ready to implement.

## Basic Setup

All you have to do is replace the **action** attribute of your form with the unique POST2 handler URL.

<aside class="notice">
Don't forget to also set the **method** attribute to **POST**. POST2 only accepts POST requests, the default method on HTML forms is GET.
</aside>

```html
<form method="POST" action="https://api.post2.io/post2-early-access">
    <!-- your form code remains unchanged -->
</form>
```
