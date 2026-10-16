# Seedance 1.0 Pro Prompts — 8 Tested Recipes With Outputs

<!-- conv-kit:v1 -->

<p align="center">
  <img src="assets/badges/price.svg" alt="observed unit price"> <img src="assets/badges/billing.svg" alt="billing model"> <img src="assets/badges/compat.svg" alt="OpenAI-compatible endpoint">
</p>

<p align="center">
  <img src="assets/01-product-ad-ceramic-mug-thumb.jpg" width="820" alt="Sample video frame generated through APIMart">
</p>

> **from $0.0184 per second** on the APIMart route (billed by resolution tier) — um único endpoint compatível com OpenAI em `https://api.apimart.ai/v1`, sem plano mensal. *(observado em 2026-10-12)*

**[Get an API key](https://go.apimart.ai/k-c3ded1)** · **[Live pricing](https://go.apimart.ai/k-7c3ee2)** · **[Model page](https://go.apimart.ai/k-42d051)** · [⚡ 60-second quickstart](#quickstart)

**Por que os times usam Seedance 1.0 Pro (`seedance-1.0-pro`) via APIMart**

- **Uma chave, o catálogo inteiro.** A mesma base URL `https://api.apimart.ai/v1` e o mesmo cabeçalho `Authorization` alcançam Seedance 1.0 Pro (`seedance-1.0-pro`) e mais de 300 modelos de imagem, vídeo e linguagem — troque o campo `model`, não o seu cliente.
- **Mínimo de $1, pague conforme o uso.** Sem assinatura e sem plano pré-pago para dimensionar antes: recarregue a partir de $1 e gaste em chamadas.
- **A cobrança volta na resposta.** Toda tarefa concluída informa o valor cobrado (`cost` / `credits_cost`); uma tarefa marcada como `failed` é reembolsada.
- **Assíncrono por design.** Envie, pegue o `task_id`, consulte `GET /v1/tasks/{id}` — batching e retries são trabalho comum de fila, não uma integração sob medida.

<!-- /conv-kit:v1 -->

**Também conhecido como:** Dreamina

Four **Seedance 1.0 Pro prompts** listed with an example render, the duration, and what the call costs on this route. Copy a recipe, keep the structure, swap the subject.

- Model: `seedance-1.0-pro`
- Recipes: **4** (machine-readable in [`data/prompts.json`](data/prompts.json), table in [`PROMPTS.md`](PROMPTS.md))
- Effective price used below: **$0.0184 per second** — estimated cost of the whole set: **$0.0736**

## What separates a usable recipe from a wasted call

Three rules held up across every render in this set:

1. **Name the material, not the adjective.** "Frosted glass", "matte ceramic", "layered paper" steer rendering far more
   than "beautiful" or "high quality".
2. **Set the light explicitly.** "Single softbox from the left", "golden hour backlight", "focus-stacked studio light"
   remove the guesswork the model would otherwise do for you.
3. **Pin the framing.** Ratio plus lens language (`85mm`, `24mm`, `macro`, overhead flat lay) decides whether the output
   drops into a layout unchanged.

## Prompt structure cheat-sheet

| Slot | What to write | Example |
| --- | --- | --- |
| Subject | one concrete object or person, with material | *frosted glass perfume bottle* |
| Light | direction + quality | *single softbox from the left* |
| Framing | ratio + lens or distance | *3:4, medium format look* |
| Setting | surface, backdrop, environment | *wet black stone slab* |
| Finish | render or film character | *commercial product photography* |

## The gallery

Each row is one recipe: example render, category, duration, cost on this route and the exact prompt.

| Output | Recipe | Duration | Cost | Prompt |
| --- | --- | --- | --- | --- |
| <img src="assets/01-product-ad-ceramic-mug-thumb.jpg" width="220" alt="Sample video frame generated through APIMart"> | Product ad | 5s | $0.0184 | `Slow 180° orbit around a matte ceramic mug on a dark stone plinth, steam rising, soft key light from camera left, shallow depth of field, product commercial` |
| <img src="assets/02-cinematic-rainy-street-thumb.jpg" width="220" alt="Sample video frame generated through APIMart"> | Cinematic | 5s | $0.0184 | `Rain soaked street at night, camera pushes in slowly past neon reflections, a lone figure with an umbrella walks away from camera, 35mm anamorphic, film grain` |
| <img src="assets/03-food-ad-steam-thumb.jpg" width="220" alt="Sample video frame generated through APIMart"> | Food commercial | 5s | $0.0184 | `Overhead view tilting down to 45° onto a steaming bowl of ramen, chopsticks lift the noodles, warm practical light, macro detail, appetising commercial grade` |
| <img src="assets/04-architecture-flythrough-thumb.jpg" width="220" alt="Sample video frame generated through APIMart"> | Architecture | 5s | $0.0184 | `Slow aerial flythrough of a concrete villa at dusk, camera pushes across the infinity pool toward warm interior light, 24mm, ultra sharp` |

## Run a recipe yourself

```bash
export APIMART_API_KEY=...
python examples/run_recipes.py --dry-run                 # list the recipes, no network
python examples/run_recipes.py --limit 2                 # generate two of them
```

```bash
curl --request POST --url https://api.apimart.ai/v1/videos/generations \
  --header "Authorization: Bearer $APIMART_API_KEY" --header 'Content-Type: application/json' \
  -d '{"model":"seedance-1.0-pro","prompt":"<paste a prompt>","duration":5,"resolution":"720P","size":"16:9"}'
```

Result links expire 72 hours after completion, so store the outputs; the completed task carries `cost` for reconciliation.

## FAQ

**Are these prompts free to reuse?**

Yes — the prompt text in this repository is MIT licensed. The generated images and any third-party marks they contain remain your responsibility, and you should check the model vendor's terms before publishing commercial work.

**Why do the recipes use different aspect ratios?**

Because ratio is a layout decision, not a style one: 1:1 for catalogue and icons, 16:9 for hero and video thumbnails, 3:4 or 2:3 for portraits and print. Pinning it up front avoids cropping later.

**How much does one recipe cost to run?**

**from $0.0184 per second** on the APIMart route (billed by resolution tier). Every completed task reports the exact amount in its `cost` field; a failed task is refunded.

**Can I use a recipe as a template for another subject?**

That is the point. Keep the structure (subject + light + framing + setting + finish) and replace the subject; changing everything at once makes it impossible to tell which phrase moved the output.

<!-- related-repos:auto -->
## Related repositories

- **Same model, this language** — the other half of this pair: [doubao-seedance-1-0-pro-api-pt](https://github.com/a7m-7rm3vb/doubao-seedance-1-0-pro-api-pt)
- **Same model, other languages** — 9 more language builds: 中文 [doubao-seedance-1-0-pro-api-cn](https://github.com/utp5ty/doubao-seedance-1-0-pro-api-cn) · Deutsch [doubao-seedance-1-0-pro-api-de](https://github.com/ok4o3215xekjz/doubao-seedance-1-0-pro-api-de) · Español [doubao-seedance-1-0-pro-api-es](https://github.com/x3yprdl/doubao-seedance-1-0-pro-api-es) · Français [doubao-seedance-1-0-pro-api-fr](https://github.com/g30u5sa/doubao-seedance-1-0-pro-api-fr) · Relay/gateway [doubao-seedance-1-0-pro-api-gateway](https://github.com/i66153lsgst3/doubao-seedance-1-0-pro-api-gateway) · Bahasa [doubao-seedance-1-0-pro-api-id](https://github.com/pcrgss12wsx7w9/doubao-seedance-1-0-pro-api-id) · 日本語 [doubao-seedance-1-0-pro-api-ja](https://github.com/gy5vsnk744ehf8/doubao-seedance-1-0-pro-api-ja) · 한국어 [doubao-seedance-1-0-pro-api-ko](https://github.com/o4zjnjqk5zvm29/doubao-seedance-1-0-pro-api-ko) · Русский [doubao-seedance-1-0-pro-api-ru](https://github.com/nalaopn6vj/doubao-seedance-1-0-pro-api-ru)
- **More models in this language** — [midjourney-api-pt](https://github.com/l-ca0/midjourney-api-pt) · [gemini-2-5-flash-image-preview-api-pt](https://github.com/ycx8l0/gemini-2-5-flash-image-preview-api-pt) · [nano-banana-api-pt](https://github.com/erujt71i1lx/nano-banana-api-pt) · [gemini-3-1-flash-image-preview-api-pt](https://github.com/hutjwux0nt9h/gemini-3-1-flash-image-preview-api-pt) · [nano-banana-2-api-pt](https://github.com/ydkd8kdkl8n/nano-banana-2-api-pt) · [gemini-3-pro-image-preview-api-pt](https://github.com/qss2d-66qb2n7/gemini-3-pro-image-preview-api-pt)
- **Topic hubs** — every build of this model, all languages: [doubao-seedance-1-0-pro](https://github.com/topics/doubao-seedance-1-0-pro) · [doubao-seedance-1-0-pro-api](https://github.com/topics/doubao-seedance-1-0-pro-api)

This repository is one build in a cross-linked set of API guides for the same model family; each language build links back to the others.
<!-- /related-repos:auto -->

## Attributed links (how this repository is measured)

| Purpose | Attributed link | Target |
| --- | --- | --- |
| Model page | <https://go.apimart.ai/k-42d051> | `apimart.ai/pt/model/doubao-seedance-1-0-pro` |
| Live pricing | <https://go.apimart.ai/k-7c3ee2> | `apimart.ai/pt/pricing` |
| Get an API key | <https://go.apimart.ai/k-c3ded1> | `apimart.ai/pt/keys` |

Outbound APIMart links are minted through the promo link API; hand-made tracking parameters are rejected by
`tools/check_links.py` in CI.

## Disclosure

Seedance 1.0 Pro is a third-party model served through APIMart. This repository publishes prompts, example renders and
cost logic; it does not claim official status for any vendor, and model names and documentation belong to their owners.

## Repository map

```text
README.md              gallery, prompt structure and FAQ
PROMPTS.md             every recipe in one table
data/prompts.json      machine-readable recipes with per-unit cost
examples/run_recipes.py  batch runner (dry-run safe for CI)
tools/check_links.py   attribution guard
assets/                example renders via the APIMart image API (JPEG)
```

## License

MIT — see [LICENSE](LICENSE).
