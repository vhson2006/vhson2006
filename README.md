# Hi, I'm Van Hai Son, an AI Engineer

I build LLM features that run in production, and the platform under them.
My current project runs 9 business websites and their admin on one Kubernetes
cluster: live at [shanovina.com](https://www.shanovina.com).

## AI work in production
- **RAG chat on 9 sites**: multilingual embeddings run locally (e5-small on WASM, no
  vector DB), hybrid BM25 + vector retrieval, score thresholds that refuse off-topic
  questions without calling the model, and code checks that reject prices or services
  the shop never published. Eval suite (56/56), daily limits, a masked question log.
- **AI content pipeline**: article outline → structured blocks → draft with generated
  images, machine translation into each site's languages, text-to-speech, and video
  renders (Remotion) on an autoscaled node pool (KEDA 0↔1).
- **One AI gateway service**: the only caller of model providers (Gemini today,
  provider-agnostic), event-driven over NATS JetStream with outbox/inbox, retries
  and refusal handling.
- **Cost visibility per tenant**: every billed call is metered where it happens (thinking
  and tool tokens, failed and retried calls), then priced per model in a monthly
  report per site.
- **Telegram bot for shop staff**: OAuth device sign-in and signed start links; it acts
  with each user's own permissions.

## Engineering
- **Microservices**: 7 NestJS services, PostgreSQL + Prisma per service, a private
  KrakenD gateway, Keycloak (multi-realm, OTP, per-site roles), audit log, RFC 9457 errors.
- **Web**: Next.js BFF (tokens never reach the browser), shared design system,
  vi/en i18n, strict CSP.
- **Platform**: Kubernetes on DigitalOcean, GitOps with Argo CD + Kustomize, External
  Secrets (Doppler), Grafana Cloud observability, Trivy + SBOM in CI.
- **Practice**: ~80 architecture decision records, HTTP tests on every route (401/403
  included), AI-assisted development with Claude Code under written project rules.

## Stack
TypeScript · Node.js · NestJS · Next.js / React · PostgreSQL · Prisma · Redis ·
NATS JetStream · Keycloak · KrakenD · Docker · Kubernetes · Argo CD · Gemini API · RAG

## Open to AI Engineer roles
Based in Ho Chi Minh City. The sites are live: [www](https://www.shanovina.com) ·
[spa](https://spa.shanovina.com) · [hotel](https://hotel.shanovina.com) ·
[laundry](https://laundry.shanovina.com) · [flowers](https://flowers.shanovina.com).
