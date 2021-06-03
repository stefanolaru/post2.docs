# AntiSPAM & Restrictions

## SPAM Submissions

All the form handles are by default filtered for spam using Akismet, the industry leader in spam detection.

The spam submissions will be discarded by default due to our Privacy Policy.

You can opt-in to save the spam submissions into your account to review them. Enabling this can be useful for debugging potential issues with legitimate submissions being marked incorrectly as spam.

## Honeypot

The honeypot is a form field that's not visible to normal users filling the form. It's used to lure bot users filling it, but it should be left blank.

A form submission that has the honeypot field completed will be silently discarded.

To enable the honeypot fields go into "SPAM Protection" tab of your form settings and fill in the **name** attribute.

```html
<!-- This is a sample email capture form -->
<form method="POST" action="https://api.post2.io/replace-with-your-id">
    <!-- email field -->
    <input type="email" name="email" placeholder="your@email.com" required />
    <!-- honeypot field -->
    <div style="position: absolute; left: -9999px">
        <input type="text" name="url" tabindex="-1" autocomplete="nope" />
    </div>
    <!-- the rest of the form -->
</form>
```

**Honeypot tips**

-   Make it as legit as possible, trick the bots to fill it
-   Don't use _type="hidden"_ fields as most bots will recognize the trap
-   Use _text_ of _email_ types and wrap the input in a div tag that's positioned out of the screen
-   Use a common name attribute, i.e. name="url"
-   Set _tabindex="-1"_ so the visitors won't focus it by accident
-   Set _autocomplete="nope"_ so the browsers' autocomplete feature won't fill it by mistake

> **NOTE** if you use a honeypot field you must declare it in you form settings, otherwise it will be ignored

## Website restrictions

Website restrictions, or HTTP referrer restriction will restrict the form submissions to specified websites.

To enable this feature go into "SPAM Protection" tab of your form settings and fill in the accepted origins.

Form submissions that don't originate from the specified websites will be blocked.

> This feature is disabled by default, submissions from any origin are accepted

## Country restrictions

Country restriction will restrict the form submissions to the specified countries.

POST2 uses a reliable IP2Location service to get the visitor's location from their IP address.

To enable this feature go into "SPAM Protection" tab of your form settings and select the accepted countries.

Form submissions made by visitors outside the selected countries will be blocked.

> This feature is disabled by default, submissions from any contry are accepted
