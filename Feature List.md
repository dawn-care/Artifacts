# **D.A.W.N. Feature List — Tablet, Caregiver & Staff Apps**

D.A.W.N. is three apps on one backend: a tablet the resident never has to touch, a family app that supplies the content, and a staff app that decides when content plays.

| App | Who uses it | Its job |
| :---- | :---- | :---- |
| Carepartner tablet | Resident with dementia | Show a calm, always-on screen; play media when it is scheduled or when staff start it |
| Caregiver web app | Family and loved ones | Record and tag media, lay out the tablet's screen, schedule playback, and preview what the tablet shows |
| Staff app | Aides, nurses, activities staff, on their own phones | Play the right clip in the moment, rate how it went, and ask the caregiver for new videos |

## **How to read this list**

Stories are grouped by app and epic, with IDs by app (CP, CG, ST, SYS). New stories added for features that were built get the next free ID.

* **Priority:** **Must (beta)** = needed to test the core idea at St. Ann's this year; **Should** = strong value once the core works; **Could (later)** = worth it, not this year.
* **Status:** **Done**, **In progress**, **Partly done** (the note says what is missing), **Not started**, or **Blocked**. Taken from the code and the DAWN project board as of November 21, 2026.
* **Issues:** the related issues in [dawn-care/DAWN](https://github.com/dawn-care/DAWN/issues).
* **Maps to:** the requirements in [Functional and Non-Functional Requirements](Functional%20and%20Non-Functional%20Requirements.md) that the story satisfies.
* *Italic notes* say what is still missing from a story that is not done.

## **Carepartner tablet**

The resident never has to tap anything: the screen is always on, media starts on a schedule or from the staff app, and each screen uses a handful of words at most.

| ID | Epic | Story | Priority | Status | Issues | Maps to |
| :---- | :---- | :---- | :---- | :---- | :---- | :---- |
| CP-1 | Always-on screen | As a resident, I see the day of the week and the time of day (morning, afternoon, evening) in very large type at all times, so I know when I am without asking. | Must (beta) | Done | [#290](https://github.com/dawn-care/DAWN/issues/290), [#309](https://github.com/dawn-care/DAWN/issues/309), [#316](https://github.com/dawn-care/DAWN/issues/316), [#321](https://github.com/dawn-care/DAWN/issues/321) | FR-1, NFR-9 |
| CP-2 | Always-on screen | As a resident, I see a large photo of a family member, so I feel connected when no one is visiting. | Must (beta) | Done | [#307](https://github.com/dawn-care/DAWN/issues/307), [#406](https://github.com/dawn-care/DAWN/issues/406) | FR-1 |
| CP-3 | Always-on screen | As a resident, I see what's next as a picture plus a clock face (lunch, bingo, a visit), so I know what's coming. | Could (later) | Not started | [#289](https://github.com/dawn-care/DAWN/issues/289), [#311](https://github.com/dawn-care/DAWN/issues/311) | FR-8 |
| CP-4 | Always-on screen | As a resident, I see today's nurse's photo and first name, so I know who to ask for help. | Should | Not started | [#312](https://github.com/dawn-care/DAWN/issues/312) | FR-8 |
| CP-5 | Always-on screen | As a resident, I see the weather as an icon, one word and the temperature, so I know whether to expect warm or cold. | Must (beta) | Done | [#310](https://github.com/dawn-care/DAWN/issues/310), [#390](https://github.com/dawn-care/DAWN/issues/390) | FR-1 |
| CP-6 | Always-on screen | As a caregiver, I choose which widgets appear on the screen, so it matches what my carepartner can handle. | Must (beta) | Done | [#360](https://github.com/dawn-care/DAWN/issues/360) | FR-1, FR-11 |
| CP-7 | Playback | As a resident, I see scheduled media play full screen at its set time with no tap needed, so the day starts with a familiar face. | Must (beta) | Done | [#298](https://github.com/dawn-care/DAWN/issues/298) | FR-2 |
| CP-8 | Playback | As staff, when I press Play in the staff app, the clip starts on the tablet within 3 seconds. *Play and stop work; meeting 3 seconds might need media cached on the tablet.* | Must (beta) | Partly done | [#288](https://github.com/dawn-care/DAWN/issues/288), [#300](https://github.com/dawn-care/DAWN/issues/300), [#301](https://github.com/dawn-care/DAWN/issues/301) | FR-3, NFR-11 |
| CP-9 | Playback | As a resident with hearing loss, I see large captions and the sender's photo and name on every video. | Should | Not started | [#305](https://github.com/dawn-care/DAWN/issues/305) | FR-7 |
| CP-10 | Playback | As a resident, the screen returns to the always-on view by itself when playback ends. | Must (beta) | Done | [#296](https://github.com/dawn-care/DAWN/issues/296) | FR-2 |
| CP-11 | Playback | As a resident, I can tap the big family photo to replay the latest message; nothing else depends on tapping. | Could (later) | Not started | [#308](https://github.com/dawn-care/DAWN/issues/308) | FR-2 |
| CP-12 | Time of day | As a resident, the screen turns dim and warm at night with one reassuring line, so it calms rather than wakes me. | Must (beta) | Done | [#314](https://github.com/dawn-care/DAWN/issues/314), [#321](https://github.com/dawn-care/DAWN/issues/321) | FR-4 |
| CP-13 | Activities | As a resident, 30–45 minutes before an activity the "next" tile becomes an invitation (a photo of me there before, or a short clip from the activity director). | Could (later) | Not started | [#317](https://github.com/dawn-care/DAWN/issues/317) | FR-8 |
| CP-14 | Activities | As a resident, later on the day of an event I see a photo from it, so I have something from today to hold onto. | Could (later) | Not started |  | FR-24 |
| CP-15 | Care rounds | As a resident, a few minutes before med rounds I see the nurse's photo and "coming", with no medication details, so I'm not surprised by who arrives. | Could (later) | Not started | [#289](https://github.com/dawn-care/DAWN/issues/289) | FR-8 |
| CP-16 | Device | As the facility, the tablet pairs by a code on its screen and runs locked in kiosk mode (no notifications, settings or exits). *Pairing works; kiosk mode is blocked.* | Must (beta) | Partly done | [#315](https://github.com/dawn-care/DAWN/issues/315), [#320](https://github.com/dawn-care/DAWN/issues/320) | FR-5, NFR-12 |
| CP-17 | Device | As staff, I can scan a code on the tablet to open this resident in the staff app. | Could (later) | Not started |  | FR-19 |
| CP-18 | Device | As a resident, the screen keeps working if the Wi-Fi drops and recovers without anyone touching it. *The tablet keeps its last screen and catches up when it reconnects; media isn't cached yet.* | Should | Partly done | [#287](https://github.com/dawn-care/DAWN/issues/287), [#300](https://github.com/dawn-care/DAWN/issues/300), [#313](https://github.com/dawn-care/DAWN/issues/313) | NFR-12 |
| CP-19 | Telemetry | As the team, the tablet reports every play (scheduled, staff or tap) as it starts, finishes, stops or fails, and what was shown, with no medical data. *Plays are reported; what the screen showed and touches aren't recorded yet.* | Must (beta) | Partly done | [#286](https://github.com/dawn-care/DAWN/issues/286), [#299](https://github.com/dawn-care/DAWN/issues/299), [#381](https://github.com/dawn-care/DAWN/issues/381) | FR-6, NFR-1 |
| CP-20 | Always-on screen | As a resident, I see a short message from my family, such as where I am or who is coming, so I feel reassured. | Should | Done | [#360](https://github.com/dawn-care/DAWN/issues/360), [#372](https://github.com/dawn-care/DAWN/issues/372) | FR-1 |
| CP-21 | Always-on screen | As a resident, I see today's reminders (up to 10, each with a time and an icon), with the next one highlighted. *The caregiver types them in; linking them to the calendar is still being designed.* | Should | Partly done | [#404](https://github.com/dawn-care/DAWN/issues/404) | FR-1 |
| CP-22 | Always-on screen | As a resident, I see my team's latest score and a news headline, so I have something familiar to talk about. | Could (later) | Done | [#310](https://github.com/dawn-care/DAWN/issues/310) | FR-1 |
| CP-23 | Playback | As a resident, scheduled audio plays over a photo (or my usual screen), and a scheduled photo shows for a set time, so a song or voice message has a face with it. | Should | Done | [#298](https://github.com/dawn-care/DAWN/issues/298) | FR-2 |

## **Caregiver app (family)**

Family members supply the content and the knowledge about the person. They record and tag media, lay out the tablet's screen and schedule playback, but never trigger playback in the moment. The caregiver app is a web app; a mobile app is in the backlog ([#281](https://github.com/dawn-care/DAWN/issues/281)).

| ID | Epic | Story | Priority | Status | Issues | Maps to |
| :---- | :---- | :---- | :---- | :---- | :---- | :---- |
| CG-1 | Account | As a family member, I sign in to the caregiver web app with Google or a code sent to my email, and manage my carepartner's content. | Must (beta) | Done | [#442](https://github.com/dawn-care/DAWN/issues/442), [#443](https://github.com/dawn-care/DAWN/issues/443), [#225](https://github.com/dawn-care/DAWN/issues/225) | FR-9 |
| CG-2 | Account | As the primary family contact, I invite siblings to contribute; each sees only this resident. | Should | Not started |  | FR-14 |
| CG-3 | Media library | As a family member, I record a video, audio clip or photo in the browser, or upload files from my computer. | Must (beta) | Done | [#335](https://github.com/dawn-care/DAWN/issues/335), [#369](https://github.com/dawn-care/DAWN/issues/369), [#226](https://github.com/dawn-care/DAWN/issues/226), [#227](https://github.com/dawn-care/DAWN/issues/227) | FR-10 |
| CG-4 | Media library | As a family member, I tag each item with the situations it helps in (wants to go home, doesn't know where they are, anxious or upset, starting the day, winding down) and the family members in it, so staff can find it in the moment. | Must (beta) | Done | [#335](https://github.com/dawn-care/DAWN/issues/335) | FR-10 |
| CG-5 | Media library | As a family member, I mark a clip "always true" or "true until \[date\]", so a promise like "see you Sunday" stops playing after Sunday. | Should | Not started |  | FR-10, FR-19 |
| CG-6 | Scheduling | As a family member, I schedule any media to play at a set time, once or repeating daily, weekly or monthly, and can skip single days, on a calendar with a month view. | Must (beta) | Done | [#122](https://github.com/dawn-care/DAWN/issues/122), [#334](https://github.com/dawn-care/DAWN/issues/334) | FR-12 |
| CG-7 | Preview | As a family member, I preview my carepartner's screen exactly as the tablet shows it. *Captions aren't built yet (CP-9).* | Should | Done | [#228](https://github.com/dawn-care/DAWN/issues/228) | FR-13 |
| CG-8 | Media library | As a family member, I see short recording tips before I record (under a minute, speak slowly, say the day and place, don't promise visits you can't keep, don't share news of a death). | Should | Not started |  | FR-10 |
| CG-9 | Resident profile | As a family member, I add family members with a name and relationship; staff see them as folders of clips. *No photos yet, and people can only be added while tagging media.* | Should | Partly done | [#335](https://github.com/dawn-care/DAWN/issues/335) | FR-15 |
| CG-10 | Resident profile | As a family member, I add guidance per person (e.g. "Husband passed away: please don't tell her again; talk about her garden"). *Staff already see guidance notes, but caregivers can't write them in the app yet.* | Should | Partly done |  | FR-15 |
| CG-11 | Resident profile | As a family member, I choose photos for the always-on screen, with an optional caption. | Must (beta) | Done | [#307](https://github.com/dawn-care/DAWN/issues/307), [#406](https://github.com/dawn-care/DAWN/issues/406), [#407](https://github.com/dawn-care/DAWN/issues/407) | FR-1, FR-11 |
| CG-12 | Resident profile | As a family member, I list my carepartner's interests (gardening, hymns, baseball), so activities staff can invite them to matching events. | Should | Not started |  | FR-24 |
| CG-13 | Resident profile | As a family member, I enter planned visit dates, so the tablet shows my photo and a clock when I'm coming. | Should | Not started |  | FR-8 |
| CG-14 | Requests | As a caregiver, I get a video request from staff when my carepartner keeps asking about something, and pass it on to the right family member. | Should | Not started |  | FR-16 |
| CG-15 | Updates | As a family member, I see which of my clips were played and how often they helped. | Should | Not started |  | FR-16 |
| CG-16 | Updates | As a family member, I see photos of events my carepartner attended, so I have something specific to talk about when I call. | Could (later) | Not started |  | FR-24 |
| CG-17 | Screen layout | As a family member, I place widgets (photo, message, reminders, weather, sports, news) on my carepartner's 4 × 3 screen; the day and time always stay in the top-left corner. | Must (beta) | Done | [#360](https://github.com/dawn-care/DAWN/issues/360), [#408](https://github.com/dawn-care/DAWN/issues/408) | FR-11 |
| CG-18 | Screen layout | As a family member, I set my carepartner's awake hours; outside them the tablet shows the night screen and nothing is scheduled. | Must (beta) | Done | [#340](https://github.com/dawn-care/DAWN/issues/340), [#341](https://github.com/dawn-care/DAWN/issues/341), [#481](https://github.com/dawn-care/DAWN/issues/481) | FR-4, FR-11 |
| CG-19 | Account | As a family member, I pair a tablet using the code on its screen, and switch between carepartners if I care for more than one. | Must (beta) | Done | [#400](https://github.com/dawn-care/DAWN/issues/400), [#405](https://github.com/dawn-care/DAWN/issues/405) | FR-14 |
| CG-20 | Feedback | As a family member, I send the team feedback on how D.A.W.N. is working or not working for my carepartner. | Must (beta) | Not started | [#244](https://github.com/dawn-care/DAWN/issues/244) | FR-17 |
| CG-21 | Updates | As a family member, I get a notification when staff rate one of my videos or other media as having helped, so I know my content is making a difference. | Should | Not started |  | FR-16 |

## **Staff app**

Staff decide when content plays: they tap what's happening, pick a clip, and rate it afterward, and those ratings are the project's main evidence. Target: under 10 seconds from pocket to playing. The app runs on staff members' own Android and iOS phones and has no sign-in yet.

| ID | Epic | Story | Priority | Status | Issues | Maps to |
| :---- | :---- | :---- | :---- | :---- | :---- | :---- |
| ST-1 | Access | As staff, I open a resident by scanning their tablet's code, or from my unit's list sorted by room. *Staff pick from a list of every resident; scanning and sorting by room aren't built.* | Must (beta) | Partly done | [#274](https://github.com/dawn-care/DAWN/issues/274), [#446](https://github.com/dawn-care/DAWN/issues/446) | FR-19 |
| ST-2 | Access | As a facility admin, I give each staff member a role (aide/nurse, activities, admin) and a unit, which limits what they see and do. | Should | Not started |  | FR-18 |
| ST-20 | Access | As staff, I sign in to the staff app on my own phone, so only facility staff can see residents and play clips on their tablets. | Must (beta) | In progress | [#491](https://github.com/dawn-care/DAWN/issues/491) | FR-18, NFR-3 |
| ST-3 | Play the right clip | As staff, I tap what's happening from a fixed list (asking for someone, wants to go home, doesn't know where they are, anxious or upset, starting the day, winding down). | Must (beta) | Done | [#275](https://github.com/dawn-care/DAWN/issues/275) | FR-19 |
| ST-4 | Play the right clip | As staff, when a resident asks for someone I pick the person and see the family's guidance for them, such as for someone who has died. | Should | Not started |  | FR-15, FR-19 |
| ST-5 | Play the right clip | As staff, I see one recommended clip (matching tag, not expired, right time of day, most recent) with who it's from and its length, plus up to two alternatives. *Staff see every matching clip, the best rated first, then the newest.* | Must (beta) | Partly done | [#275](https://github.com/dawn-care/DAWN/issues/275) | FR-19 |
| ST-6 | Play the right clip | As staff, I play the clip on the room's tablet, see whether it reached the tablet and how it ended, and can stop it from my phone. | Must (beta) | Done | [#288](https://github.com/dawn-care/DAWN/issues/288), [#301](https://github.com/dawn-care/DAWN/issues/301), [#382](https://github.com/dawn-care/DAWN/issues/382), [#383](https://github.com/dawn-care/DAWN/issues/383) | FR-20 |
| ST-7 | Play the right clip | As staff, I see the last clip played for this resident and how it was rated. *The last play is shown, but not its rating.* | Should | Partly done | [#299](https://github.com/dawn-care/DAWN/issues/299) | FR-20 |
| ST-8 | Feedback | As staff, right after a clip plays I rate it on five steps (much worse to helped a lot), within 5 minutes of it ending. | Must (beta) | Done | [#276](https://github.com/dawn-care/DAWN/issues/276), [#286](https://github.com/dawn-care/DAWN/issues/286) | FR-21, NFR-10 |
| ST-9 | Feedback | As staff, I get a reminder if I haven't rated a clip I played. | Should | Not started | [#234](https://github.com/dawn-care/DAWN/issues/234) | FR-21 |
| ST-10 | Video requests | As staff, when no clip fits I can send the caregiver a request with a topic and a short message. *The screen is built but doesn't send anything yet.* | Should | Partly done |  | FR-23, NFR-1 |
| ST-11 | Video requests | As staff, I see each request's status; the unit coordinator is notified if family hasn't replied in 3 days. | Could (later) | Not started |  | FR-23 |
| ST-12 | Staff content | As staff, I record a short intro of myself, and admins can add general clips ("You're safe here") used as fallbacks. | Should | Not started |  | FR-25 |
| ST-13 | Activities | As activities staff, I see which residents' interests match today's events, so I know whom to invite. | Could (later) | Not started |  | FR-24 |
| ST-14 | Activities | As staff, 15 minutes before an event I see the list of rooms to bring to it. | Could (later) | Not started |  | FR-24 |
| ST-15 | Activities | As activities staff, I mark who attended an event, which gives the team an attendance measure. | Could (later) | Not started |  | FR-24 |
| ST-16 | Activities | As activities staff, I take a photo at an event and check off the residents in it; residents without photo consent can't be checked, and the photo goes to their tablet and family. | Could (later) | Not started |  | FR-24, NFR-2 |
| ST-18 | Admin | As a facility admin, I set each resident's photo-consent flag. | Could (later) | Not started |  | FR-25, NFR-2 |
| ST-19 | Play the right clip | As staff, I see and edit a resident's sleeping hours, and can't play anything during them. *The screen is built, but the hours aren't saved to the server yet.* | Should | Partly done |  | FR-22 |

## **Shared backend**

| ID | Requirement | Priority | Status | Issues | Maps to |
| :---- | :---- | :---- | :---- | :---- | :---- |
| SYS-1 | One purpose taxonomy, defined once, shared by clip tags (CG-4), staff situations (ST-3) and request topics (ST-10). *Tags and situations share one list on the server; request topics are a separate list.* | Must (beta) | Partly done |  | FR-10, FR-19 |
| SYS-2 | Roles and scopes: family sees their own carepartners; aides and nurses play and rate for their unit; activities staff manage events; admins manage staff and consent. *Only caregiver accounts exist; staff have no sign-in yet.* | Must (beta) | Partly done | [#443](https://github.com/dawn-care/DAWN/issues/443) | FR-18, NFR-3 |
| SYS-3 | Real-time play and stop commands from the staff app to a tablet, with an acknowledgement back. | Must (beta) | Done | [#286](https://github.com/dawn-care/DAWN/issues/286), [#288](https://github.com/dawn-care/DAWN/issues/288), [#301](https://github.com/dawn-care/DAWN/issues/301) | FR-3, FR-20 |
| SYS-4 | Clip recommendation by rules: matching tag, then not expired, then right time of day, then most recent; weighted by past ratings. *Clips are ordered by recent ratings, then newest; expiry and time of day aren't used.* | Must (beta) | Partly done |  | FR-19 |
| SYS-5 | Expired "true until" clips are never recommended or scheduled. | Should | Not started |  | FR-19 |
| SYS-6 | A schedule model for meals, activities, visits and care rounds that drives the "next" tile, invitations and escort lists. | Could (later) | Not started | [#289](https://github.com/dawn-care/DAWN/issues/289) | FR-8, FR-24 |
| SYS-7 | Email or push notifications to the caregiver for video requests. | Should | Not started |  | FR-16 |
| SYS-8 | Hosting moved from the RIT server to AWS, with data and media migrated without loss. | Must (beta) | Not started | [#213](https://github.com/dawn-care/DAWN/issues/213), [#219](https://github.com/dawn-care/DAWN/issues/219), [#221](https://github.com/dawn-care/DAWN/issues/221), [#223](https://github.com/dawn-care/DAWN/issues/223) | NFR-14 |

## **Open questions for Gerry and Tim**

☑ Can floor staff carry phones on shift? *Answered: yes, staff use their own Android or iOS phones.*  
☐ Is there a photo release on file for each resident, and who keeps it? Needed before ST-16.  
☐ Does the activity director already photograph events or keep attendance? ST-15 and ST-16 should reuse that habit.