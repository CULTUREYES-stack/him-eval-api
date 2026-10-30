# HIM-Eval API

```
❯ him-eval api
  an open-model evaluation service, judged by MIZAN
  ________________________________________________

  website    https://eval.cultureyes.ae   ← not a dev? go here, no code needed
  api        /api/v1      sign in, submit models, run evaluations
  hub        /public      the Leaderboard, downloads, chat with MIZAN
  errors     RFC 9457 problem+json, 35 codes, bilingual reasons
  ________________________________________________
```

## What is HIM-Eval?

You upload a model. We run it inside **HIM** — our adaptive inference engine that accepts
any model format, no adapter, no conversion, no coding. A blind judge operator named
**MIZAN (ميزان)** grades every answer by meaning. You get a report: strengths, gaps, what
your model needs. Results go to a public, bilingual (العربية / English) Leaderboard.

It exists because existing leaderboards refuse models that ship their own code. The
Open Arabic LLM Leaderboard would not accept our own model for that reason. Exact-match
scoring is broken — in our own test, word matching scored 37/100 while reading the
answers by meaning gave 45/100. HIM-Eval accepts **any model** and judges by meaning.

**Not a developer?** Go straight to **[eval.cultureyes.ae](https://eval.cultureyes.ae)** —
sign in, upload, watch live status, read your report, chat with MIZAN about the results.
This repo is the API for developers who want to script it.

## Created by Mohamed Al Hajeri

HIM-Eval is created and architected by **Mohamed Al Hajeri** — **NVIDIA Inception**
builder, running on the **AWS cloud**.

Two of his creations meet in this service:

- **MIZAN (ميزان)** — the judge that scores every model's answers, born on
  [opsoul.dev](https://opsoul.dev/operators/d5ce4ed7-aa04-470c-b26b-4575d024bdf4),
  his operator platform. The judge grew from there under its own charter, and this
  service holds it accountable: pinned by version, qualified before it serves anyone.
  Live qualification: **8/8 grading agreement, 100%**.
- **HIM — the Hajeri Inference Manager** — the next-level inference engine, also his
  creation. Self-installing, hardware-adaptive, zero cold start. The models this
  service evaluates run on HIM, and it is working and running here, now.

## What the service does

Models run in GPU-isolated sandboxes, one at a time. MIZAN grades every answer blind
— owners never enter the judgment — and the results publish to a public, bilingual
(العربية / English) Leaderboard. Model owners submit models, watch live status, read
results, and publish. Everyone else reads the Hub and can ask MIZAN about the results
in their own language.

## Connect in 30 seconds

```bash
# The service is alive
curl https://eval.cultureyes.ae/api/v1/health

# The public Leaderboard — no authentication
curl https://eval.cultureyes.ae/public/seasons

# Ask MIZAN which model did best this season (anonymous, rate-limited)
curl -X POST https://eval.cultureyes.ae/public/hub-chat/messages \
  -H "Content-Type: application/json" \
  -c cookies.txt \
  -d '{"message": "Which model scored highest this season?"}'
```

## Authentication

Sign in through the browser (OIDC authorization-code with PKCE) at
`https://eval.cultureyes.ae` — the session is an HMAC-signed cookie. For scripts and
pipelines, create a Personal_Access_Token:

```bash
# after signing in, create a token — the full value is shown exactly once
curl -X POST https://eval.cultureyes.ae/api/v1/auth/tokens \
  -b cookies.txt -H "Content-Type: application/json" \
  -d '{"name": "ci pipeline"}'

# then use it everywhere a session works
curl https://eval.cultureyes.ae/api/v1/whoami \
  -H "Authorization: Bearer ***"
```

Tokens carry no admin rights and never carry MFA — administrator actions need a
multi-factor authenticated session.

## The developer flow

```bash
# 1. create a Submission for your model
curl -X POST https://eval.cultureyes.ae/api/v1/submissions \
  -H "Authorization: Bearer ***" -H "Content-Type: application/json" \
  -d '{"model_name": "MyModel-1B", "stated_licence": "apache-2.0", ...}'

# 2. upload weights and declaration — resumable tus uploads at /files,
#    every file announced with its SHA-256, re-verified by the service

# 3. request an Evaluation_Run
curl -X POST https://eval.cultureyes.ae/api/v1/submissions/$ID/runs \
  -H "Authorization: Bearer ***"

# 4. poll live status (updates within 60 seconds)
curl https://eval.cultureyes.ae/api/v1/runs/$RUN_ID -H "Authorization: Bearer ***"

# 5. read results, publish to the Leaderboard when you are ready
curl -X POST https://eval.cultureyes.ae/api/v1/runs/$RUN_ID/publication \
  -H "Authorization: Bearer ***"
```

## Errors: one format, always

Every refusal is `application/problem+json` (RFC 9457), with a stable `code`, the
HTTP status, and the reason in the caller's own language:

```json
{
  "type": "/docs/api/errors/quota_exhausted",
  "title": "The free-run quota is exhausted.",
  "status": 409,
  "code": "quota_exhausted",
  "detail": "You have used all free runs for this period. Your quota renews at 2026-11-01T00:00:00Z.",
  "instance": "/api/v1/submissions/…/runs"
}
```

All 35 codes, statuses, and both languages' reasons: [docs/errors.md](docs/errors.md).
Every endpoint of both apps: [docs/endpoints.md](docs/endpoints.md).

## The typed client

`client/api-client.ts` is generated from the live OpenAPI documents — 96 operations,
zero dependencies, plain `fetch`. Copy the file, or:

```bash
npm install @cultureyes-stack/him-eval-api
```

## The OpenAPI documents

- [`openapi/main.json`](openapi/main.json) — the HTTP_API (`/api/v1`)
- [`openapi/hub.json`](openapi/hub.json) — the public Hub (`/public`)

Interactive docs live at `https://eval.cultureyes.ae/en/docs` (English) and
`/ar/docs` (Arabic).

## Conventions

- Every `POST` accepts an `Idempotency-Key` header; a replay answers the original
  result instead of acting twice.
- Recorded results never change: writes to result paths answer
  `409 results_immutable` and are audited.
- Public pages and downloads cache for 20 seconds; the conversation transcript never
  caches.
- Hub_Chat keeps conversations for the stated retention period and then deletes
  them; the rate limit counts each answered message once.

## License

MIT
