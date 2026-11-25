<p align="center"><img src="assets/weizerouter-banner.svg" alt="WeizeRouter — A Weize Studio Product" width="100%"></p>

# WeizeRouter · Weize Studio Ecosystem

**AI APIs, developer tools, creative AI and automation — connected through the Weize Studio ecosystem.**

[WeizeRouter](https://weizerouter.com/) · [Weize Studio](https://weizestudio.web.id/) · [Weize Omni](https://weizeomni.web.id/) · [Telegram Bot](https://t.me/WeizeRouterBot) · [Documentation](docs/README.md)

WeizeRouter is the developer API platform in the **Weize Studio** ecosystem, based in Medan, Indonesia. Use supported models through OpenAI-compatible and Anthropic-compatible interfaces, manage developer access on the web, or purchase and manage bot packages through Telegram.

> Public documentation refreshed **26 November 2026**. Product availability, model permissions, prices and payment methods follow the live catalog and checkout. This repository contains public documentation and illustrations, **not production source code**.

## Explore the ecosystem

| Product / service | What it is | Official entry |
| --- | --- | --- |
| **Weize Studio** | Parent technology brand: cloud API, software engineering and automation services | [weizestudio.web.id](https://weizestudio.web.id/) |
| **WeizeRouter / My WeizeRouter** | Developer platform: web registration, purchases, API keys, wallets and usage | [weizerouter.com](https://weizerouter.com/) |
| **WeizeRouter Bot** | Telegram purchasing, balances, keys and personal portal access | [@WeizeRouterBot](https://t.me/WeizeRouterBot) |
| **Weize Omni** | Browser-based AI chat, image and voice workspace with Google login; its own credits | [weizeomni.web.id](https://weizeomni.web.id/) |
| **Weize Audio** | Text-to-speech Studio and API; Audio balance is separate from chat tokens | [Audio Studio](https://weizerouter.com/audio) |
| **WeizeRouter CLI & integrations** | Guides for coding agents, editors and SDK integrations | [CLI guide](https://weizerouter.web.id/cli-guide.html) |
| **WeizeRouter Tube** | Community video tutorials | [Tube](https://weizerouter.web.id/tube/) |
| **Regular personal portal** | Bot customer's own wallet and usage view | Request a private link from the bot |
| **Weize Premium** | Premium model and wallet surface; access follows your account and package | [Premium portal](https://weizerouter.web.id/premium) |
| **Weize Unlimited** | Separate fixed-price, time-limited package family; not the permanent-token wallet product | [Unlimited portal](https://weizerouter.web.id/unlimited) |
| **Weize Uncensored · 18+** | Separate adult-only text service, credentials and balance; subject to lawful-use terms | Access through the bot |
| **Weize Image Turbo** | Credit-based image generation through the Telegram bot | Bot command `/gambar` |
| **Video workspace / catalog** | Separate video product surfaces; model listing is not a guarantee of generation availability | Check the current website / Omni workspace |
| **Official Resellers** | Reseller registration, terms and signature directory; purchase availability varies | [Reseller directory](https://my.weizerouter.web.id/reseller-resmi) |
| **Partner & Referral** | Partnership and referral programs with their own eligibility and terms | Bot menus; [Partner](https://weizerouter.web.id/partner/) |
| **Leaderboard & telemetry** | Public community rankings and usage statistics | [Leaderboard](https://weizerouter.web.id/leaderboard) · website statistics |
| **Weize VPS** | Cloud VPS service information; a visible page does not mean new sales are open | [VPS](https://weizerouter.web.id/vps) |

**Important:** website accounts, bot accounts, Omni credits and product-specific balances are not one shared wallet. Do not assume balances or keys transfer between services. Personal portal links are private.

See [the ecosystem guide](docs/ecosystem.md) for account boundaries and availability notes.

## Developer API

- OpenAI-compatible base URL: **`https://weizerouter.com/v1`**
- Chat completions: **`POST /v1/chat/completions`**
- Discover model IDs: **`GET /v1/models`** using your own key.
- Anthropic-compatible base URL: **`https://weizerouter.com`**, with **`POST /v1/messages`** for supported models.
- Existing `.web.id` API addresses remain available; `.com` is the primary address for new integrations.
- Streaming and tool calling depend on the selected model and client.

Use a model ID returned for **your account**. A catalog listing is not an uptime guarantee or proof that every package can use every model.

### Python quickstart

```python
import os
from openai import OpenAI

client = OpenAI(
    api_key=os.environ["WEIZEROUTER_API_KEY"],
    base_url="https://weizerouter.com/v1",
)
# Set this to an exact model ID available to your account.
model_id = os.environ["WEIZEROUTER_MODEL"]
reply = client.chat.completions.create(
    model=model_id,
    messages=[{"role": "user", "content": "Hello, WeizeRouter!"}],
)
print(reply.choices[0].message.content)
```

[API usage](docs/api-usage.md) · [Models](docs/models.md) · [Editor & SDK integrations](docs/integrations.md) · [Errors](docs/error-codes.md)

## Accounts, packages & payment

**Website:** register / sign in at [weizerouter.com](https://weizerouter.com/), choose a package and payment method, then check your order and wallet in the same account.

**Telegram:** open [@WeizeRouterBot](https://t.me/WeizeRouterBot), choose the product and package, then select the payment method. QRIS is displayed in chat; bank/card flows use the payment page.

**Payments now use Midtrans**, not a QRIS-only checkout description. Supported choices shown by the current checkout can include QRIS, GoPay, bank Virtual Accounts / Mandiri Bill, Visa and Mastercard. Method availability, bank authorization and invoice limits can vary. Transactions settle in **Indonesian Rupiah (IDR)**.

Regular and Premium token wallets are separate. Purchased token balances are permanent; **Unlimited packages have their own duration**, and other products have their own accounting and terms. Model multipliers and package permissions affect usage. Always review the live price and allocation before paying; historic GitHub pricing is not a current offer.

[Packages & balances](docs/packages.md) · [Payment flow](docs/payment-flow.md) · [FAQ](docs/faq.md)

## Support & community

- Admin / purchases: [@wangweize4](https://t.me/wangweize4)
- WhatsApp: [+62 882-7720-0044](https://wa.me/6288277200044)
- Studio support: **support@weizestudio.web.id**
- Community: [@weizerouter_indonesia](https://t.me/weizerouter_indonesia)
- Studio and official channel links: [Weize Studio](https://weizestudio.web.id/)

GitHub Issues are for public documentation feedback. **Never post API keys, private portal URLs, payment credentials, customer data or confidential logs.** Security issues belong in a private report: [Security policy](SECURITY.md).

## Documentation scope

No static badge here certifies live uptime. RPM means requests per minute, **not simultaneous concurrency**. Rate limits are not guaranteed daily or monthly request capacity. Product status pages, account permissions and current checkout take precedence over illustrative documentation.

Documentation is licensed under [MIT](LICENSE). This does not license private production software, grant rights to third-party models, or replace service terms. WeizeRouter and the ecosystem are independently operated; third-party trademarks belong to their respective owners.

**A Weize Studio Product.**
