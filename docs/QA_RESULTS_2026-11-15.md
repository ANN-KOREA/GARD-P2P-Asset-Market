# QA results at source package creation — 2026-11-15

| QA gate | Result | Evidence | Scope |
|---|---|---|---|
| JS syntax | PASS | `node --check js/*.js sw.js` | Parse only; not runtime |
| Unit tests | PASS (7/7) | `npm test` | ZIP roundtrip, CRC, catalog whitelist, HTML escaping, SHA256, transition mapping, CSV quoting |
| Public catalog whitelist | PASS | `npm run check:catalog` | Initial empty catalog only |
| HTML references and IDs | PASS | Python stdlib static parse | All three pages, local references, duplicate IDs |
| HTTP static file response | PASS | `curl -I http://127.0.0.1:8765/owner.html` | HTTP 200 from development server, not UI |
| Full browser journey | BLOCKED | Chromium/Playwright navigation error `ERR_BLOCKED_BY_ADMINISTRATOR` on local HTTP, file and test URLs | Not treated as PASS; runnable smoke test included |
| New GitHub repo creation | NOT_DONE | Connected GitHub actions in current environment did not expose `create_repository` | ZIP prepared; user can create repository through GitHub UI or Windows script |
| Netlify deployed site | NOT_RUN | No authorized Netlify deployment performed | Pending user repository and Netlify connection |
| Real email, bank payment, buyer | NOT_RUN | No external participants or bank transactions | Must be independently verified |

The README and `docs/TESTING.md` include acceptance criteria. Do not infer customer demand, paid conversion, rights clearance or legal compliance from test data.
