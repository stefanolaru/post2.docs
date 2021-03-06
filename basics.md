# Form Setup

## Getting Started

The POST2 can be used with any HTML form, to get started you need to [sign in](https://app.post2.io) into your account and create a handler.

Once the form handler was created, we have an unique ID and ready to implement.

## Basic Setup

All you have to do is replace the **action** attribute of your existing form with the unique POST2 handler URL
Example: <span>_https://api.post2.io/replace-with-your-id_</span>

```html
<!-- This is a sample email capture form -->
<form method="POST" action="https://api.post2.io/replace-with-your-id">
    <!-- your form code remains unchanged -->
    <input type="email" name="email" placeholder="your@email.com" required />
</form>
```

> **NOTE** Set the **method** attribute to **POST**. If it's not set the default method on HTML forms is GET.
> POST2 only accepts HTTP POST requests.

> **NOTE2** Only form elements with a **name** attribute will have their values passed when submitting a form.

## Redirect ("Thank You" page)

Using the basic setup the browser will reload the page on form submit. It display a default POST2 page with a success or error message.

You can customize the success page content in the form handler settings page.

If you want to use your own thank you page you can add the URL in the settings and the browser will redirect to that on successful submit.

> **NOTE** the redirect option can only be used with basic setup.

> **NOTE 2** If using validation the browser will display the validation errors (if any) in the POST2 default layout.

## Advanced Setup

To enhance the UI/UX of your forms you can submit data using AJAX without reloading the page.

```html
<!-- This is a sample email capture form -->
<form
    method="POST"
    action="https://api.post2.io/replace-with-your-id"
    id="post2-form"
>
    <!-- email field -->
    <input type="email" name="email" placeholder="your@email.com" required />
    <!-- submit button -->
    <button type="submit">Subscribe</button>
</form>
```

Now the Javascript code.

```javascript
// get the form
const post2Form = document.getElemetById("post2-form");

// attach the event listener
post2Form.addEventListener("submit", (e) => {
    // prevent the form submission
    e.preventDefault();
    // get the email field
    const emailField = post2Form.querySelector('type="email"');

    // initiate the HTTP request, note we use the form handler as the endpoint
    fetch(post2Form.getAttribute("action"), {
        method: "POST",
        body: JSON.stringify({
            email: emailField.value,
        }),
        headers: {
            "Content-type": "application/json; charset=UTF-8",
        },
    })
        .then((response) => response.json())
        .then((res) => {
            if (res.error) {
                // there was an error
                alert(res.error);
            } else {
                // successful submit
                alert("Yay! it worked");
            }
        })
        .catch((err) => {
            // something went wrong with the request, see console
            console.error(err);
        });
});
```

## Health Dashboard

We provide a simple dashboard to monitor your forms activity for the past 30 days.

The SPAM submissions are not counted into the total.

**POST2 doesn't store any submitted data, we log just the timestamp and if it's spam or not**

The stats don't include the submissions blocked by the honeypot fields or other restrictions.

![Dashboard](img/dashboard.png)
