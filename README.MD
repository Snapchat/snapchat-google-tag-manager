# Snap Pixel Community Template

The Snap Pixel community template is a Google Tag Manager [community gallery template repository](https://support.google.com/tagmanager/answer/9454109) that can be used to easily implement Snap Pixel using Google Tag Manager.

## Conversions API Gateway Support

This template supports the Conversions API Gateway, which allows you to serve the Snap Pixel script from your own first-party domain for improved tracking reliability.

**To use a custom gateway URL:**

1. In the template configuration, enter your full gateway script URL in the "Gateway Script URL" field (e.g., `https://yourdomain.com/scevent.min.js`)
2. **IMPORTANT:** You must also update the template's Script Injection permissions:
   - Edit the template in GTM
   - Navigate to the Permissions tab
   - Add your custom domain to the "Inject Scripts" permission (e.g., `https://yourdomain.com/*`)

If you leave the Gateway Script URL field blank, the template will use the standard Snap servers (default behavior).

## Feedback

To submit feedback, see the [Github issues](https://github.com/Snapchat/snapchat-google-tag-manager/issues) section.
