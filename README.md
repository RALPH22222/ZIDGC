# 🎮 Zamboanga Indie Game Developer Club (ZIDGC) — Portfolio Platform

Welcome to the official web repository for the **Zamboanga Indie Game Developer Club (ZIDGC)**. This platform serves as the central showcase and community hub for indie game developers, designers, artists, and enthusiasts based in Zamboanga.

---

## 🎯 About the Project

The ZIDGC Portfolio Platform is designed to highlight the talent, creativity, and progress of the local game development community. It provides a clean, modern interactive space to display:

- 🕹️ **Projects Showcase**: Highlighting games across all development stages:
  - **Planned**: Concept stage, game design documents, and pitch ideas.
  - **In Development**: Active projects with progress logs and screenshots.
  - **Testing**: Alpha/Beta builds needing community playtesting and feedback.
  - **Released**: Finished titles available to play or download.
- 📅 **Events Hub**: 
  - **Past Events**: Highlights, photos, recaps, and winner showcases from previous game jams and workshops.
  - **Future Events**: Upcoming meetups, hackathons, jams, and learning sessions.
- 🚀 **Mission & Vision**: Our mandate, long-term community roadmap, and core goals.
- 👥 **Members & Pioneers**: A hall of fame celebrating founders, core contributors, and club members.

---

## 🛠 Tech Stack

| Category | Technology | Description |
|---|---|---|
| **Core Framework** | [React 19](https://react.dev/) | UI library for component-based web development |
| **Language** | [TypeScript](https://www.typescriptlang.org/) | Strongly typed JavaScript for scalability and bug prevention |
| **Build Tool** | [Vite](https://vitejs.dev/) | Ultra-fast development server & bundler |
| **Styling** | [Tailwind CSS v4](https://tailwindcss.com/) | Utility-first CSS engine (`@tailwindcss/vite`) |
| **Routing** | [React Router](https://reactrouter.com/) | Client-side page navigation & layout management |
| **Iconography** | [Lucide React](https://lucide.dev/) / [React Icons](https://react-icons.github.io/react-icons/) | Modern SVG icon sets for interactive UI elements |
| **Code Quality** | ESLint | Linting and static analysis rules |

---

## 🏗 Directory & Code Architecture

To ensure long-term maintainability, easy debugging, and smooth multi-developer collaboration, this project follows a strict **Modular Component-Driven Architecture**.

> ⚠️ **No Monolithic / Spaghetti Code**: All UI components, page views, static data, and TypeScript types are modularized into dedicated files and directories. `App.tsx` serves as the root router and layout wrapper, rather than containing inline UI logic.

### Recommended Directory Structure

```text
src/
├── assets/             # Static assets (logos, banner art, game screenshots)
├── components/         # Reusable atomic UI components
│   ├── common/         # Buttons, Cards, Modals, Badges, Loaders
│   ├── layout/         # Navbar, Footer, Sidebar, PageContainer
│   ├── projects/       # ProjectCard, ProjectFilter, StageBadge
│   ├── events/         # EventCard, EventTimeline, CountdownTimer
│   └── members/        # MemberCard, ProfileGrid
├── pages/              # Page view components mapped to React Router routes
│   ├── HomePage.tsx
│   ├── ProjectsPage.tsx
│   ├── EventsPage.tsx
│   ├── AboutPage.tsx
│   ├── MembersPage.tsx
│   └── NotFoundPage.tsx
├── layouts/            # Master layout templates wrapping page content
│   └── MainLayout.tsx
├── routes/             # Router setup and route configuration
│   └── AppRoutes.tsx
├── data/               # Decoupled mock & static content data files
│   ├── projectsData.ts # Data array for games (Planned, Dev, Testing, Released)
│   ├── eventsData.ts   # Data array for past & upcoming events
│   └── clubData.ts     # Mission, vision, goals, and pioneer profiles
├── types/              # Centralized TypeScript definitions & schemas
│   ├── index.ts        # Re-exported types
│   ├── project.ts      # Project & Stage interfaces
│   ├── event.ts        # Event interfaces
│   └── member.ts       # Member & Pioneer interfaces
├── App.tsx             # Root component initializing Router & Global Providers
├── main.tsx            # React DOM mounting entry point
└── index.css           # Global Tailwind CSS imports & theme overrides
```

### Architectural Principles

1. **Separation of Concerns**: Presentation (components/pages) is decoupled from Data (`data/`) and Types (`types/`). Updating a game title or adding a new member requires only editing a data file without modifying UI rendering logic.
2. **Component Reusability**: Common elements (cards, badges, buttons) are encapsulated in `src/components/common/`.
3. **Single Responsibility**: Each file exports one clear component, hook, or type definition.

---

## 🌿 Multi-Developer Workflow & Git Branching Strategy

> **Question**: *Since this project will be invited by multiple developers, do I need to make branching?*  
> **Answer**: **Yes, absolutely!** When multiple developers collaborate on a single codebase, working directly on the `main` branch leads to code conflicts, broken builds, and overwritten work. A structured branching strategy is essential.

### Recommended Git Flow Strategy

```
main        --------------------------------------------● (Production Release)
               \                                      /
dev             ●--------●------------------●--------● (Integration Branch)
                 \      /                  /        /
feature/projects  ●----●                  /        /
                        \                /        /
feature/events           ●--------------●        /
                                                /
fix/navbar-bug                                 ●
```

#### 1. Branch Hierarchy

- **`main`**: Production-ready code ONLY. Never push code directly to `main`.
- **`dev`** (or `staging`): The primary integration branch where feature branches are merged after testing.
- **Feature / Task Branches**: Branch off `dev` for every new feature, page, bug fix, or documentation update.
  - `feature/projects-page` (adding the projects showcase page)
  - `feature/events-timeline` (building the events section)
  - `fix/navbar-mobile-toggle` (fixing a specific UI bug)
  - `docs/readme-update` (updating documentation)

#### 2. Workflow Rules for Collaborators

1. **Clone & Setup**:
   ```bash
   git clone https://github.com/your-org/zidgc.git
   cd zidgc
   npm install
   ```

2. **Create a Feature Branch**:
   Always pull the latest changes from `dev` before creating a new branch:
   ```bash
   git checkout dev
   git pull origin dev
   git checkout -b feature/your-feature-name
   ```

3. **Develop & Commit**:
   Keep commits small, descriptive, and focused:
   ```bash
   git add .
   git commit -m "feat(projects): add stage filtering for games list"
   ```

4. **Push & Open a Pull Request (PR)**:
   Push your branch to GitHub and create a Pull Request targeting `dev`:
   ```bash
   git push origin feature/your-feature-name
   ```
   - Request at least 1 code review from a fellow member before merging.
   - Ensure `npm run build` and `npm run lint` pass cleanly before approval.

---

## 🚀 Getting Started for Developers

### Prerequisites

- [Node.js](https://nodejs.org/) (v18.0.0 or higher recommended)
- [npm](https://www.npmjs.com/) or [pnpm](https://pnpm.io/)

### Installation & Execution

1. **Install dependencies**:
   ```bash
   npm install
   ```

2. **Add planned project libraries** (when starting development):
   ```bash
   npm install react-router-dom lucide-react
   ```

3. **Start the local development server**:
   ```bash
   npm run dev
   ```
   Open your browser at `http://localhost:5173`.

4. **Build for Production**:
   ```bash
   npm run build
   ```

5. **Preview Production Build**:
   ```bash
   npm run preview
   ```

---

## 🤝 Contributing & Community Guidelines

We welcome contributions from all ZIDGC community members and developers!

### 💻 1. Code & Platform Contributions (Website Developers)

If you are contributing code, UI components, pages, or bug fixes to this platform:
1. **Follow Directory Standards**: Maintain the clean, modular folder structure established in `src/`.
2. **Type Safety**: Write explicit TypeScript interfaces/types for all components, props, and hooks.
3. **Branching Workflow**: Follow the Git Branching Strategy (branch from `dev`, test locally, and open a Pull Request).
4. **Data Formatting**: Keep static data formatted neatly in `src/data/`.

### 🎮 2. Game & Project Submissions (Club Members & Game Devs)

If you want to showcase your game project (Planned, In Development, Testing, or Released) on the website:
- **No Coding Required**: You do not need to modify React code to add your game.
- **Submission Template**: A **Standard Project Submission Template** will be released soon.
- **How it Works**: Members will simply fill out the submission template/form with game details (title, stage, synopsis, screenshots, trailer, download links), and the maintainers will integrate it into `src/data/projectsData.ts`.

---

## 👥 Project Governance & Maintainers

This repository is owned and maintained by the ZIDGC development team:

- **Lead Maintainer & Repository Owner**: [@RALPH22222](https://github.com/RALPH22222)
- **Co-Maintainers & Contributors**: ZIDGC Core Developer Team & Community Contributors

---

*Maintained with ❤️ by [@RALPH22222](https://github.com/RALPH22222) & the **Zamboanga Indie Game Developer Club (ZIDGC)**.*
