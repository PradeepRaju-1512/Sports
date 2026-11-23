# VERSION II
# IIIT Tiruchirappalli (IIITT) Sports Platform — New From-Scratch

## 1. Vision & Build Approach

This new version replaces the earlier generic/SaaS build with a **ground-up rebuild** tailored specifically to **IIIT Tiruchirappalli (IIITT)** and its **2 major sports events per year (one per semester)**, culminating in **Prothymos**.

* **Visual Direction (Unified Across the Entire Website):** Dark-editorial aesthetic inspired by *Red Dead Redemption II*—deep obsidian/charcoal backgrounds, dramatic poster framing, bold condensed display typography, and high-contrast crimson/ochre/gold/cream accents on every page so the platform feels cohesive, atmospheric, and distinctly IIITT rather than a generic portal.
* **Clean From-Scratch Execution:** Built cleanly from scratch in modular stages and tested locally (`npm install`, `npm run db:push`, `npm run db:seed`, `npm run dev`) before pushing to GitHub and deploying to Render.
* **Single Source of Truth:** Connects Sports Clubs, Batch Inductions, Student Registration, `CLUB` vs. `NON_CLUB` Auction Classes, Live Stage Bidding, Match Lineups, Live Scoring, and the Permanent Sports Archive.

---

## 2. Covered Sports & Clubs (All 9 Sports)

All sports are organized into two clear groups across the landing page, clubs directory, facilities, tournaments, and archive:

* **Outdoor & Team Sports**
* Football
* Cricket
* Volleyball
* Kho Kho
* Kabaddi


* **Indoor Games**
* Badminton
* Table Tennis
* Carrom
* Chess



---

## 3. Landing Page Structure

When a user opens the main landing page, the page flows in this exact vertical order:

1. **Conditional Ultra-Short Top Alert Banner (≤ 5 Words)**
* Appears **only** when there is an active, urgent high-priority announcement.
* Strictly **no more than 5 words** long (e.g., `PROTHYMOS AUCTION LIVE NOW` or `MAIN GROUND CLOSED TODAY`).
* Completely hidden when no urgent alert is active.


2. **Hero Banner (`college.png` + `"IIIT TRICHY SPORTS"`)**
* Uses the watermark-free `college.png` artwork as the hero backdrop with dark vignette shading and bold **`IIIT TRICHY SPORTS`** display typography.
* Paired with the clean top navigation bar (`Overview`, `Archive`, `Current Tournament`, `Auction`, `Live Auction`, `Live` / `Upcoming`, plus compact role/account controls).


3. **Brief Announcements & Notice Board**
* Directly below the hero, a concise, scannable notice section showing key announcements and updates.


4. **Sports Clubs Section (All 9 Clubs)**
* Displays cards for **Football, Cricket, Volleyball, Kho Kho, Kabaddi, Badminton, Table Tennis, Carrom, and Chess** (grouped by Outdoor & Team Sports and Indoor Games).
* Clicking any club card opens that club's **dedicated page**.



---

## 4. Dedicated Club Page (`/clubs/:slug`)

Each of the 9 sports has its own dedicated page structured as follows:

* **Upcoming Activities Section (Top)**
* Displays a **compact list of upcoming activities** for that club (showing activity type, target batch, category/gender, date/time, and venue).
* **Editable by the Club Secretary or Club Coordinator** for that club:
* **Activity Type:** Dropdown with `Practice`, `Induction`, `Meeting`, or `Other` (choosing `Other` reveals a custom free-text input).
* **Target Batch:** `1st Year`, `2nd Year`, `3rd Year`, `4th Year`, `MTech`, or `All Batches`.
* **Category / Gender:** `Boys`, `Girls`, or `Open`.
* **Time & Venue:** e.g., `5:00 PM`, date, and ground/court/hall.


* **Automatic Member Notification:** Adding or updating an activity sends a notification to the relevant club members (and induction applicants if the activity is an `Induction`).


* **Leadership & Members Section (Below Upcoming Activities)**
1. **Club Secretary** (head of the club).
2. **Club Coordinators** organized by year (`1st Year`, `2nd Year`, `3rd Year`, `4th Year`, `MTech`).
3. **Club Members** (inducted roster; joining requires proper induction and Club Secretary approval, and club membership determines `CLUB` vs. `NON_CLUB` auction base-price eligibility).



---

## 5. Top Navigation Bar Behavior & Conditional Tabs

### A. `Overview`

* Displays **upcoming tournaments and their dates**.
* Updated/managed by the **Sports Secretary**.
* Whenever changes are saved, gives the Sports Secretary an explicit option to **notify everyone or not** (`Yes` / `No`).

### B. `Archive` (Year Dropdown — e.g., `2025`, `2024`)

* Clicking `Archive` opens a **dropdown of years** (`2025`, `2024`, etc.).
* Selecting a year opens that year's archive view showing **that year's tournaments** and the **list of sports**.
* Selecting a sport displays:
1. **Winners** and **2 Runners-Up**.
2. **Points table**.
3. Below the points table, a **split view**:
* **Left side:** List of **all matches played**, ordered from **Final** down to the **first/opening match** (Final → Semis → Quarterfinals → earlier rounds/last match).
* **Right side:** A **Teams dropdown**—selecting a team displays all **team members** with each member's **role**, **year**, and **branch**.




* **Search & Filters:**
* Search by **year, sport, team, or player**.
* Filter by **tournament type** and **competition format**.



### C. `Current Tournament`

* Designed around IIITT's rhythm of **2 sports events per year (one per semester)**.
* **Sports Secretary Controls:** Chooses the tournament, sports, timetables, and tournament structure, with an option to **notify everyone or not** whenever changes are made.
* **Spectator / Campus View:**
* Shows the **currently happening match** with **live scores** updated on field by an **assigned Match Scorer**.
* Below the current match is a **sport selector bar** listing the sports in the tournament.
* Clicking a sport shows its **points table** and **past matches** in that tournament.
* Clicking a past match opens its **detailed points/score breakdown**.



### D. `Auction` (Conditional Tab)

* **Visible only** when the **Sports Secretary** plans/opens an auction.
* **Student Enrollment:** Any student can enroll freely with **year**, **branch**, **sports (multiple allowed)**, and **positions (multiple allowed)**.
* **`CLUB` vs. `NON_CLUB` Base Prices:** Players belong to **Club** or **Non-Club** classes with **different base prices**.
* **Post-Deadline Sports Secretary View:** Once the Sports Secretary's registration deadline closes, the Sports Secretary sees all enrolled students **separated by sport**, can **edit student registration details** (to fix mistakes), **search** for a player, and **sort by year, branch, or position**.

### E. `Live Auction` (Conditional / Stage View)

* Run in the auditorium by a **single operator** while players and captains physically bid in the room.
* Updates are pushed **live in real time across all logged-in devices** (and projector/war-room screens), with server-side purse/quota validation and atomic state updates.

### F. `Live` / `Upcoming` (Dynamic Tab)

* **`Live` tab appears only** when there are live matches or active events, showing:
* Live scorecards
* Current match status
* Upcoming fixtures
* Match results
* Live tournament brackets


* When **no matches are live**, the **`Live` tab stays hidden** and is **replaced by `Upcoming**` showing the next scheduled matches.

---

## 6. Roles, Campus Operations & Persistence

* **Authority & Roles:** Faculty Advisor / PED oversees the Sports Secretary; Sports Secretary manages tournaments, auctions, notices, and event permissions (Captains, Auction Operator, Match Scorers assigned by the Sports Secretary), alongside Club Secretaries, year-wise Club Coordinators, Equipment/Ground Staff, Students/Players, and public read-only spectators.
* **Campus Utilities & Vertical Integration:** Supports court/gym booking, QR equipment issuing (tracked assets + bulk stock + overdue blocks + no-dues records), pickup games, player profiles, and vertical flow from registration/induction and auction rosters to lineups, live scoring, and permanent archive records.
* **Stack & Deployment:** Node.js + TypeScript, PostgreSQL (`DATABASE_URL`), real-time SSE/WebSocket updates, local testing first, GitHub version control, and Render hosting.

---
