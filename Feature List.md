# **D.A.W.N. Feature List — Tablet, Caregiver & Staff Apps**

D.A.W.N. becomes three apps on one backend: a tablet the resident never has to touch, a family app that supplies the content, and a staff app that decides when content plays.

| App | Who uses it | Its job |
| :---- | :---- | :---- |
| Carepartner tablet | Resident with dementia | Show a calm always-on screen; play videos when scheduled or started by staff |
| Caregiver app | Family and loved ones | Record and tag videos, fill in the resident's profile, answer video requests |
| Staff app | Aides, nurses, activities staff, facility admin | Play the right clip in the moment, rate it, request videos, log events |

Stories are grouped by epic, with IDs by app (CP, CG, ST, SYS). Priority: **Must (beta)** \= needed to test the core idea at St. Ann's this year; **Should** \= strong value once the core works; **Could (later)** \= worth it, not this year. "Maps to" points at the requirement IDs already in Additional Elements where one exists.

## **Carepartner tablet**

The resident never has to tap anything: the screen is always on, videos start on a schedule or from the staff app, and each screen uses a handful of words at most.

| ID | Epic | Story | Priority | Maps to |
| :---- | :---- | :---- | :---- | :---- |
| CP-1 | Always-on screen | As a resident, I see the day of the week and the time of day (morning, afternoon, evening) in very large type at all times, so I know when I am without asking. | Must (beta) |  |
| CP-2 | Always-on screen | As a resident, I see a large photo of a family member, so I feel connected when no one is visiting. | Must (beta) |  |
| CP-3 | Always-on screen | As a resident, I see what's next as a picture plus a clock face (lunch, bingo, a visit), so I know what's coming. | Must (beta) |  |
| CP-4 | Always-on screen | As a resident, I see today's nurse's photo and first name, so I know who to ask for help. | Should |  |
| CP-5 | Always-on screen | As a resident, I see the weather as one icon and one word, so I know whether to expect warm or cold. | Should |  |
| CP-6 | Always-on screen | As staff, I can switch the date, weather and captions on or off per resident, so the screen matches what each person can handle. | Should |  |
| CP-7 | Video playback | As a resident, I see the morning message play full screen at a set time with no tap needed, so the day starts with a familiar face. | Must (beta) |  |
| CP-8 | Video playback | As staff, when I press Play in the staff app, the clip starts on the tablet within 3 seconds. | Must (beta) |  |
| CP-9 | Video playback | As a resident with hearing loss, I see large captions and the sender's photo and name on every video. | Must (beta) |  |
| CP-10 | Video playback | As a resident, the screen returns to the always-on view by itself when a video ends. | Must (beta) |  |
| CP-11 | Video playback | As a resident, I can tap the big family photo to replay the latest message; nothing else depends on tapping. | Should |  |
| CP-12 | Time of day | As a resident, the screen turns dim and warm at night with one reassuring line, so it calms rather than wakes me. | Must (beta) |  |
| CP-13 | Activities | As a resident, 30–45 minutes before an activity the "next" tile becomes an invitation (a photo of me there before, or a short clip from the activity director). | Should |  |
| CP-14 | Activities | As a resident, later on the day of an event I see a photo from it, so I have something from today to hold onto. | Could (later) |  |
| CP-15 | Care rounds | As a resident, a few minutes before med rounds I see the nurse's photo and "coming", with no medication details, so I'm not surprised by who arrives. | Could (later) |  |
| CP-16 | Device | As the facility, the tablet pairs by device code and runs locked in kiosk mode (no notifications, settings or exits). | Must (beta) |  |
| CP-17 | Device | As staff, I can scan a code on the tablet to open this resident in the staff app. | Should |  |
| CP-18 | Device | As a resident, the screen keeps working with today's cached content if the Wi-Fi drops, and recovers without anyone touching it. | Should |  |
| CP-19 | Telemetry | As the team, the tablet logs what was shown and every video start (scheduled, staff or tap), finish and stop, with no medical data. | Must (beta) | FR5, NFR1 |

## **Caregiver app (family)**

Family members supply the content and the knowledge about the person; they record and tag clips but never trigger playback in the moment.

| ID | Epic | Story | Priority | Maps to |
| :---- | :---- | :---- | :---- | :---- |
| CG-1 | Account | As a family member, I log in on my phone and manage my relative's content. | Must (beta) | FR3 |
| CG-2 | Account | As the primary family contact, I invite siblings to contribute; each sees only this resident. | Should |  |
| CG-3 | Video library | As a family member, I record a video in the app or upload one from my camera roll. | Must (beta) | FR3 |
| CG-4 | Video library | As a family member, I tag each clip with a purpose from a fixed list (morning, calming, asking for me, why you're here, evening, activity encouragement, special occasion), so staff can find it in the moment. | Must (beta) |  |
| CG-5 | Video library | As a family member, I mark a clip "always true" or "true until \[date\]", so a promise like "see you Sunday" stops playing after Sunday. | Must (beta) |  |
| CG-6 | Video library | As a family member, I choose which clip is the scheduled morning message and when it plays. | Must (beta) | FR3 |
| CG-7 | Video library | As a family member, I preview a clip exactly as it will look on the tablet, captions included. | Should | FR3 |
| CG-8 | Video library | As a family member, I see short recording tips before I record (under a minute, speak slowly, say the day and place, don't promise visits you can't keep, don't share news of a death). | Must (beta) |  |
| CG-9 | Resident profile | As a family member, I add family members with photo, name and relationship, used on the tablet and in the staff app. | Must (beta) |  |
| CG-10 | Resident profile | As a family member, I add structured guidance per person or topic (e.g. "Husband passed away: please don't tell her again; talk about her garden"). | Must (beta) |  |
| CG-11 | Resident profile | As a family member, I upload photos for the always-on screen. | Must (beta) |  |
| CG-12 | Resident profile | As a family member, I list my relative's interests (gardening, hymns, baseball), so activities staff can invite them to matching events. | Should |  |
| CG-13 | Resident profile | As a family member, I enter planned visit dates, so the tablet shows my photo and a clock when I'm coming. | Should |  |
| CG-14 | Requests | As a family member, I get a video request when my relative keeps asking about something, with a one-tap path to record the answer. | Should |  |
| CG-15 | Updates | As a family member, I see which of my clips were played and how often they helped. | Should |  |
| CG-16 | Updates | As a family member, I see photos of events my relative attended, so I have something specific to talk about when I call. | Could (later) |  |

## **Staff app**

Staff decide when content plays: they tap what's happening, the app picks the clip, and a one-tap rating afterward becomes the project's main evidence. Target: under 10 seconds from pocket to playing.

| ID | Epic | Story | Priority | Maps to |
| :---- | :---- | :---- | :---- | :---- |
| ST-1 | Access | As staff, I open a resident by scanning their tablet's code, or from my unit's list sorted by room with photos. | Must (beta) |  |
| ST-2 | Access | As a facility admin, I give each staff member a role (aide/nurse, activities, admin) and a unit, which limits what they see and do. | Must (beta) |  |
| ST-3 | Play the right clip | As staff, I tap what's happening from a fixed list (asking for someone, wants to go home, doesn't know where they are, anxious, starting the day, winding down). | Must (beta) |  |
| ST-4 | Play the right clip | As staff, when a resident asks for someone I pick the person and see the family's guidance for them, including "no videos" for someone who has died. | Must (beta) |  |
| ST-5 | Play the right clip | As staff, I see one recommended clip (matching tag, not expired, right time of day, most recent) with who it's from, its length and family notes, plus up to two alternatives. | Must (beta) |  |
| ST-6 | Play the right clip | As staff, I play the clip on the room's tablet and can stop it from my phone. | Must (beta) |  |
| ST-7 | Play the right clip | As staff, I see the last clip played for this resident and how it was rated. | Should |  |
| ST-8 | Feedback | As staff, right after a clip plays I rate it in one tap (helped, no change, made it worse) or choose "remind me later". | Must (beta) | FR4, NFR2 |
| ST-9 | Feedback | As staff, I get a reminder if I haven't rated a clip I played. | Should | FR4 |
| ST-10 | Video requests | As staff, when no clip fits I see a fallback clip and can send family a structured request (topic plus recipients, with a preview, no free text). | Should | NFR1 |
| ST-11 | Video requests | As staff, I see each request's status; the unit coordinator is notified if family hasn't replied in 3 days. | Could (later) |  |
| ST-12 | Staff content | As staff, I record a short intro of myself, and admins can add general clips ("You're safe here") used as fallbacks. | Should |  |
| ST-13 | Activities | As activities staff, I see which residents' interests match today's events, so I know whom to invite. | Should |  |
| ST-14 | Activities | As staff, 15 minutes before an event I see the list of rooms to bring to it. | Should |  |
| ST-15 | Activities | As activities staff, I mark who attended an event, which gives the team an attendance measure. | Should | FR5 |
| ST-16 | Activities | As activities staff, I take a photo at an event and check off the residents in it; residents without photo consent can't be checked, and the photo goes to their tablet and family. | Could (later) |  |
| ST-17 | Admin | As a facility admin, I pair a tablet to a room and resident. | Must (beta) | FR3 |
| ST-18 | Admin | As a facility admin, I review new family clips before they go live and can pull any clip. | Should |  |
| ST-19 | Admin | As a facility admin, I set each resident's photo-consent flag and screen settings (date, weather, captions). | Must (beta) |  |

## **Shared backend and non-functional requirements**

The one piece to settle before either UI is built is SYS-1: the purpose tags families use, the situations staff tap and the topics in video requests must be the same list.

| ID | Requirement | Priority | Maps to |
| :---- | :---- | :---- | :---- |
| SYS-1 | One purpose taxonomy, defined once in the domain model, shared by clip tags (CG-4), staff situations (ST-3) and request topics (ST-10). | Must (beta) |  |
| SYS-2 | Roles and scopes: family sees one resident; aides and nurses play and rate for their unit; activities staff manage events; admins manage tablets, staff, consent and uploads. | Must (beta) |  |
| SYS-3 | Real-time play and stop commands from the staff app to a tablet, with an acknowledgement back. | Must (beta) |  |
| SYS-4 | Clip recommendation by rules: matching tag, then not expired, then right time of day, then most recent. Weight by past ratings only once a resident has enough of them. | Must (beta) |  |
| SYS-5 | Expired "true until" clips are never recommended or scheduled. | Must (beta) |  |
| SYS-6 | A schedule model for meals, activities, visits and care rounds that drives the "next" tile, invitations and escort lists. | Must (beta) |  |
| SYS-7 | Email or push notifications to family for video requests. | Should |  |
| SYS-8 | Media stored in S3; data and media migrated from the RIT server without loss. | Must (beta) | FR1, FR2 |
| NFR-A | No medical information in telemetry, ratings or video requests: structured fields only, no free text. | Must (beta) | NFR1 |
| NFR-B | Staff can start the right clip in 3 taps and under 10 seconds; rating takes 1 tap. | Must (beta) | NFR2 |
| NFR-C | The tablet never requires a tap, and nothing moves or flashes on its own apart from videos. | Must (beta) |  |
| NFR-D | Tablet legibility: orientation text 76px or larger, other text 26px or larger, text contrast 7:1 or better, touch targets about 20 mm or larger. | Must (beta) |  |
| NFR-E | Event photos are only ever shown for residents whose photo-consent flag is on. | Must (beta) |  |

## **Open questions for Gerry and Tim**

Several Must stories depend on how St. Ann's actually works, so confirm these before sprint planning.

☐ Can floor staff carry phones on shift? If not, ST-1 and ST-6 need a shared device or a staff-only control on the tablet.  
☐ Which three moments would staff actually use the video library in? Build those situations first.  
☐ Do any beta residents take their own medication? If not, pill reminders stay out of scope (CP-15 only shows the nurse coming).  
☐ Is there a photo release on file for each resident, and who keeps it? Needed before ST-16.  
☐ Who normally contacts families: floor staff, a social worker or a coordinator? This decides who sends and follows up on video requests (ST-10, ST-11).  
☐ Does the activity director already photograph events or keep attendance? ST-15 and ST-16 should reuse that habit.  
☐ Does Gerry accept an always-on screen with a few words alongside the video, or should both versions go into the beta as a comparison?