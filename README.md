# Dorm_Dash
# DormDash

**A room-cleaning request app for VIT Vellore hostels — built for the Forge AI Hackathon.**

DormDash replaces the informal "text the hostel WhatsApp group and hope someone reads it" process with a proper two-portal system, and solves a language-barrier problem along the way: most students at VIT-V are North Indian and write in English, while most housekeeping staff are Tamil-speaking. DormDash automatically translates every request so instructions actually reach staff in the language they read comfortably.

## The problem

Room cleaning requests at VIT-V hostels currently go through a shared WhatsApp group. Requests get lost in the scroll, there's no way to track whether a request was seen or completed, and English-language messages are often misunderstood by Tamil-speaking staff — leading to repeated requests, delays, and frustration on both sides.

## The solution

Two focused portals, one shared backend:

- **Student portal** — pick your room, block, and a preferred time slot, and describe what needs doing in plain English.
- **Staff portal** — see requests translated into Tamil (or another language of your choice), filter by hostel block, and mark jobs as started or completed.

Every request is timestamped and tracked through a status pipeline (**Waiting → In progress → Completed**), so nothing falls through the cracks the way a chat message can.

## Key features

- **Two separate portals** — student and staff each get their own page, tailored to what they actually need to do.
- **Automatic translation** — requests written in English are translated for staff automatically, with a fallback translation engine if the primary one is unavailable.
- **Multi-theme UI** — Light, Dark, Ocean, and Sunset themes, switchable at any time.
- **Status tracking** — students can see exactly where their request stands; staff can triage by block and urgency.
- **PRISM-routed AI observability** — the app's LLM-powered features are traced through [PRISM](https://prism.blockconvey.com) (Block Convey) for quality monitoring, in line with the hackathon's AI-governance track.
- **Realistic, mobile-first UI** — designed to look and feel like a real installed app rather than a form on a webpage.

## Tech stack

| Layer | Technology |
|---|---|
| Backend | Python (Flask) |
| Frontend | HTML, CSS, vanilla JavaScript |
| Fonts / Icons | IBM Plex Sans, Noto Sans Tamil, Tabler Icons |
| Translation | LLM-based translation with a dictionary/API fallback |
| Observability | PRISM (Block Convey) |

## Project structure

```
dormdash/
├── app.py                 # Flask app: routes, in-memory data store, translation logic
├── requirements.txt
├── templates/
│   ├── student.html        # Student portal page
│   └── staff.html          # Staff portal page
└── static/
    ├── style.css            # Shared styling and theme definitions
    ├── student.js           # Student portal behavior
    └── staff.js             # Staff portal behavior
```

## Getting started

1. Clone the repository and move into it:
   ```
   git clone <your-repo-url>
   cd dormdash
   ```
2. Install dependencies:
   ```
   pip install -r requirements.txt
   ```
3. (Optional) Set an API key to enable higher-quality AI translation:
   ```
   export ANTHROPIC_API_KEY=your_key_here
   ```
   Without a key, DormDash falls back to a free translation lookup.
4. Run the app:
   ```
   python app.py
   ```
5. Open the student portal at `http://localhost:5000/student` and the staff portal at `http://localhost:5000/staff`.

## Future scope

- Multi-campus rollout beyond VIT-V hostels
- QR codes on room doors for one-tap request creation
- A warden-facing analytics dashboard (peak request times, average completion time)
- Smart staff-assignment based on live workload
- Push/SMS notification when a request is marked complete

## Impact

- Eliminates lost requests from an unstructured WhatsApp group
- Removes the English–Tamil communication gap between students and staff
- Gives hostel administration visibility into cleaning demand and staff performance
- A model that generalizes to any campus with a multilingual student–staff population

## Team

Built for the Forge AI Hackathon, VIT Vellore.

## License
