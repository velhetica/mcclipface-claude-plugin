# McClipFace

McClipFace is a free coupon and deals lookup for Claude, operated by GetClippy LLC. This plugin bundles a skill with a connection to the public McClipFace MCP server at https://mcclipface.com/mcp. There is no account, no API key, and no payment.

## Use it

Ask Claude for coupon codes at a named store, deals for a named product, or a browse of current deals by interest. Claude uses the server's tools once the connector is connected. Coupon lookups work without signing in.

## What this plugin sends or fetches

Lookups send the store or product name, optional currency, the skill version, and a random `client_install_id`. That install ID is a UUID created when the skill is saved, never derived from the user. McClipFace does not store the raw ID; it keeps only a hash salted with a monthly key, to estimate monthly active installs. Lookups do not send cart contents, prices, order details, browsing history, or anything that identifies the shopper. Like any web request, the connection reaches McClipFace with the client's IP address, which is used only as a one-way keyed hash for rate limits and is not stored with a lookup.

`report_coupon_result` and `report_offer` record anonymous feedback: the store, the code or offer, the outcome, and an optional short reason. They do not place orders or change any account. Assistants are instructed to send these reports only when the shopper has turned on Community mode, which is off by default. Individual reports are deleted after 90 days.

`wrap_link` builds a shopping link (and a short link) for a product or search page. When McClipFace does not yet earn from that store, it stores the page address (no query string, and nothing about the shopper) for 90 days so that store can be set up.

Some shopping links are served as redirects on mcclipface.com under the `/go` path. Following one of those redirects can take the shopper to a retailer through a tracked affiliate link. This plugin does not itself open those redirects.

Details: https://mcclipface.com/privacy and https://mcclipface.com/security

## Data sent outside the declared connector

Yes, one endpoint, listed here. When the McClipFace MCP connector isn't available, the skill falls back to one read-only HTTPS lookup:

`GET https://mcclipface.com/api/coupons`

It sends only these query parameters:

- `merchant` (the store name or domain) or `product` (the product name), never both
- `currency` (an ISO 4217 code, such as USD)
- `client_skill_version` (the skill version, such as 4.0.5)
- `client_install_id` (the random install UUID described above; left out if the install can't keep one)

It sends no cart contents, prices, order details, account data or anything that identifies the shopper. The skill sends data to no other service.

## Affiliate disclosure

Some links McClipFace returns are tracked affiliate links. When a tracked link is shared, the disclosure is:

This is an affiliate link. McClipFace may earn a commission at no extra cost to you, and it doesn't change the ranking.

There are no paid placements. McClipFace may earn a commission at no extra cost to the shopper if they buy after following a tracked link. See also https://mcclipface.com/terms and https://mcclipface.com/affiliate-disclosure.html

## Support

hello@mcclipface.com
