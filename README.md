# ArchGen Frontend (archgen-frontend)

ArchGen Frontend is a modern, single-page web application (SPA) built with **Next.js (App Router)** and **TypeScript**. It provides an interactive cloud diagramming canvas utilizing **React Flow** to generate, visualize, edit, and optimize cloud architectures, compile Terraform files, track project version history, and view security audits.

---

## 1. Tech Stack & Key Libraries

The application dependencies are configured in [package.json](file:///c:/Users/Praveen/Desktop/New%20folder/archgen-frontend/package.json):

* **Framework**: Next.js 14+ (React 18) with App Router.
* **Diagram Canvas**: `reactflow` (version 11+) for node graph manipulation, custom nodes, routing edges, and viewport controls.
* **Styling**: Tailwind CSS with custom styling and CSS variables in [globals.css](file:///c:/Users/Praveen/Desktop/New%20folder/archgen-frontend/app/globals.css).
* **Animations**: `framer-motion` for smooth micro-animations, transitions, slide-outs, and loading indicators.
* **Icons**: `lucide-react` for cloud service icons, action triggers, and sidebar elements.
* **Utilities**: `tailwind-merge` and `clsx` for conditional CSS class styling.

---

## 2. Directory Structure

The repository organizes layout pages, hooks, state managers, and types:

```
archgen-frontend/
├── app/                  # Next.js App Router folders
│   ├── dashboard/        # User project dashboard
│   ├── login/            # Login view and verification forms
│   ├── register/         # Signup view
│   ├── healthz/          # Frontend container health checks
│   ├── ready/            # Frontend container readiness checks
│   ├── page.tsx          # Main interactive canvas workspace
│   ├── layout.tsx        # Global HTML wrapper
│   └── globals.css       # Tailwind directives and CSS variables
├── components/           # Reusable UI component elements
│   ├── canvas/           # Custom React Flow nodes and edges
│   └── ui/               # Buttons, inputs, modals, alerts
├── hooks/                # Custom React hook utilities
├── lib/                  # Shared configurations and API client
└── types/                # TypeScript type declarations
```

---

## 3. Core Interface Components

The main canvas is defined in [page.tsx](file:///c:/Users/Praveen/Desktop/New%20folder/archgen-frontend/app/page.tsx) and includes:

1. **Control Sidebar (Component Palette)**: Allows users to drag and drop cloud nodes (Compute, Databases, Storage, Gateways, Security, Monitoring) onto the canvas.
2. **React Flow Canvas**: Renders custom nodes representing cloud services (such as AKS, Application Gateway, Azure SQL Database, and Key Vault) grouped inside Subnets and virtual networks.
3. **Inspector Panel (Node Details)**: Displays the properties of the selected node, allowing users to configure details like size, subnet, availability zone, IP boundaries, and pricing tier.
4. **Control Deck**: Actions panel to trigger cost optimization (`/optimize-cost`), security/compliance validation (`/validate-architecture`), explanation generation (`/explain-architecture`), and AI-assist transformations (`/ai-assist`).
5. **Terraform Compiler Modal**: Compiles and downloads `main.tf`, `variables.tf`, `outputs.tf`, and `terraform.tfvars`.

---

## 4. Configuration & Environment Variables

Create a `.env` file at the root of this folder to connect to the backend gateway:

| Variable | Type | Example | Description |
|---|---|---|---|
| `NEXT_PUBLIC_API_URL` | `str` | `http://api.printnow.space/api` | The base URL of the API Gateway routing traffic downstream. |

---

## 5. Development & Build Commands

Manage dependencies and execute the client using standard scripts:

### Installation
Install node modules:
```bash
npm install
```

### Run Locally (Development Server)
Launch the local Hot Module Replacement (HMR) dev server at `http://localhost:3000`:
```bash
npm run dev
```

### Build & Optimize for Production
Compile code and build the production bundle under `.next/`:
```bash
npm run build
```

### Start Production Server
Launch the production build locally:
```bash
npm run start
```
