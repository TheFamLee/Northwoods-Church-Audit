# Northwoods Church Staging Site Audit
## northwoods.juxt.studio
**Audit Date:** February 27, 2026
**Prepared for:** Development Team
**Scope:** Spell check, content review, widget/integration audit, site structure, and pre-launch checklist

---

## Table of Contents
1. [Executive Summary](#executive-summary)
2. [Critical Spelling & Content Errors](#critical-errors)
3. [Sitewide Issues (Repeated Across Multiple Pages)](#sitewide-issues)
4. [Page-by-Page Spelling Findings](#page-by-page-findings)
5. [Placeholder / Template Content to Address](#placeholder-content)
6. [Third-Party Widgets & Integrations Audit](#widgets-integrations)
7. [Site Structure & Page Hierarchy](#site-structure)
8. [Pre-Launch Checklist](#pre-launch-checklist)
9. [Pages Not Yet Checked (Rate Limited)](#pages-not-checked)

---

## Executive Summary

A comprehensive spell check was performed across 150+ pages on the Northwoods Church staging site (northwoods.juxt.studio). The audit identified:

- **80+ spelling/grammar/content errors** across the site
- **1 sitewide JavaScript bug** affecting 10+ pages (the "thsi" typo in event fallback text)
- **30+ instances of placeholder text** left in production content ("Your Subtitle Goes Here" x25, "Title Here" x9, "Ministry Partner Name" x2, Lorem Ipsum, "Sermon Title Here" x3+)
- **4 copy-paste/wrong content errors** (Brazil content in India section, "women's ministry" on 55+ Adults, Young Adults, wrong Valentine's URL content)
- **2 potentially wrong dollar amounts** on the Now Is The Time campaign page ($8,000,00 and $15,000,00)
- **1 potentially wrong phone number** (area code 302 vs 309 on OCC page)
- **1 broken URL** (trailing %20 space on volunteer page SERVE button)
- **1 CSS class typo** causing a styling bug on event-details page
- **1 invalid Bible reference** ("1 John 1:14b" doesn't exist - only 10 verses in 1 John 1)

### Priority Levels
- **P0 - Fix Immediately:** Dollar amounts, phone numbers, sitewide JS bug, placeholder text
- **P1 - High:** Wrong ministry references (copy-paste errors), missing words that change meaning
- **P2 - Medium:** Spelling errors, grammar issues, punctuation
- **P3 - Low:** Capitalization inconsistencies, style preferences

---

## Critical Errors

### P0 - Fix Before Launch

| Page | Issue | Details |
|------|-------|---------|
| `/now-is-the-time/` | **Wrong dollar amounts** | "$8,000,00" should be "$8,000,000" (Celebration Goal) and "$15,000,00" should be "$15,000,000" (Dream Goal) - missing final zeros |
| `/occ/` | **Possibly wrong phone number** | Craig Smith listed as "302-243-2740" but all other staff use 309 area code (Peoria, IL). 302 is Delaware. Verify this is correct. |
| **SITEWIDE (6+ pages)** | **JavaScript "thsi" typo** | The inline JS event fallback message reads "There are no upcoming events at **thsi** time." - appears on `/converge/`, `/supportgroups/`, `/getfree/`, `/foursteps/`, `/baptism/`, `/finances/`, `/leadership/`, `/55-adults/`, and likely more. This is user-facing text. |
| `/faq/` | **Placeholder text** | "Your Subtitle Goes Here" appears 9 times under FAQ accordion items |
| `/employment/` | **Placeholder text** | "Your Subtitle Goes Here" appears 3 times under job listing accordions |
| `/events/title-here/` (x9) | **Placeholder pages** | 9 event pages contain Lorem Ipsum text, placeholder dates ("Month X, 2025"), and "Title Here" headings |
| `/series/sermon-title-here/` (x6) | **Placeholder pages** | 6 sermon series pages with placeholder titles |

---

## Sitewide Issues

### 1. JavaScript Event Fallback Text Bug
**Affected pages:** `/converge/`, `/supportgroups/`, `/getfree/`, `/foursteps/`, `/baptism/`, `/finances/`, `/leadership/`, `/55-adults/`, `/marriage/`, `/alpha/`, `/staff-widget/` (8 instances), and any other page using the featured events widget.

The inline JavaScript contains two errors:
```javascript
// ORIGINAL_TEXT (used for matching) has doubled "no":
"There are no currently no featured events."
// Should be: "There are currently no featured events."

// NEW_TEXT (displayed to users) has "thsi" typo:
"There are no upcoming events at thsi time. Check back soon!"
// Should be: "There are no upcoming events at this time. Check back soon!"
```

**Fix:** Search for "thsi" across all page templates and correct to "this". Also fix the doubled "no" in the match string.

### 2. Copy-Paste Ministry Reference Errors
Three pages reference the wrong ministry in their email signup sections:

| Page | Current Text | Should Be |
|------|-------------|-----------|
| `/youngadults/` | "updates on upcoming events and opportunities with **women's ministry**" | "...with **20s & 30s ministry**" |
| `/55-adults/` | "updates on upcoming events and opportunities with **women's ministry**" | "...with **55+ ministry**" or "**adult ministries**" |

### 3. "Your Subtitle Goes Here" Placeholder
Divi theme accordion subtitle fields left with default text on:
- `/faq/` (9 instances)
- `/employment/` (3 instances)

**Fix:** Either remove the subtitle field or replace with meaningful text in Divi accordion module settings.

---

## Page-by-Page Findings

### Homepage (`/`)
| Severity | Error | Correction | Context |
|----------|-------|------------|---------|
| P2 | "walking **along side** you" | "walking **alongside** you" | Welcome section |
| P3 | "life's hurts and **hangups**" | "life's hurts and **hang-ups**" | Get Involved / Freedom section |

### About Page (`/about/`)
| Severity | Error | Correction | Context |
|----------|-------|------------|---------|
| P0 | **"Your Subtitle Goes Here" (x13)** | Remove or replace | Placeholder in Values and Statement of Faith accordions |
| P0 | **"1 John 1:14b"** - invalid Bible reference | Likely should be "**John 1:14b**" (Gospel of John) | Peace measure anchor scripture - 1 John ch.1 only has 10 verses |
| P1 | **Duplicate anchor verse "Luke 19:10"** | About God section needs different verse (e.g., Genesis 1:1) | Luke 19:10 is correctly used for Evangelistic Heartbeat but copy-pasted to About God |
| P1 | **Steps 3 & 4 mismatch with /newhere/** | About: "Step 3: Discover, Step 4: Serve" vs New Here: "Step 3: Serve, Step 4: Join" | Cross-page inconsistency - determine which is correct |
| P2 | "three **personalities**" | "three **persons**" (standard theological term) | About God - Trinity description |
| P3 | "Romans 13**: **13-14" | "Romans 13**:**13-14" (remove extra space) | Freedom measure anchor scripture |

### New Here (`/newhere/`)
| Severity | Error | Correction | Context |
|----------|-------|------------|---------|
| P2 | "walking **along side** you" | "walking **alongside** you" | Welcome section - same as homepage |
| P1 | **Steps 3 & 4 mismatch with /about/** | See About page entry above | Cross-page inconsistency |

### Give Page (`/give/`)
| Severity | Error | Correction | Context |
|----------|-------|------------|---------|
| P1 | "operation **or** the church" | "operation **of** the church" | General Fund card description |
| P2 | "by giving **by giving** to the General Fund" | "by giving to the General Fund" | Duplicated phrase in Giving Options |
| P2 | "as you feel **lead** by God" | "as you feel **led** by God" | Intro text - past participle needed |

### FAQ Page (`/faq/`)
| Severity | Error | Correction | Context |
|----------|-------|------------|---------|
| P0 | "Your Subtitle Goes Here" (x9) | Remove or replace | Accordion subtitle placeholder |
| P2 | "bread and juice for each person **you** to take" | "for each person **to take**" | "How do we take communion?" section |

### Employment Page (`/employment/`)
| Severity | Error | Correction | Context |
|----------|-------|------------|---------|
| P0 | "Your Subtitle Goes Here" (x3) | Remove or replace | Job listing accordion placeholder |
| P2 | "**on boarding**" | "**onboarding**" | Family Ministries Volunteer Associate |
| P2 | "Connect with **currents** volunteers" | "Connect with **current** volunteers" | Volunteer Communication section |
| P2 | "volunteer **celebration** throughout the year" | "volunteer **celebrations** throughout the year" | Special Events section |

### Privacy Policy (`/privacy-policy/`)
| Severity | Error | Correction | Context |
|----------|-------|------------|---------|
| P2 | "we have **placed** appropriate...procedures" | "we have **put in place** appropriate...procedures" | Data Security section |
| P2 | "types of information that **is** collected" | "types of information that **are** collected" | Website section - subject-verb agreement |
| P2 | "with **regards** to" | "with **regard** to" | Website section |
| P2 | "ad networks **uses** technologies" | "ad networks **use** technologies" | Advertising Partners section |
| P2 | "sent directly to users' **browser**" | "sent directly to users' **browsers**" | Advertising Partners section |
| P2 | "we will **do our best efforts**" | "we will **make our best efforts**" or "**do our best**" | Children's Information section |

### Photo Release (`/photo-release/`)
| Severity | Error | Correction | Context |
|----------|-------|------------|---------|
| P2 | "video **and/or or** sound recordings" | "video **and/or** sound recordings" | Duplicated "or" |
| P3 | "**web casts**" / "**web casting**" (x3) | "**webcasts**" / "**webcasting**" | Should be one word |

### Creative Communications (`/creative-communications/`)
| Severity | Error | Correction | Context |
|----------|-------|------------|---------|
| P2 | "aptitudes and **interest**" | "aptitudes and **interests**" | Communications Team section |

### Pastoral Care (`/pastoral-care/`)
| Severity | Error | Correction | Context |
|----------|-------|------------|---------|
| P1 | "church **oranother** location" | "church **or another** location" | Funerals section - missing space |
| P1 | "Have you **every** been water baptized?" | "Have you **ever** been water baptized?" | Life Help intake form |

### Prayer (`/prayer/`)
| Severity | Error | Correction | Context |
|----------|-------|------------|---------|
| P2 | "**Employers** name" | "**Employer's** name" | Deliverance Intake Form - missing apostrophe |
| P2 | "Set aside time over your **lunch hour**...every Tuesday from **6-8pm**" | Misleading - 6-8pm is evening, not lunch hour | Prayer Room section - only Friday 12-1pm is lunch hour |

### Young Adults (`/youngadults/`)
| Severity | Error | Correction | Context |
|----------|-------|------------|---------|
| P1 | "opportunities with **women's ministry**" | "opportunities with **20s & 30s ministry**" | Email signup - copy-paste error |
| P3 | "to **hangout** and make new friends" | "to **hang out** and make new friends" | Verb should be two words |

### 55+ Adults (`/55-adults/`)
| Severity | Error | Correction | Context |
|----------|-------|------------|---------|
| P1 | "opportunities with **women's ministry**" | Reference 55+ ministry | Email signup - copy-paste error |

### Women's Page (`/women/`)
| Severity | Error | Correction | Context |
|----------|-------|------------|---------|
| P2 | "**Woman's** Group" (page title) | "**Women's** Group" | Browser tab title - singular vs plural |

### Small Groups (`/small-groups/`)
| Severity | Error | Correction | Context |
|----------|-------|------------|---------|
| P3 | "Small Christian Group" (HTML title) | "Small Groups" | Browser tab title inconsistent with page heading |

### Global Missions (`/global-missions/`)
| Severity | Error | Correction | Context |
|----------|-------|------------|---------|
| P1 | "described in **book** of Acts" | "described in **the book** of Acts" | Parana/Brazil section - missing "the" |
| P1 | "make **in** difference in the lives" | "make **a** difference in the lives" | Jericho/Israel section |
| P2 | "public health **decision**" | "public health **decisions**" | Bienvenida Suero bio |
| P2 | "This missionary is trained....**I'm** currently" | POV switch from 3rd to 1st person | Sara, West Eurasia bio |
| P2 | "the local Japanese **Christian**. To encourage" | "**Christians**" (plural) + fix sentence fragment | Alissa Bauer bio |

### Local Missions (`/localmissions/`)
| Severity | Error | Correction | Context |
|----------|-------|------------|---------|
| P2 | "organization that **focus** on" | "organization that **focuses** on" | Parachurch Organizations - subject-verb agreement |
| P3 | "**Lifewise** Academy" vs "**LifeWise**" in heading | Standardize to **LifeWise** | Inconsistent capitalization |

### Church Planting (`/churchplanting/`)
| Severity | Error | Correction | Context |
|----------|-------|------------|---------|
| P1 | "explaining **for** vision and passion" | "explaining **your** vision and passion" | Church Planter application form |

### Fasting (`/fasting/`)
| Severity | Error | Correction | Context |
|----------|-------|------------|---------|
| P0 | **"Your Subtitle Goes Here" (x4)** | Remove or replace | Placeholder under all 4 accordion headings |

### Global Partners (`/missions/global-partners/`)
| Severity | Error | Correction | Context |
|----------|-------|------------|---------|
| P0 | **India North section has Brazil North content** | Replace with correct India North description | Copy-paste error - references "Igreja Presbyteriana de Manaus" and "Amazon River" under India |
| P2 | Brazil South description is redundant | Rewrite second sentence | Second sentence restates the first nearly verbatim |
| P2 | Dominican Republic, Zambia, Vietnam have no descriptions | Add partner descriptions | Sections exist but have no text content |

### Zambia Photos (`/missions/zambia-photos/`)
| Severity | Error | Correction | Context |
|----------|-------|------------|---------|
| P2 | "**Africa** Church Planting Initiative" | "**African** Church Planting Initiative" | H1 heading - Videos page correctly uses "African" |

### Vietnam Videos & Photos (`/missions/vietnam-videos/`, `/missions/vietnam-photos/`)
| Severity | Error | Correction | Context |
|----------|-------|------------|---------|
| P0 | **"Ministry Partner Name, Vietnam"** | Replace with actual partner name | Placeholder heading on both pages |

### Global Church Planting (`/global-church-planting/`)
| Severity | Error | Correction | Context |
|----------|-------|------------|---------|
| P1 | "for such **as** time as this" | "for such **a** time as this" | Immanuel Church section (Esther 4:14 reference) |

### Bethlehem Partner Page (`/missions/bethlehem-partner-page/`)
| Severity | Error | Correction | Context |
|----------|-------|------------|---------|
| P1 | "for such **as** time as this" | "for such **a** time as this" | Same Esther 4:14 error as above |

### Vietnam Partner Page (`/missions/vietnam-partner-page/`)
| Severity | Error | Correction | Context |
|----------|-------|------------|---------|
| P2 | "Meet our partners in **the** Vietnam" | "Meet our partners in Vietnam" | Page heading - remove "the" |
| P2 | "**Northwood's** mission teams" | "**Northwoods'** mission teams" | Church name is "Northwoods" not "Northwood" |

### Brazil North Stories (`/missions/brazil-north-stories/`)
| Severity | Error | Correction | Context |
|----------|-------|------------|---------|
| P2 | "in pain **specially** explaining" | "in pain **especially** explaining" | Story text |

### India North Partner Page (`/missions/india-north-partner-page/`)
| Severity | Error | Correction | Context |
|----------|-------|------------|---------|
| P3 | "**seven acre** compound" | "**seven-acre** compound" | Hope Partners description - compound adjective needs hyphen |

### India South Partner Page (`/missions/india-south-partner-page/`)
| Severity | Error | Correction | Context |
|----------|-------|------------|---------|
| P1 | "having **training** thousands of Pastors" | "having **trained** thousands of Pastors" | Syam description - wrong verb form |
| P1 | Heading says "**Zion Evangelical Ministries**" but body says "**Zion Evangelistic and Care Ministries (ZEC)**" | Verify official name and make consistent | Organization name mismatch |

### MSP Page (`/msp/`)
| Severity | Error | Correction | Context |
|----------|-------|------------|---------|
| P2 | "are one-time **experience** observing" | "are one-time **experiences** observing" | Plural needed |
| P1 | "vocational ministry **of** simply desire" | "vocational ministry **or** simply desire" | Wrong word |

### OCC Page (`/occ/`)
| Severity | Error | Correction | Context |
|----------|-------|------------|---------|
| P0 | Craig Smith phone: "**302**-243-2740" | Likely "**309**-243-2740" | All other staff use 309 area code (Peoria, IL) |

### Milestone Moments (`/milestone-moments/`)
| Severity | Error | Correction | Context |
|----------|-------|------------|---------|
| P3 | "Life Help **ministries** office" | "Life Help **Ministries** office" | Inconsistent capitalization |

### Event Details (`/event-details/`)
| Severity | Error | Correction | Context |
|----------|-------|------------|---------|
| P1 | CSS class typo: `.event-**desription**` | `.event-**description**` | Inline `<style>` block - missing "c" causes `min-width: 300px` rule to not apply to event descriptions |

### Volunteer (`/volunteer/`)
| Severity | Error | Correction | Context |
|----------|-------|------------|---------|
| P1 | **Broken URL:** SERVE button links to `/localmissions/%20` | Remove trailing `%20` (encoded space) | "In The Community" section - will likely 404 |
| P3 | "The **four steps** class" | "The **Four Steps** class" | Body text - inconsistent with heading capitalization |

### Ministries (`/ministries/`)
| Severity | Error | Correction | Context |
|----------|-------|------------|---------|
| P2 | "in the communities **around**" | "in the communities **around us**" or "in the **surrounding** communities" | Local Missions section - incomplete phrase |

### Online Courses (`/online-courses/`)
| Severity | Error | Correction | Context |
|----------|-------|------------|---------|
| P3 | "Please **login**" | "Please **log in**" | Verb form should be two words |

### Discoveryland (`/discoveryland/`)
| Severity | Error | Correction | Context |
|----------|-------|------------|---------|
| P2 | "their relationship with **the** Him" | "their relationship with Him" | God's Love section - erroneous article |
| P3 | Missing period at end of sentence | Add period after "releasing your child to you" | Check-in section |

### Quest (`/quest/`)
| Severity | Error | Correction | Context |
|----------|-------|------------|---------|
| P1 | "encounter Jesus **though** worship" | "encounter Jesus **through** worship" | Engaging Worship section - missing "r" |

### Purity Groups (`/purity-groups/`)
| Severity | Error | Correction | Context |
|----------|-------|------------|---------|
| P1 | "for **girl** who are becoming young **woman**" | "for **girls** who are becoming young **women**" | Behind the Mask - plural errors |
| P1 | "**they** behind masks" | "they **hide** behind masks" | Missing verb |
| P3 | "anxiety; anger**:** alcohol" | "anxiety; anger**;** alcohol" | Colon should be semicolon for consistency |

### Now Is The Time (`/now-is-the-time/`)
| Severity | Error | Correction | Context |
|----------|-------|------------|---------|
| P0 | "$8,000,**00**" | "$8,000,**000**" | Celebration Goal - missing zero |
| P0 | "$15,000,**00**" | "$15,000,**000**" | Dream Goal - missing zero |

### Yes Page (`/yes/`)
| Severity | Error | Correction | Context |
|----------|-------|------------|---------|
| P1 | "you have **to** a new authority" | "you have **a** new authority" or "you have **submitted to** a new authority" | Baptism description - grammatically broken |

### Book of Prayers - Index (`/book-of-prayers/`)
| Severity | Error | Correction | Context |
|----------|-------|------------|---------|
| P2 | "cleanse it **dedicate** it" | "cleanse it **and dedicate** it" | Missing "and" |

### Book of Prayers - Breaking Generational Curses
| Severity | Error | Correction | Context |
|----------|-------|------------|---------|
| P2 | "repent **for of** any and all sins" | "repent **for** any and all sins" | Double preposition |

### Book of Prayers - Spiritual Warfare (`/book-of-prayers/spiritual-warfare/`)
| Severity | Error | Correction | Context |
|----------|-------|------------|---------|
| P2 | "**construct-ed**" | "**constructed**" | Hyphenation artifact left in text |
| P2 | "**subordi-nate**" | "**subordinate**" | Hyphenation artifact left in text |

### Book of Prayers - Declarations of Identity (`/book-of-prayers/declarations-of-identity-in-christ/`)
| Severity | Error | Correction | Context |
|----------|-------|------------|---------|
| P2 | "**Hebrew** 7:25" | "**Hebrews** 7:25" | Bible book name missing plural |

### Book of Prayers - Covering and Victory (`/book-of-prayers/covering-and-victory/`)
| Severity | Error | Correction | Context |
|----------|-------|------------|---------|
| P2 | "In **Jesus** name!" (x2) | "In **Jesus'** name!" | Missing possessive apostrophe |

### Book of Prayers - Warfare
| Severity | Error | Correction | Context |
|----------|-------|------------|---------|
| P2 | "as **you** the Holy Spirit leads you" | "as the Holy Spirit leads you" | Extra word "you" |
| P3 | "**self discipline**" | "**self-discipline**" | Missing hyphen |

### Book of Prayers - Cleansing & Dedicating Property
| Severity | Error | Correction | Context |
|----------|-------|------------|---------|
| P2 | "cleanse it **dedicate** it" | "cleanse it **and dedicate** it" | Missing "and" |
| P2 | "worship **through** the property" | "worship **throughout** the property" | Wrong preposition |
| P1 | "I now proclaim that **his** home" | "I now proclaim that **this** home" | Typo changes meaning |

### Kiosk Pages
| Severity | Error | Correction | Context |
|----------|-------|------------|---------|
| P3 | "Join **A** Group" | "Join **a** Group" | Inconsistent capitalization with "Host a Group" and "Take a Class" |
| P3 | "**20's & 30's**" vs "**20s & 30s**" | Standardize to "20s & 30s" | Breadcrumb vs heading inconsistency |
| P3 | "**hangups**" | "**hang-ups**" | Get Free calendar tagline |

---

## Placeholder Content

The following pages contain placeholder/template content that needs to be replaced before launch:

### Event Post Templates (9 pages)
All contain identical Lorem Ipsum content:
- `/events/title-here/`
- `/events/title-here-2/` through `/events/title-here-9/`

**Content issues:** "Title Here" headings, "Month X, 2025" dates, Lorem Ipsum body text, "by Juxt Marketing" author attribution.

**Action needed:** Either populate with real event content or remove/unpublish these pages before launch.

### Sermon Series Templates (6 pages)
- `/series/sermon-title-here/`
- `/series/sermon-title-here-2/` through `/series/sermon-title-here-6/`

**Action needed:** Populate with real sermon series content or remove before launch.

### Featured Event Templates (2 pages)
- `/featured-events/title-here-10/`
- `/featured-events/title-here-11/`

**Action needed:** Populate or remove before launch.

### Valentine's Date Night (`/featured-events/valentines-date-night/`)
| Severity | Error | Correction | Context |
|----------|-------|------------|---------|
| P0 | URL/content mismatch: URL says "valentines-date-night" but content is "Receiving the Fullness of the Holy Spirit" | Fix URL or content | Wrong content assigned to this URL |
| P1 | "**:30 PM** - 9:00 PM" | "**5:30 PM** - 9:00 PM" | Event time missing hour digit |

### URL/Content Mismatches
- `/featured-events/valentines-date-night/` - URL says "Valentine's Date Night" but page content is "Receiving the Fullness of the Holy Spirit"
- `/series/sermon-title-here/` - URL is placeholder but contains "Spiritual Warfare" prayer content
- `/series/sermon-title-here-2/` - URL is placeholder but contains "Declarations of Identity in Christ"
- `/series/sermon-title-here-3/` - URL is placeholder but contains "Prayer for Daily Covering and Victory"

### Story Placeholders
- `/missions/vietnam-stories/` - Contains only "Story coming soon"

---

## Third-Party Widgets & Integrations Audit

### Global Integrations (Present on ALL Pages)

These scripts and services are loaded site-wide:

| Integration | Script/Source Domain | Purpose |
|-------------|---------------------|---------|
| **Ministry Platform Widgets** | `my.northwoods.church/widgets/dist/MPWidgets.js` | Custom web components (`<mpp-user-login>`, `<mpp-group-finder>`) |
| **BlackPulp Widgets v1** | `widgets.blackpulp.com/resources/northwoods/loader.js` | `bpPortal` framework for staff directories, featured events |
| **BlackPulp Widgets v3** | `widgets3.blackpulp.com/js/northwoods/widgets3.js` | `widgets3.eventFinderW3()` event search widget |
| **Ministry Platform SSO** | `northwoods.onlinegiving.org/assets/mpsso.js` | SSO between website and online giving portal |
| **BugHerd** | `www.bugherd.com/sidebarv2.js?apikey=e80shryijifxwxc5azhxbq` | **DEV TOOL - REMOVE BEFORE LAUNCH** QA bug tracking sidebar |
| **Juxt Book of Prayers Plugin** | First-party WP plugin | Prayer request functionality |
| **Site Kit by Google** | v1.173.0 | Analytics, Search Console integration |
| **Yoast SEO** | WP plugin | SEO metadata and structured data |
| **Divi Theme** | v4.27.5 by Elegant Themes | Page builder / theme framework |
| **Divi Plugins** | Various | Divi Switch (WP Zone), Divi Area/Popups v3.2.4, Chi Divi Accordions v2.1.2, Gravity Forms Divi Module Premium v8.5.0 |

### Page-by-Page Widget Matrix

| Page | Gravity Forms | reCAPTCHA | MPP Login | MPP Group Finder | bpPortal Staff Dir | bpPortal Featured Events | widgets3 Event Finder | Sermon Widget | Giving Links | Video |
|------|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| `/give/` | #19 | Yes | Yes | -- | -- | -- | -- | -- | Yes | -- |
| `/events/` | -- | -- | -- | -- | -- | -- | Yes | -- | -- | -- |
| `/groups/` | -- | -- | -- | Yes | -- | -- | -- | -- | -- | -- |
| `/sermons/` | -- | -- | -- | -- | -- | -- | -- | Yes | -- | -- |
| `/prayer/` | #38 (12-page) | Yes | -- | -- | -- | Yes | -- | -- | -- | -- |
| `/staff/` | -- | -- | -- | -- | Yes (7+) | -- | -- | -- | -- | -- |
| `/volunteer/` | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- |
| `/newhere/` | -- | -- | -- | -- | -- | -- | -- | -- | -- | MP4 |
| `/watch/` | -- | -- | -- | -- | -- | -- | -- | Yes | -- | -- |

### Widget Configuration Details

**Gravity Forms:**
- **Form #19** (`/give/`): Simple contact form - Name, Message, reCAPTCHA
- **Form #38** (`/prayer/`): 12-page multi-step counseling intake form with conditional logic and save-and-continue. Fields include personal info, address, emergency contacts (x3), spiritual information, prayer concerns, urgency level

**bpPortal Staff Directory** (`/staff/`):
Uses `flat-group-collections` service with 7+ container sections:
`#StaffSeniorPastor`, `#StaffExecutives`, `#StaffExecAdmins`, `#StaffAdults`, `#StaffMissions`, `#StaffStudents`, `#StaffcreativeExperiences`

**BlackPulp Event Finder** (`/events/`):
```javascript
widgets3.eventFinderW3().then(unifinder => {
    unifinder.init('#widget', {
        coreType: 'events',
        itemDetailURL: '/event-details/',
        displayEventDate: true,
        displayEventTime: true,
        displayEventLocation: true,
        futureEventsOnly: true,
    });
});
```

**bpPortal Featured Events** (`/prayer/`):
```javascript
bpPortal.service.load('featured-events2');
// programId: [170, 366]
```

**BlackPulp Sermon Widget** (`/sermons/`, `/watch/`):
```javascript
// Script: sermons.northwoods.apps.blackpulp.com/app/sermonwidget.js
sermonwidget.sermons().then(function(sermons) {
    sermons.init('#sermons', { /* config */ });
});
```

**MPP Group Finder** (`/groups/`):
```html
<mpp-group-finder targeturl="/group-details/"></mpp-group-finder>
```

**Inline JS Featured Events Widget** (multiple ministry pages):
Appears on `/converge/`, `/supportgroups/`, `/getfree/`, `/foursteps/`, `/baptism/`, `/finances/`, `/leadership/` (4 instances), `/55-adults/`. Uses MutationObserver to replace default "no events" message. **Contains the "thsi" typo bug.**

### External Domains Referenced

| Domain | Service | Scope |
|--------|---------|-------|
| `my.northwoods.church` | Ministry Platform Widgets | Global |
| `widgets.blackpulp.com` | BlackPulp v1 Loader | Global |
| `widgets3.blackpulp.com` | BlackPulp v3 Widgets | Global + `/events/` |
| `sermons.northwoods.apps.blackpulp.com` | Sermon Widget | `/sermons/`, `/watch/` |
| `northwoods.onlinegiving.org` | Online Giving / SSO | Global + `/give/` |
| `www.google.com` | reCAPTCHA v2 | `/give/`, `/prayer/` |
| `www.bugherd.com` | BugHerd QA | Global (**remove for launch**) |
| `linktr.ee` | Northwoods Worship | External nav link |

### Key Widget Findings

1. **No iframes detected** on any pages audited - all widgets use JavaScript injection and custom web components
2. **No YouTube/Vimeo/Subsplash embeds** found - video is self-hosted MP4 or via BlackPulp sermon widget
3. **Ministry Platform** is the core ChMS powering authentication, groups, and giving
4. **BlackPulp** provides three service layers: v1 loader (staff/events), v3 framework (event finder), and dedicated sermon app
5. **BugHerd is loaded globally with a visible API key** - must be removed before production launch

---

## Site Structure & Page Hierarchy

*Based on sitemap analysis of northwoods.juxt.studio*

### Platform
- **CMS:** WordPress with Divi Theme (Elegant Themes)
- **Staging URL:** northwoods.juxt.studio
- **Third-party integrations identified:** Brushfire/bpPortal (events), Subsplash (app), likely Ministry Platform or similar ChMS

### Primary Navigation Menu (from HTML source)

*Extracted from `<ul id="menu-primary-menu">` in the page header*

```
1. ABOUT (/about/)
   +-- Leadership (/leadership/)
   +-- Staff (/staff/)
   +-- Employment Opportunities (/employment/)
   +-- Milestone Moments (/milestone-moments/)
   +-- Northwoods Worship (https://linktr.ee/northwoodsworship) [EXTERNAL]
   +-- Alerts & Subscriptions (/alerts/)
   +-- Translations (/translation/)

2. NEW HERE (/newhere/)
   (no sub-items)

3. MINISTRIES & CLASSES (/ministries/) ★ Largest menu section
   +-- Core Classes (/ministries/#core-classes)
   |   +-- Four Steps (/foursteps/)
   |   +-- Alpha (/alpha/)
   |   +-- Get Free (/getfree/)
   |   +-- Doing What Jesus Did (/dwjd/)
   |   +-- More Classes (/classes/)
   |
   +-- Children & Students (/ministries/#children)
   |   +-- Discoveryland (/discoveryland/)
   |   +-- Quest (/quest/)
   |   +-- Converge (/converge/)
   |   +-- Parenting & Families (/family)
   |
   +-- Freedom & Prayer (/ministries/#freedom)
   |   +-- Get Free (/getfree/) [DUPLICATE - also under Core Classes]
   |   +-- Prayer (/prayer/)
   |   +-- Prayer Resources (/prayer-resources/)
   |   +-- Bible Reading Resources (/bible/)
   |   +-- Fasting Resources (/fasting/)
   |
   +-- Adult Groups (/ministries/#adult)
   |   +-- Small Groups (/small-groups/)
   |   +-- Men's Groups (/men/)
   |   +-- Women's Groups (/women/)
   |   +-- 20s & 30s (/youngadults/)
   |   +-- 55+ Connection (/55-adults)
   |
   +-- Life Help (/ministries/#life-help)
   |   +-- Support Groups (/supportgroups/)
   |   +-- Pastoral Care & Assistance (/pastoral-care/)
   |   +-- Marriage (/marriage/)
   |   +-- Baptism (/baptism/)
   |
   +-- Church Planting & Missions (/ministries/#making)
   |   +-- Domestic Church Planting (/churchplanting/)
   |   +-- Global Church Planting (/global-church-planting/)
   |   +-- Local Missions (/localmissions/)
   |   +-- Global Missions (/global-missions/)
   |
   +-- Finances (/finances/)
   +-- Volunteer (/volunteer/)
   +-- FAQ (/faq/)

4. EVENTS (/events/)
   (no sub-items)

5. CHURCH PLANTING (# - dropdown trigger only)
   +-- Domestic (/churchplanting/) [DUPLICATE - also under Ministries]
   +-- Global (/global-church-planting/) [DUPLICATE - also under Ministries]

6. WATCH (# - dropdown trigger only)
   +-- Watch Online (https://northwoods.online/) [EXTERNAL]
   +-- Message Archive (/watch/#/)
   +-- Streaming (/mobile/)

7. GIVE (# - dropdown trigger only)
   +-- Ways To Give (/give/)
   +-- Give Online (https://northwoods.onlinegiving.org/...) [EXTERNAL]
```

### Login Widget (separate from nav - `<mpp-user-login>` component)
```
   My Pledges (/widgets/my-pledges/)
   Contribution Statements (/widgets/contribution-statements/)
   My Giving (/widgets/my-giving/)
```

### Navigation Notes for Developers
- **3 nesting levels max** - deepest items are 3rd-level under Ministries & Classes
- **"Church Planting" appears twice** - as standalone top-level (#5) AND under Ministries & Classes (#3)
- **"Get Free" appears twice** - under both Core Classes and Freedom & Prayer
- **Top-level dropdown triggers** - "Watch", "Give", "Church Planting" have `href="#"` (not clickable links)
- **"New Here" and "Events" are standalone** - no sub-menus

### Pages NOT in Navigation (accessible only via direct link or in-page links)

```
Content Pages:
  /privacy-policy/          /photo-release/           /creative-communications/
  /counseling-referrals/    /news/                    /blogs/
  /weddings/                /puredesire/              /purity-groups/
  /msp/                     /occ/                     /online-courses/
  /now-is-the-time/         /yes/                     /book-of-prayers/ (+ all prayer sub-pages)
  /global-missions/         /missions/global-partners/
  /connect-with-church-planting/
  /localmissions-interest-form/

Mission Partner Pages (all under /missions/):
  /missions/brazil-north-partner-page/    + /videos/, /photos/, /stories/
  /missions/brazil-south-partner-page/    + /videos/, /photos/
  /missions/dominican-republic-partner-page/ + /dr-videos/, /dr-photos/, /dr-stories/
  /missions/india-north-partner-page/     + /photos/
  /missions/india-south-partner-page/     + /videos/, /photos/, /boat-story/
  /missions/kfar-saba-partner-page/
  /missions/jericho-partner-page/         + /videos/
  /missions/bethlehem-partner-page/
  /missions/zambia-partner-page/          + /videos/, /photos/
  /missions/vietnam-partner-page/         + /videos/, /photos/, /stories/

Kiosk / Interactive Pages:
  /smallgroupkiosk/         + /host-a-group/, /in-home-group/
  /smallgroupkiosk/smallgroupkiosk/ (+ all calendar sub-pages)

Widget / Embed Pages:
  /widgets/event-detail/    /widgets/opportunity-detail/   /widgets/opportunity-finder/
  /widgets/small-groups-finder/  /widgets/prayer-form/     /widgets/group-finder/
  /widgets/my-pledges/      /widgets/contribution-statements/  /widgets/my-giving/
  /widgets/custom-form/

Watch Streams:
  /watch-1/ through /watch-4/

Functional Pages:
  /signup-slots/  /invoices/  /group-details/  /giving-history/  /scratch/  /staff-widget/

Translation Pages:
  /spanish/  /portuguese/  /telugu/  /arabic/  /hindi/  /chinese/  /vietnamese/
```

### Widget/Embed Pages (Internal use / iframe targets)
These pages appear to serve as widget containers, likely embedded via iframes on other pages:

```
/widgets/
+-- event-detail/        - Single event detail display
+-- opportunity-detail/  - Single volunteer opportunity display
+-- opportunity-finder/  - Volunteer opportunity search
+-- small-groups-finder/ - Small group search/filter
+-- prayer-form/         - Prayer request submission form
+-- group-finder/        - General group search
+-- my-pledges/          - User pledge dashboard (authenticated)
+-- contribution-statements/ - Giving statements (authenticated)
+-- my-giving/           - Giving dashboard (authenticated)
+-- custom-form/         - Generic form container
```

### Key Third-Party Integrations Identified
Based on JavaScript and embed patterns observed across pages:

| Integration | Purpose | Pages Observed On |
|-------------|---------|-------------------|
| **Brushfire / bpPortal** | Event calendar, featured events, event registration | Most ministry pages, kiosk pages, events pages |
| **Subsplash** | Mobile app, potentially giving | `/mobile/`, `/give/` |
| **Divi Builder** (Elegant Themes) | Page builder / theme | All pages |
| **WordPress** | CMS platform | All pages |
| **YouTube** | Video embeds | Mission partner video pages |
| **Vimeo** (likely) | Sermon/worship video embeds | `/watch/` pages |
| **Inline JS Event Widget** | Featured events with fallback messaging | 6+ ministry/class pages |

### Featured Events Widget (Inline JavaScript)
The following pages include an inline `<script>` block that loads featured events from bpPortal and provides a fallback message when no events are found. This is the script containing the "thsi" typo:

**Pages with this widget:**
- `/converge/`
- `/supportgroups/`
- `/getfree/`
- `/foursteps/`
- `/baptism/`
- `/finances/`
- `/leadership/` (4 instances)
- `/55-adults/`

---

## Pre-Launch Checklist

Beyond spelling and content corrections, the following items should be verified before going live on Monday.

### Critical - Must Do Before Launch

- [ ] **Remove BugHerd** - The BugHerd QA sidebar (`sidebarv2.js?apikey=e80shryijifxwxc5azhxbq`) is loaded on every page. This is a development tool and must be removed for production.
- [ ] **DNS & Domain Migration** - Confirm DNS records are ready to switch from `northwoods.juxt.studio` to the production domain. Lower TTL values in advance.
- [ ] **SSL Certificate** - Verify the production domain has a valid SSL certificate installed and auto-renews.
- [ ] **Staging URL References** - Search the entire database and theme for any remaining `northwoods.juxt.studio` or `juxt.studio` references. Check hardcoded URLs in Divi modules, custom CSS, JavaScript, and the `<mpp-user-login customcss>` attribute.
- [ ] **Remove/Unpublish Placeholder Content** - 9 "Title Here" event posts, 6 "Sermon Title Here" series posts, 2 "Title Here" featured event posts.
- [ ] **Fix All P0 Errors** - Dollar amounts, phone number, placeholder text, sitewide JS "thsi" bug.

### SEO & Search

- [ ] **Robots.txt** - Ensure `robots.txt` allows search engine crawling (staging sites often block with `Disallow: /`)
- [ ] **XML Sitemaps** - Verify sitemaps are valid and submit to Google Search Console
- [ ] **Yoast SEO Meta** - Spot-check key pages have proper meta titles/descriptions
- [ ] **Open Graph / Social Sharing** - Test sharing homepage, give, and events on Facebook/Twitter
- [ ] **Canonical URLs** - Verify canonical tags point to production domain, not staging
- [ ] **Google Analytics / Site Kit** - Confirm GA4 property is connected for production
- [ ] **Google Search Console** - Add and verify the production domain

### Redirects & Links

- [ ] **301 Redirects** - If migrating from an existing site, ensure all old URLs redirect properly
- [ ] **Internal Broken Links** - Run a link checker (the `/localmissions/%20` broken URL on `/volunteer/` is already documented)
- [ ] **External Links** - Verify: `linktr.ee/northwoodsworship`, `northwoods.onlinegiving.org`, `northwoods.online/`
- [ ] **404 Page** - Verify a custom 404 page exists and is styled consistently

### Forms & Interactive Features

- [ ] **Gravity Form #19** (`/give/`) - Submit test entry, verify email notification received
- [ ] **Gravity Form #38** (`/prayer/`) - Test all 12 pages of intake form, including save-and-continue
- [ ] **reCAPTCHA Keys** - Verify reCAPTCHA keys are registered for production domain (staging keys won't work)
- [ ] **MPP User Login** (`<mpp-user-login>`) - Test login/logout flow on production domain
- [ ] **MPP Group Finder** (`/groups/`) - Verify group search returns results
- [ ] **Online Giving Links** - Test all `/give/` CTA buttons reach the correct giving portal
- [ ] **Prayer Request Form** - Test the Juxt Book of Prayers plugin submission

### Third-Party Integrations

- [ ] **BlackPulp Event Finder** (`/events/`) - Verify events load and link to detail pages
- [ ] **BlackPulp Sermon Widget** (`/sermons/`, `/watch/`) - Verify sermons load and play
- [ ] **bpPortal Staff Directory** (`/staff/`) - Verify all 7+ staff sections load with photos/bios
- [ ] **bpPortal Featured Events** (`/prayer/` and ministry pages) - Verify events display
- [ ] **Ministry Platform SSO** - Verify `mpsso.js` works with production domain
- [ ] **Subsplash / Mobile App Links** (`/mobile/`) - Verify app store links are correct

### Performance & Mobile

- [ ] **Mobile Responsiveness** - Test homepage, events, give on phone + tablet
- [ ] **Page Load Speed** - Run PageSpeed Insights (aim for 90+ desktop, 70+ mobile)
- [ ] **Image Optimization** - Compress large hero/banner images and mission partner photos
- [ ] **Self-hosted Video** (`/newhere/`) - Verify the welcome MP4 video loads and plays on mobile

### Security & Access

- [ ] **WordPress Admin** - Change staging admin passwords, review user accounts
- [ ] **Remove Dev Plugins** - BugHerd, any debug/log plugins
- [ ] **File Permissions** - Verify `wp-config.php` is not publicly accessible
- [ ] **API Keys** - Verify all API keys are production keys (BugHerd key is visible in source)

### Content & Branding

- [ ] **Favicon** - Verify favicon displays in browser tabs
- [ ] **Browser Tab Titles** - Fix known issues: "Woman's Group" → "Women's Group", "Small Christian Group" → "Small Groups"
- [ ] **Copyright Year** - Verify footer shows 2026
- [ ] **Contact Info** - Verify all phone numbers and addresses across the site
- [ ] **Social Media Links** - Verify footer/header social icons link to correct profiles

### Post-Launch Monitoring

- [ ] **Uptime Monitoring** - Set up uptime monitoring for production
- [ ] **Error Logs** - Check WordPress error logs after launch
- [ ] **Form Notifications** - Monitor that form emails are received
- [ ] **Search Console** - Watch for crawl errors in the first week
- [ ] **Caching** - Configure page caching plugin
- [ ] **Backup Strategy** - Ensure automated backups are running

---

## Pages Not Yet Checked

The following pages could not be spell-checked due to API rate limits during the audit. These should be reviewed in a follow-up pass:

### Main Content Pages
- `/staff/` (dynamic content loads via JS - bios loaded from external service)


### Other Pages
- `/arabic/`, `/hindi/` (language pages - not yet checked)
- `/invoices/`, `/group-details/` (functional pages)
- All `/widgets/` sub-pages (widget embed targets - functional, minimal text)

### Widget/Integration Pages -- COMPLETED

See the new **Widget Page Third-Party Integration Inventory** section below for full documentation of all `/widgets/` pages.

---

## Widget Page Third-Party Integration Inventory

All `/widgets/` pages share a common set of third-party scripts loaded sitewide. Each page then uses specific custom HTML elements (web components) to render its primary widget. The widgets are powered by two main third-party platforms: **Ministry Platform (MPP)** via `my.northwoods.church` and **BlackPulp (bpPortal)** via `widgets.blackpulp.com`.

### Sitewide Third-Party Scripts (loaded on ALL widget pages)

| Script | Source Domain | Purpose |
|--------|---------------|---------|
| `MPWidgets.js` | `https://my.northwoods.church/widgets/dist/MPWidgets.js` | **Ministry Platform Widget Library** -- Defines all `<mpp-*>` custom HTML elements (web components) for groups, forms, giving, opportunities, event details, user authentication, etc. Hosted on the church's Ministry Platform (Bonterra/MP) instance running on IIS/ASP.NET. |
| `loader.js` | `https://widgets.blackpulp.com/resources/northwoods/loader.js` | **BlackPulp bpPortal Widget Loader** -- Core framework for the BlackPulp church engagement platform. Handles authentication, API communication, React-based rendering, and service registration. Reads query parameters to render event details dynamically. |
| `widgets3.js` | `https://widgets3.blackpulp.com/js/northwoods/widgets3.js` | **BlackPulp Widgets v3** -- Webpack-bundled widget modules including event finder, event lists, group finder, and giving components. Loads additional chunk files on demand. |
| `mpsso.js` | `https://northwoods.onlinegiving.org/assets/mpsso.js` | **Ministry Platform SSO for Online Giving** -- Single sign-on bridge between Ministry Platform authentication and the online giving portal at `northwoods.onlinegiving.org`. |
| `mp-widget-customizer` CSS | `northwoods.juxt.studio/wp-content/plugins/mp-widget-customizer/assets/styles.css` | **MP Widget Customizer Plugin** -- WordPress plugin providing custom CSS overrides for Ministry Platform widgets. |
| `sidebarv2.js` | `https://www.bugherd.com/sidebarv2.js?apikey=e80shryijifxwxc5azhxbq` | **BugHerd** -- Visual bug tracking/feedback tool (staging/dev tool, must be removed before production launch). |

### Per-Page Widget Details

#### 1. `/widgets/event-detail/` -- Event Detail Display

| Attribute | Value |
|-----------|-------|
| **Primary Widget** | BlackPulp bpPortal Event Detail (rendered dynamically by `loader.js` and `widgets3.js`) |
| **Custom Element** | None in static HTML -- content is injected at runtime by BlackPulp scripts based on URL query parameters (e.g., `?id=...`) |
| **Script Source** | `https://widgets.blackpulp.com/resources/northwoods/loader.js` + `https://widgets3.blackpulp.com/js/northwoods/widgets3.js` |
| **Purpose** | Displays a single event's details (title, date, description, registration button) when linked from event listings elsewhere on the site |
| **Custom CSS** | `.event-meta:after { background: #004c97 }` and `button.bp-widgets3-button` styled with Northwoods navy blue branding |
| **Authentication** | `<mpp-user-login>` in header for optional authenticated user context |
| **Notes** | The page's main content area (`#main-content`) contains an empty Divi text module -- all content is rendered client-side by BlackPulp JavaScript. The CSS class `.event-desription` (missing "c") noted in the main audit is related to this widget's styling. |

#### 2. `/widgets/opportunity-finder/` -- Volunteer Opportunity Search

| Attribute | Value |
|-----------|-------|
| **Primary Widget** | Ministry Platform Opportunity Finder |
| **Custom Element** | `<mpp-opportunity-finder>` |
| **Element Attributes** | `targeturl="/widgets/opportunity-detail/"` `customcss="https://northwoods.juxt.studio/wp-content/uploads/nw-widget-css.css"` |
| **Script Source** | `https://my.northwoods.church/widgets/dist/MPWidgets.js` |
| **Purpose** | Searchable directory of volunteer/serving opportunities. Clicking an opportunity navigates to `/widgets/opportunity-detail/` for full details. |
| **Authentication** | `<mpp-user-login>` in header |
| **Notes** | The `targeturl` attribute points to a sibling widget page (`/widgets/opportunity-detail/`) where individual opportunity details are displayed. Custom CSS is loaded from an uploaded file (`nw-widget-css.css`) for branding consistency. |

#### 3. `/widgets/small-groups-finder/` -- Small Groups Search

| Attribute | Value |
|-----------|-------|
| **Primary Widget** | Ministry Platform Group Finder (filtered to Small Groups) |
| **Custom Element** | `<mpp-group-finder>` |
| **Element Attributes** | `targeturl="https://northwoods.juxt.studio/widgets/group-finder/"` `countgroupinquiries="true"` `showfullgroups="false"` `showfuturegroups="true"` `ministryid="8"` `customcss="https://northwoods.juxt.studio/wp-content/uploads/nw-widget-css.css"` |
| **Script Source** | `https://my.northwoods.church/widgets/dist/MPWidgets.js` |
| **Purpose** | Searchable directory of small groups, filtered to Ministry ID 8 (Small Groups ministry). Hides full groups, shows upcoming/future groups. Links to `/widgets/group-finder/` for group details. |
| **Authentication** | `<mpp-user-login>` in header |
| **Notes** | Uses `ministryid="8"` to filter results to small groups only. The `countgroupinquiries="true"` attribute tracks interest/inquiry counts. The `targeturl` points to the general group-finder widget page for individual group details. |

#### 4. `/widgets/prayer-form/` -- Prayer Request Submission

| Attribute | Value |
|-----------|-------|
| **Primary Widget** | Ministry Platform Custom Form |
| **Custom Element** | `<mpp-custom-form>` |
| **Element Attributes** | `formguid="249e7a76-6701-42bd-9818-e2479f3eacbb"` `customcss="https://northwoods.juxt.studio/wp-content/uploads/nw-widget-css.css"` |
| **Script Source** | `https://my.northwoods.church/widgets/dist/MPWidgets.js` |
| **Purpose** | Renders a prayer request submission form defined in Ministry Platform, identified by the GUID `249e7a76-6701-42bd-9818-e2479f3eacbb`. Form submissions are sent to Ministry Platform's backend. |
| **Authentication** | `<mpp-user-login>` in header (x4 instances -- 2 in desktop header, 2 in mobile header, plus 2 additional login widgets in the page body for pre-authentication before form submission) |
| **Notes** | This page has extra `<mpp-user-login>` elements within the body content (not just the header), suggesting users may need to authenticate before submitting prayer requests. The form GUID ties it to a specific form configuration in Ministry Platform. |

#### 5. `/widgets/group-finder/` -- General Group Search & Details

| Attribute | Value |
|-----------|-------|
| **Primary Widget** | Ministry Platform Group Finder |
| **Custom Element** | `<mpp-group-finder>` |
| **Element Attributes** | `targeturl="https://northwoods.juxt.studio/group-details/"` `countgroupinquiries="true"` `showfullgroups="false"` `showfuturegroups="true"` `ministryid="8"` `customcss="https://northwoods.juxt.studio/wp-content/uploads/nw-widget-css.css"` |
| **Script Source** | `https://my.northwoods.church/widgets/dist/MPWidgets.js` |
| **Purpose** | General group search/finder widget. Same Ministry ID 8 filter as small-groups-finder but with a different `targeturl` pointing to `/group-details/` (a non-widget page) for group detail views. |
| **Authentication** | `<mpp-user-login>` in header |
| **Notes** | Very similar to `/widgets/small-groups-finder/` but the `targeturl` points to `/group-details/` instead of `/widgets/group-finder/`. This means the small-groups-finder page links INTO this page, while this page links OUT to the main `/group-details/` page. Both share `ministryid="8"`. |

#### 6. `/widgets/my-giving/` -- Personal Giving Dashboard

| Attribute | Value |
|-----------|-------|
| **Primary Widget** | Ministry Platform My Giving Dashboard |
| **Custom Element** | `<mpp-my-giving>` |
| **Element Attributes** | `customcss="https://northwoods.juxt.studio/wp-content/uploads/nw-widget-css.css"` |
| **Script Source** | `https://my.northwoods.church/widgets/dist/MPWidgets.js` |
| **Purpose** | Authenticated personal giving dashboard showing giving history, recurring gifts, and giving management. Requires user login via Ministry Platform SSO. |
| **Authentication** | `<mpp-user-login>` in header; `mpsso.js` from `northwoods.onlinegiving.org` provides SSO bridge |
| **Online Giving Portal** | Navigation links to `https://northwoods.onlinegiving.org/donate/guest_donate?#!/` for new donations |
| **Notes** | This is an authenticated widget -- users must log in via the `<mpp-user-login>` component to see their giving data. The `mpsso.js` script bridges authentication between Ministry Platform and the separate online giving platform at `northwoods.onlinegiving.org`. |

### Summary of Third-Party Services Across Widget Pages

| Service | Domain(s) | Role | Widget Pages Using It |
|---------|-----------|------|----------------------|
| **Ministry Platform (Bonterra)** | `my.northwoods.church` | Church management system (ChMS) providing the `<mpp-*>` web component library for groups, forms, giving, opportunities, event details, and user authentication | All 6 pages (login on all; primary widget on 5 of 6) |
| **BlackPulp / bpPortal** | `widgets.blackpulp.com`, `widgets3.blackpulp.com` | Event management and engagement platform providing event detail, event finder, and event list widgets rendered via JavaScript | All 6 pages (scripts loaded sitewide; primary widget on event-detail) |
| **Online Giving (Ministry Platform)** | `northwoods.onlinegiving.org` | Donation/giving portal with SSO integration to Ministry Platform | All 6 pages (SSO script loaded sitewide; "Give Online" nav link on all) |
| **BugHerd** | `www.bugherd.com` | Visual bug tracking sidebar (staging tool) | All 6 pages (loaded sitewide -- **remove before production launch**) |

### Available MPP Widget Components (from MPWidgets.js)

The `MPWidgets.js` library defines the following custom elements, all available for use on any page that loads the script:

```
Authentication & User:
  <mpp-user-login>         <mpp-user-label>        <mpp-user-service>
  <mpp-about-me>           <mpp-household>         <mpp-locale-selector>

Events:
  <mpp-event-finder>       <mpp-event-details>     <mpp-event-registration>

Groups:
  <mpp-group-finder>       <mpp-group-details>     <mpp-my-groups>

Giving & Finance:
  <mpp-my-giving>          <mpp-my-pledges>        <mpp-pledge-campaign>
  <mpp-my-contribution-statement>  <mpp-my-invoices>  <mpp-pay>  <mpp-checkout>
  <mpp-checkout-complete>

Serving & Opportunities:
  <mpp-opportunity-finder> <mpp-opportunity-details>

Missions:
  <mpp-mission-trip-finder>  <mpp-mission-trip>    <mpp-my-mission-trips>

Forms & Content:
  <mpp-custom-form>        <mpp-prayer-feedback-form>  <mpp-plan-your-visit>
  <mpp-smart-frame>        <mpp-smart-link>        <mpp-rss-reader>
  <mpp-subscribe-to-publication>  <mpp-subscriptions>  <mpp-unsubscribe>

Directory:
  <mpp-online-directory>

Configuration:
  <mpp-widget-configurator>  <mpp-widgets>  <mpp-pre-check>
```

---

## Recommended Fix Order

1. **Fix the sitewide JavaScript "thsi" typo** - This is likely in a single template/code snippet that gets included on multiple pages. Fixing it once should resolve it everywhere.

2. **Correct the dollar amounts on `/now-is-the-time/`** - Campaign page with incorrect financial goals.

3. **Verify the phone number on `/occ/`** - Craig Smith's area code (302 vs 309).

4. **Remove placeholder content** - "Your Subtitle Goes Here" on `/faq/` and `/employment/`. Decide whether to publish or delete the 17+ "Title Here" placeholder posts.

5. **Fix copy-paste errors** - Wrong ministry references on `/youngadults/` and `/55-adults/` email signup sections.

6. **Address high-priority spelling errors** - Missing words, wrong words, and errors that change meaning (see P1 items above).

7. **Fix remaining P2 spelling/grammar errors** across all pages.

8. **Run follow-up audit** on unchecked pages once available.

---

*This audit was generated using automated web content analysis. Some pages load content dynamically via JavaScript which may not have been fully captured. A manual review of dynamic content (staff bios, event listings, form fields) is recommended as a complement to this audit.*
