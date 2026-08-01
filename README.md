# How to export a public MemberClicks member directory

Many associations, chambers, and trade groups run their membership website on [MemberClicks](https://memberclicks.com/) — either **MC Professional** (built around individual-based memberships) or **MC Trade** (built around organization-based memberships, common for chambers). Their online member directory is a common target for anyone trying to build a list of members, prospects, or contacts: sales teams, researchers, journalists, other associations doing market comparisons, and members themselves.

The usual first question is simple: *"How do I export this directory?"* The honest answer is "it depends who you are." MemberClicks ships real export tools, but they are administrator tools that live inside the association's own login — built for the association's staff to export their own membership data, not for an outside visitor to export what the association has chosen to publish. If you are not that administrator and the association has not offered you a file, your options are narrower, and this guide is about using them correctly.

This guide is scoped to one platform and one situation: **a public MemberClicks directory that has no suitable export offered to you**, and how to collect the visible, unauthenticated part of it responsibly. It assumes you already understand the general legal and quality issues around directory-sourced leads; for that broader treatment across multiple platforms — ChamberMaster/GrowthZone, MembershipWorks, Wild Apricot, MemberClicks, Glue Up, and others — see [chamber-association-lead-lists](https://github.com/willowridge1234/chamber-association-lead-lists), a companion guide from the same authors. This one goes deeper on MemberClicks specifically.

**Commercial disclosure:** Rook Data Tools publishes a purpose-built [MemberClicks Directory Scraper](https://apify.com/rook-data-tools/memberclicks-directory-scraper) on the Apify platform, linked in the relevant section below. That link is to our own product, not an independent recommendation. Every other section of this guide stands on its own whether you end up collecting a handful of records by hand, get an export from the association directly, or use a tool — ours or anyone else's.

## Who this is for

- A salesperson or founder who wants a lead list of a MemberClicks-hosted association's public members.
- A researcher, journalist, or comparison shopper who needs a defensible snapshot of a public membership roster.
- An association staffer evaluating a *different* association's public directory, who doesn't have (and shouldn't ask for) that association's own admin login.
- Anyone who tried the obvious "export" button and found it either doesn't exist for them or sits behind a login they don't have.

This guide does not cover accessing your own association's data as its administrator — MemberClicks' own help documentation already covers that — and it does not cover accessing any member-only or login-gated area under any circumstance.

## First, recognize a MemberClicks site

Before deciding anything about export, confirm you're actually looking at a MemberClicks-powered directory rather than a different association management platform, since the ownership, terms, and available tools differ by vendor.

Use visible evidence only: MemberClicks branding in the site footer, on the sign-in screen, on a "powered by" line, or in help/support links. MemberClicks' own materials describe the product as association management software offering "membership websites" with searchable "online directories," running as either MC Professional or MC Trade depending on whether the association's members are individuals or organizations. If you see none of that and the directory looks similar, don't guess from layout alone — record the platform as unknown. Misidentifying the platform is how people end up citing the wrong vendor's terms or the wrong tool.

## Why the built-in "export" usually isn't available to you

MemberClicks' own documentation describes real export paths — a Reporting → Exports screen, and a Profile List where an administrator can tag records and export selected fields to CSV, plus separate Excel/CSV export options inside MC Trade's Membership Directory Report. These are genuine, well-built tools. They are also **administrator tools**, reached only after logging into the association's own MemberClicks backend with staff-level credentials.

If you are not that association's administrator, that export does not exist for you, no matter how the directory looks from the outside. Three honest paths follow from that:

1. **Ask.** If your use case is legitimate — a partnership, a sponsorship, a research project the association might support — ask the association directly for an export or an API-style feed. Many will say yes to a clearly stated, reasonable request faster than any technical workaround gets you a clean result. This is the only path that can also get you fields the public page doesn't show.
2. **Use whatever public export the association *did* build for visitors**, if one exists — an RSS feed, a downloadable member list, a public API. Some associations publish these; check the directory page itself and its help or FAQ links before assuming none exists.
3. **Collect only what the public directory page already displays to any visitor**, without logging in, if neither of the above applies and the site's own rules allow it. The rest of this guide is about doing that third path correctly and knowing when not to.

## What a public MemberClicks directory may show — and what it won't

There is no single MemberClicks record format. Each association's administrator decides which profile fields exist, which are shown on the public-facing directory versus only to logged-in members, and which are hidden from members entirely. MemberClicks' Group Attribute Security documentation describes exactly this: individual attributes can be marked so a viewer can edit them, only view them, or not see them at all. What a directory shows one visitor may not match what it shows a logged-in member, and it will vary from one association's MemberClicks site to the next.

Because MC Professional is built around individual memberships and MC Trade around organization memberships, the unit of a "record" differs by product too: an MC Professional directory more often surfaces individual people, while an MC Trade / chamber-style directory more often surfaces one profile per member organization, sometimes with multiple staff contacts attached. Confirm which pattern you're looking at before you assume what a "duplicate" even means for that specific directory.

### Fields commonly visible on a public profile, when the association has chosen to show them

- organization or individual member name;
- category, specialty, industry, or member type;
- a public description, services, or keywords;
- city, region, or full mailing address;
- a main phone number;
- a company or personal website;
- social profile links;
- a logo or profile photo;
- a named representative and title, when the association publishes one;
- a public email address or contact form, when the association publishes one.

### What a public directory almost never gives you

- anything behind the member login — private profile fields, member-to-member contact details, event rosters, billing or renewal status;
- fields the association's own attribute security marked hidden;
- reliable revenue, headcount, budget, or purchasing authority;
- confirmation that a named person still holds that role;
- confirmation that a displayed email or phone is actively monitored;
- current buying intent, timing, or need — membership is not a purchase signal;
- the association's underlying export files, reports, or admin-only data.

Treat an empty field as "not shown to the public," not as evidence the association has no such information. Don't fill gaps with guesses.

## The line that matters: public directory vs. member-only area

MemberClicks sites commonly separate a directory a visitor can browse without an account from areas that require a member login to see anything at all. That distinction is the entire boundary for this guide.

- **In scope:** whatever a directory page shows to an ordinary visitor with no account, no payment, no invitation link, and no bypass of any access control.
- **Out of scope, always:** anything that requires signing in as a member, requesting member access, using someone else's credentials, or working around a login wall, a paywall, or a bot challenge. If the only way to see a field is to be a logged-in member, that field is not part of a public collection — full stop, regardless of how the field is displayed once you're inside.

This guide, and the actor linked below, only address the public case. Neither is a substitute for a data-sharing agreement with the association if what you actually need is member-only information.

## Whose terms actually govern the data

This is a MemberClicks-specific trap worth calling out directly: **MemberClicks' own privacy policy is about MemberClicks the vendor, not about any individual association's member data.** MemberClicks' privacy materials describe collecting its own site and product-usage data, and state that when MemberClicks processes personal data as a vendor on behalf of a customer association, that processing follows MemberClicks' contract with the association and *the association's own privacy policy* — not a single MemberClicks-wide member-data policy.

In practice, that means the rules for a specific directory live on that association's own website — its own privacy policy, terms of use, and any acceptable-use language — not on memberclicks.com. Read the association's own pages, not the software vendor's, before deciding what's appropriate.

## Respect the site's own rules, robots.txt, and rate limits

This section is operational guidance, not legal advice, and it isn't specific to MemberClicks — the same standard applies to any public directory.

- Read the association's terms of use and privacy notice for that specific site before collecting anything, and don't proceed if they prohibit your intended use.
- Check the site's `robots.txt`. The [Robots Exclusion Protocol](https://www.rfc-editor.org/rfc/rfc9309.html) is the standard way a site communicates crawler access preferences. Treat it as a floor, not a grant of permission — a path that isn't disallowed can still be off-limits under the site's terms, privacy obligations, or plain common sense.
- Keep any automated request volume conservative, and stop or slow down at the first sign of rate-limit responses, errors, or strain on the site. Never rotate identities, defeat bot challenges, or retry aggressively to push past a block. If getting the data requires bypassing a control, you're outside the boundary this guide describes.
- Never attempt to reach anything behind the member login, under any framing — that includes borrowing a member's credentials, joining specifically to get to non-public data, or treating "visible after I log in" as if it were public.

## Preserve provenance

A directory-sourced record is only as trustworthy as its documented source. For every record, keep:

- the exact profile URL it came from;
- the association's name and its MemberClicks site's domain;
- the date and time you collected it;
- the raw values as displayed, before any cleanup or normalization.

Also record which MemberClicks product pattern the site follows (individual-style directory vs. organization-style directory), since that materially changes how you should interpret a "record" later. If the association migrates platforms in the future, that provenance note is also what tells you why a later collection looks structurally different.

If you're planning to use the actor linked below, note before you rely on it: as of this writing it does not capture the exact profile URL per record described above — see "Where the actor fits" for what it actually preserves.

## Deduplicating MemberClicks-sourced records

Full deduplication method is covered in the [companion cross-platform guide](https://github.com/willowridge1234/chamber-association-lead-lists#how-to-clean-and-deduplicate-a-directory-sourced-list); the MemberClicks-specific wrinkle is the individual-vs-organization pattern above. An MC Trade / chamber-style directory may show one organization profile with several attached staff contacts — decide up front whether your list unit is the organization or each named contact, and don't silently collapse them into duplicates of each other. An MC Professional-style directory more often already lists individuals directly, so the more common duplicate risk is the same person appearing under more than one membership category or chapter.

As with any directory source: keep the raw values, use more than one identity signal (domain, name, phone, address) before merging two records, and don't merge people just because they share an employer.

## When automation is the wrong call

Don't automate collection of a MemberClicks directory when:

- the directory (or the fields you actually need) sits behind a member login;
- the site's terms, robots.txt, or an explicit request from the association say no;
- the directory is small enough to review and copy by hand in a few minutes — a script adds risk for no real benefit;
- what you actually need is verified, current, or private information that no public profile will ever contain — the honest fix is asking the association, not scraping harder;
- the association has already told you no, or you have a live relationship where simply asking is faster and cleaner.

Automation is a convenience for the *public, at-scale, repetitive* case. It is never a workaround for a login wall or a "no."

## Where the actor fits

If you've confirmed the site runs on MemberClicks, confirmed the directory is genuinely public (no login required to view it), checked the association's own terms and `robots.txt`, and decided a public collection is appropriate for your use case, we publish the [MemberClicks Directory Scraper](https://apify.com/rook-data-tools/memberclicks-directory-scraper) on Apify for exactly that job.

What it does, plainly: it exports public MemberClicks directory records — the fields the association has chosen to show an ordinary visitor — as structured data (JSON, CSV, or Excel-ready), with a source URL preserved per record — the directory/search page the run started from, not a distinct profile-page link per member. If your use case needs the exact profile URL described above, the actor does not currently capture that separately; you would need to add it yourself or collect that field manually. It only works against directories that expose public search; it has no path into a member login, and it isn't built or intended to reach anything behind one. It runs pay-per-event on Apify — a small charge to start a run plus a small per-record charge — so cost scales with what it actually returns.

In the interest of not overselling a new listing: it is new, has no reviews yet, and we don't yet have independent evidence of how many people have used it beyond ourselves. Judge it on the Apify listing's own current stats and on a small test run against a directory you already understand, not on anything claimed here.

We don't publish how it identifies or reaches directory data — consistent with the rest of this guide, the goal is a described outcome, not a technique write-up.

## Final checklist

Before collecting anything from a MemberClicks directory:

- [ ] Confirmed the site is actually MemberClicks, from visible evidence, or marked it unknown.
- [ ] Checked whether the association would simply provide an export or feed if asked.
- [ ] Confirmed the specific pages and fields you want are visible to an ordinary visitor with no login.
- [ ] Read that association's own terms of use and privacy notice — not MemberClicks' vendor-level policy — and confirmed nothing there prohibits your use.
- [ ] Checked `robots.txt` and treated it as a floor, not a green light.
- [ ] Planned conservative request volume and a stop condition if the site shows any strain.
- [ ] Decided your list unit (organization vs. individual) before collecting, given the MC Trade/MC Professional pattern difference.
- [ ] Have a plan to preserve source URL, association name, and collection date per record.
- [ ] Ruled out that what you actually need is private, member-only, or unverifiable from a public profile.

## Frequently asked questions

### Can I export a MemberClicks member directory as an outside visitor?

Not through MemberClicks' built-in export tools — those require an association administrator login. If the association hasn't offered you a file and the directory is genuinely public, you're limited to collecting what an ordinary visitor can already see on the page, subject to the site's own terms and robots.txt.

### Does MemberClicks have a public API for member directories?

MemberClicks' own materials describe administrator-facing reporting and export tools, not a public API for outside visitors to query member directory data. Some individual associations publish their own public feeds or downloads; check the specific site before assuming none exists.

### What information is public on a MemberClicks directory?

It depends entirely on how that association configured its directory and its per-field visibility settings — there's no single MemberClicks record shape. Commonly public fields include organization/member name, category, location, phone, website, and a short description; named individual contacts and emails are shown only when the association chose to publish them.

### Is scraping a public MemberClicks directory legal?

There's no universal answer, and this isn't legal advice. Staying outside any login wall, respecting the association's own terms and `robots.txt`, keeping request volume conservative, and using only what's already visible to an ordinary visitor are the baseline conditions. Separately, collecting a public business contact doesn't by itself authorize marketing to it — see the FTC's [CAN-SPAM compliance guide](https://www.ftc.gov/business-guidance/resources/can-spam-act-compliance-guide-business) for US email rules and the UK ICO's [business-to-business marketing guidance](https://ico.org.uk/for-organisations/direct-marketing-and-privacy-and-electronic-communications/business-to-business-marketing/) for a jurisdiction where B2B rules differ from consumer rules. Get legal advice for a high-risk or large-scale use.

### Why isn't MemberClicks' privacy policy the one that governs this data?

Because MemberClicks is the software vendor, not the data owner. Its own privacy policy states that when it processes personal data on behalf of a customer association, that processing follows the association's contract and *that association's* privacy policy — so the operative rules for a specific directory live on the association's own site.

### What's the difference between MC Professional and MC Trade directories?

MC Professional is built around individual-based memberships, so its directories more often list people directly. MC Trade is built around organization-based memberships (common for chambers), so its directories more often list one profile per member organization, sometimes with multiple attached staff contacts. Knowing which pattern applies changes how you should define a "record" and a "duplicate."

## The useful standard

A responsibly collected MemberClicks directory export is not the biggest file you can pull. It's a traceable set of the records that association actually chose to make public, collected without touching anything behind its member login, respecting its own rules, and honest about what it can and can't tell you about intent, timing, or authority. If you need more than that, the association — not a workaround — is the right next step.

## Related

Other free workflows and guides we publish:

- [n8n-ai-lead-scoring](https://github.com/willowridge1234/n8n-ai-lead-scoring) — Free workflow — score scraped leads against your ICP, log to Google Sheets
- [n8n-review-intent-lead-scoring](https://github.com/willowridge1234/n8n-review-intent-lead-scoring) — Free workflow — score G2/Capterra reviewers by switching intent
- [n8n-tradeshow-exhibitor-lead-scoring](https://github.com/willowridge1234/n8n-tradeshow-exhibitor-lead-scoring) — Free workflow — score trade-show exhibitors against your ICP
- [n8n-lead-scoring-guide](https://github.com/willowridge1234/n8n-lead-scoring-guide) — Guide — which signals predict a good lead, and how to tell if scoring works
- [chamber-association-lead-lists](https://github.com/willowridge1234/chamber-association-lead-lists) — Guide — building B2B lead lists from chamber & association directories
- [new-liquor-license-data-guide](https://github.com/willowridge1234/new-liquor-license-data-guide) — Guide + tool — building a lead list from public liquor-licence records
- [chicago-food-service-license-data-guide](https://github.com/willowridge1234/chicago-food-service-license-data-guide) — Guide + tool — building a lead list from Chicago food-service licence records
- [wild-apricot-directory-export-guide](https://github.com/willowridge1234/wild-apricot-directory-export-guide) — Guide — exporting a public Wild Apricot member directory
- [membershipworks-member-directory-export-guide](https://github.com/willowridge1234/membershipworks-member-directory-export-guide) — Guide + tool — exporting a public MembershipWorks member directory
- [chambermaster-directory-export-guide](https://github.com/willowridge1234/chambermaster-directory-export-guide) — Guide — exporting a public ChamberMaster or GrowthZone member directory
