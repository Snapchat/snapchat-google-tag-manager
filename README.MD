# Snap Pixel Community Template

The Snap Pixel community template is a Google Tag Manager [community gallery template repository](https://support.google.com/tagmanager/answer/9454109) that can be used to easily implement Snap Pixel using Google Tag Manager.

## Debugging and Console Logging

By default, the template does not log to the browser console to prevent performance issues during testing and debugging sessions with GTM Tag Assistant.

**To enable console logging for debugging:**

1. Open your Snap Pixel tag configuration in GTM
2. Scroll to the "Enable Console Logging (Debug Mode)" checkbox
3. Check the box to enable detailed console logging
4. Save and preview your container

When enabled, the template will output initialization data and event tracking information to the browser console during GTM preview/debug mode. This can be helpful for:
- Verifying configuration values
- Troubleshooting tracking issues
- Confirming data layer mappings

**Note:** Keep this option disabled during normal operations or if you experience performance issues during testing sessions, as logging large data objects can impact preview performance.

## Conversions API Gateway Support

This template supports the Conversions API Gateway, which allows you to serve the Snap Pixel script from your own first-party domain for improved tracking reliability.

**To use a custom gateway URL:**

1. In the template configuration, enter your full gateway script URL in the "Gateway Script URL" field (e.g., `https://yourdomain.com/scevent.min.js`)
2. **IMPORTANT:** You must also update the template's Script Injection permissions:
   A. Edit the template in GTM
   B. Navigate to the Permissions tab
   C. Add your custom domain to the "Inject Scripts" permission (e.g., `https://yourdomain.com/*`)

If you leave the Gateway Script URL field blank, the template will use the standard Snap servers (default behavior).

## Testing a template change

Import this branch's `template.tpl` in a GTM Web container under Templates > Tag Templates > New > Import. Run every scenario in the Tests tab, then save the template. The tests mock GTM APIs and do not send events to Snap.

The template reads the current page URL with `getUrl()` instead of a hidden field. Keep the Reads URL permission enabled so initialization and tracking data continue to include `page_url`.

For a browser check, create two tags from the imported template with the same test Pixel ID. Fire a SIGN_UP tag with Event Tag `qualified_lead` on All Pages, then a PURCHASE tag with no Event Tag on Window Loaded. Leave `event_tag` out of setup-only tags. Connect GTM Preview to a page with that container installed. Confirm both tags show Succeeded, only the SIGN_UP request has `et=qualified_lead`, and `scevent.min.js` appears once in the page's Network panel. A cached response still counts as one script load. Use a real test Pixel ID to check event requests; the all-zero dummy ID used by the mocked tests is rejected by Pixel JS.

## Feedback

To submit feedback, see the [Github issues](https://github.com/Snapchat/snapchat-google-tag-manager/issues) section.
