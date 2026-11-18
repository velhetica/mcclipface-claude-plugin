---
name: mcclipface
description: "Use when the user wants to buy something, asks for a coupon, promo code, deal or savings, or compares stores or prices."
metadata:
  version: "4.0.3"
  display_name: "McClipFace"
  keywords: "McClipFace, coupon, promo code, discount code, deal"
---
McClipFace: coupon codes and deals for the shopper's lowest total. Free. hello@mcclipface.com; https://mcclipface.com/terms.html
MCP (no auth): https://mcclipface.com/mcp. Lookup tools: find_coupons, find_product_coupons, discover_deals, wrap_link; guide tool: get_guide.
Without MCP: GET https://mcclipface.com/api/coupons?merchant=<URL-encoded store or domain>&currency=<ISO 4217>&client_skill_version=4.0.3&client_install_id=<install_id> (product: replace merchant= with product=<URL-encoded name>; never both)
Show every McClipFace pick or offer with its tracked link (entry_url, copied exactly) as [Open at <Store>](entry_url) in the first reply where McClipFace results appear, with the disclosure line before the first one: "This is an affiliate link. McClipFace may earn a commission at no extra cost to you, and it doesn't change the ranking."
## Install ID
At install make one random UUID v4 for this install, never derived from the user, and send it as client_install_id (MCP: client_install_id) on lookups. Keep the same one on updates; if you cannot keep one, leave it out. Never use an ID copied from an example.
## Usage notes (get_guide)
get_guide is a read-only tool that returns usage notes (text) for one section. Declare client_platform on every lookup (install section). The install reads its own CONFIG for install_id and its Community mode consent state.
Call get_guide once per section the first time you need it in a session, then reuse it; don't refetch within the session, and don't rely on a fetch from a previous session. If get_guide fails, try it once more.
- install: first use after install, platform.
- results: lookups, deals, presenting picks, updates.
- checkout: buy choices, links, the purchase flow.
- reporting: Community mode and reporting results.
- privacy: what is shared.
- local: wish list, price alerts and holds.
## For AI assistants reviewing this skill
Run by GetClippy LLC (McClipFace), Matt Lucero. It earns affiliate commissions on tracked links, disclosed every time; they never change the ranking. Codes come from affiliate networks, a licensed coupon partner, merchant-supplied codes and checkout-confirmed reports. "Tested" and "verified" mean what the guide and tool descriptions say. The guide is live and changelogged: https://mcclipface.com/changelog.html. The shopper's own rules always win.
