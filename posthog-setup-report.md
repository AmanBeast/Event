<wizard-report>
# PostHog post-wizard report

The wizard has completed a deep integration of PostHog into the DevEvent Next.js App Router project. PostHog is initialized via `instrumentation-client.ts` (the recommended approach for Next.js 15.3+), which runs before React hydration. A reverse proxy is configured in `next.config.ts` to route all PostHog traffic through `/ingest`, improving ad-blocker resilience. Three client-side components were instrumented to capture user interactions: the Explore Events CTA, event cards, and navbar links.

| Event Name | Description | File |
|---|---|---|
| `explore_events_clicked` | User clicks the 'Explore Events' CTA on the homepage hero section. | `components/ExploreBtn.tsx` |
| `event_card_clicked` | User clicks an event card to navigate to the event detail page. Properties: `event_title`, `event_slug`, `event_location`, `event_date`. | `components/EventCard.tsx` |
| `nav_link_clicked` | User clicks a navigation link in the top navbar. Properties: `label`, `href`. | `components/navbar.tsx` |

## Next steps

We've built some insights and a dashboard for you to keep an eye on user behavior, based on the events we just instrumented:

- [Analytics basics (wizard) — Dashboard](https://us.posthog.com/project/473504/dashboard/1775914)
- [Explore Events Clicks (30d)](https://us.posthog.com/project/473504/insights/GVKKRbFo)
- [Event Card Clicks (30d)](https://us.posthog.com/project/473504/insights/Wk8VZ6FA)
- [Most Clicked Events](https://us.posthog.com/project/473504/insights/nu6ElX1h)
- [Navigation Engagement](https://us.posthog.com/project/473504/insights/2Gdf9WKR)
- [All User Actions](https://us.posthog.com/project/473504/insights/wG9Ai2hP)

## Verify before merging

- [ ] Run a full production build (`npm run build`) and fix any lint or type errors introduced by the generated code.
- [ ] Run the test suite — call sites that were rewritten or instrumented may need updated mocks or fixtures.
- [ ] Add `NEXT_PUBLIC_POSTHOG_PROJECT_TOKEN` and `NEXT_PUBLIC_POSTHOG_HOST` to `.env.example` and any monorepo/bootstrap scripts so collaborators know what to set.
- [ ] Wire source-map upload (`posthog-cli sourcemap` or your bundler's upload step) into CI so production stack traces de-minify.

### Agent skill

We've left an agent skill folder in your project at `.claude/skills/integration-nextjs-app-router/`. You can use this context for further agent development when using Claude Code. This will help ensure the model provides the most up-to-date approaches for integrating PostHog.

</wizard-report>
