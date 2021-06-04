# Email Notifications

POST2 sends you the form submitted data via email. It can send to one or multiple recipients.

> You can opt-out from email notifications, but for the handler to remain active it needs to be linked to a [Webhook](webhooks.md) or [Integration](integrations.md)

## Notification Template

The email notification template is fully customizable using [{{handlebars}}](handlebarsjs.com). It contains no POST2 branding.

The {{unsubscribe_link}} needs to be present, but you can customize it as you want.

```html
<p>Hi John</p>

<p>
    {{first_name}} requested private beta access.<br />
    Email: {{email}}
</p>

<p>Cheers!</p>
```

## Autoresponse

You can set up a fully customizable autoresponse to the person who submitted the form. It works the same as for notification templates.

```html
<p>Hi {{first_name}}</p>

<p>
    Thanks a lot for your interest in our product, we'll set up your account and
    get back to you with all the info.
</p>

<p>Have an awesome day!</p>
```

> The form needs to contain an **email** field
