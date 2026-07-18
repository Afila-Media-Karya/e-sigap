[CONTEXT]
Design a B2B SaaS onboarding dashboard for a WhatsApp CRM application. The product helps users connect WhatsApp API, manage contacts, and handle customer service messaging.

[OVERALL STYLE]
Visual style: Minimalist SaaS Dashboard. Mood: Clean, professional, technical, calm. Inspired by Vercel and Tailwind UI. The interface feels highly productive, flat, and relies on strict structural borders rather than shadows for depth.

[SCREEN TO GENERATE]
Generate the "Dashboard Onboarding" screen with this layout:
- Left: A fixed, collapsible sidebar navigation. 
- Top: A minimalist top navigation bar with search and utility icons.
- Main: A centered content area with a maximum width constraint (e.g., max-w-4xl) to maintain optimal readability, containing a hero greeting and two main functional cards.

[COMPONENTS]
Required components:
- Collapsible Sidebar: Includes a workspace switcher at the top, categorized navigation links (Overview, WhatsApp, Configuration, CRM, Workspace) with SVG icons, and a user profile at the bottom. When collapsed, text labels hide, leaving only centered icons.
- Top Bar: Includes a sidebar toggle button (left), a Search input "Cmd+K" (center/right), theme toggle icon, language icon, and notification bell.
- Onboarding Stepper Card: A large container labeled "Get started with Kirimdev" and a "0 / 4" counter. Contains 4 list items. Each item has a grey circular radio icon, a title, a description, and an outlined action button on the right.
- Link List Card: A container labeled "Read this first" containing 4 clickable rows. Each row has an icon, a text label, and a small diagonal arrow pointing up-right to indicate an external link.

[DESIGN TOKENS]
Colors:
- Primary: #10B981 (Emerald green — used for status indicators, active states, and specific badges)
- Background: #FFFFFF (Pure white main canvas)
- Surface: #FFFFFF (Card background, same as canvas but separated by border)
- Text-primary: #111827 (Near black)
- Text-secondary: #6B7280 (Cool gray)
- Border: #E5E7EB (Light gray, essential for separating all elements)
- Hover/Accent: #F9FAFB (Very light gray for row and button hovers)

Typography:
- Headings: Inter or similar geometric sans-serif. H1 24px font-bold tracking-tight. Card titles 16px font-semibold.
- Body: 14px, weight 400, line-height 1.5. text-gray-500 for descriptions.
- Labels: 12px, font-medium for small badges (like "NEW" or "BETA").

Spacing: 8px grid. Use padding p-6 for main cards, gap-4 between layout elements. 
Border radius: rounded-md (6px) for buttons, rounded-lg (8px) or rounded-xl (12px) for main outer cards.
Elevation: Strictly flat design. No drop shadows. Rely entirely on border border-gray-200.

[CONTENT]
Hero headline: "Welcome back, Aso"
Subheadline: "Finish the steps below to start using Kirimdev."

Stepper items:
1. "Connect a WhatsApp account" / "Link your Cloud API or Business number." / Button: "Connect ->"
2. "Import or add contacts" / "Build your customer list to enable broadcasts." / Button: "Add contacts ->"
3. "Create message templates" / "Pre-approved templates power campaigns." / Button: "New template ->"
4. "Start chatting with customers" / "Open the inbox and reply to incoming messages." / Button: "Open inbox ->"

Read this first links:
- "Kirimdev quickstart guide"
- "The 24-hour window & templates"
- "Meta's official per-message rates"
- "Kirimdev blog — tips & case studies"

[INTERACTIONS]
- Sidebar Collapse: Add a smooth CSS transition. When collapsed (simulated via CSS classes or Alpine.js if needed, but focus on the UI state), the width shrinks. Sidebar menu items become icon-only. 
- Tooltips: Add a tooltip structure (absolute positioning, hidden by default, visible on group-hover) for sidebar icons so when it is collapsed, hovering shows the menu name.
- Hover states: Main card rows and sidebar links should have hover:bg-gray-50 transition-colors duration-150. 
- Focus: focus:ring-2 focus:ring-gray-200 focus:outline-none for accessibility.

[RESPONSIVE]
Desktop-first structure. On mobile screens (max-width: 768px), hide the sidebar behind a hamburger menu and stack all card contents vertically. 

[ACCESSIBILITY]
Use semantic tags (<aside>, <nav>, <main>, <section>). Ensure SVG icons have aria-hidden="true" or proper titles. Text contrast must be WCAG AA compliant.

[TECH OUTPUT]
Generate code as pure HTML + Tailwind CSS (using standard utility classes). Do not use React or Vue frameworks for this output. Structure the HTML cleanly with comments separating Sidebar, Topbar, and Main Content.