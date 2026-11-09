# Leapio Analytics for Google Tag Manager

Add [Leapio](https://www.leapio.com) to your site through Google Tag Manager, with no code changes.
Leapio is analytics for go-to-market teams: the tag starts automatic pageviews, and you can track
events and revenue from your other tags.

## Install

1. In Google Tag Manager, open **Templates → Tag Templates → Search Gallery**, find **Leapio Analytics**, and
   add it to your workspace.
2. Go to **Tags → New**, choose **Leapio Analytics**, and paste your project's public key. It starts with
   `pk_`; find it on your project's install screen in the Leapio dashboard.
3. Under **Triggering**, choose **Consent Initialization - All Pages** if you use a consent banner,
   otherwise **All Pages**. Fire the tag once per page; Leapio tracks pageviews after that.
4. Use **Preview** to check the tag fires, then **Submit** to publish your container.

### Install Without the Gallery

Download [`template.tpl`](template.tpl) from this repository, then in Google Tag Manager open
**Templates → Tag Templates → New → ⋮ → Import** and select it. Continue from step 2 above.

## Fields

| Field | Required | What it does |
|---|---|---|
| Leapio public key | Yes | Your project's public key (`pk_...`). |
| Cookie domain | No | For example `.example.com`, to count visitors across subdomains. |
| Pageviews channel | No | A label recorded on automatic pageviews. |
| Consent source(s) | No | Comma-separated: `concord`, `onetrust`, `usercentrics`, `cookiebot`, `gcm`. |
| Consent behavior | No | `implied` or `express`. The default follows your Leapio dashboard setting. |
| Strip query parameters | No | Removes query parameters and the hash from tracked URLs. |

Only the public key is used; no secret key is involved. Leapio always enforces consent on its
servers, whatever these settings are.

## Track Events

Once the Leapio tag has loaded, `window.leapio` is available to your other tags. For example, in a
Custom HTML tag sequenced after the Leapio tag:

```html
<script>
  window.leapio &&
    window.leapio.track({ event: 'NewsletterSignup', metadata: { source: 'footer' } });
</script>
```

## Permissions

- **Injects scripts:** only `https://cdn.leapio.com/lp.js`.
- **Logs to console:** in Preview mode only.

## Support

- Documentation: https://www.leapio.com/docs/integrations/google-tag-manager
- Email: support@leapio.com

## License

Apache 2.0. See [LICENSE](LICENSE).
