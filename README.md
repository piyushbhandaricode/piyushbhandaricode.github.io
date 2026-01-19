# Portfolio Website

A modern, minimalist portfolio built with Astro and Tailwind CSS.

## Local Development

1. Clone the repository:
```bash
git clone https://github.com/piyushbhandaricode/piyushbhandaricode.github.io.git
cd piyushbhandaricode.github.io
```

2. Install dependencies:
```bash
npm install
```

3. Start the development server:
```bash
npm run dev
```

4. Build for production:
```bash
npm run build
```

## Deployment

This portfolio is automatically deployed to GitHub Pages at https://piyushbhandaricode.github.io/ whenever changes are pushed to the `main` branch.

The deployment is handled by GitHub Actions using the workflow defined in `.github/workflows/deploy.yml`.

### Manual Deployment

To trigger a manual deployment:
```bash
git add .
git commit -m "Your commit message"
git push origin main
```

The site will be automatically built and deployed within a few minutes.

## Editing Your Portfolio

All content is managed through a single configuration file: `src/config.ts`

### Personal Information

Update your basic information:
```typescript
name: "Your Name"
title: "Your Job Title"
description: "Brief description"
accentColor: "#1d4ed8"  // Change the theme color
```

### Social Links

Add or update your social media links (all optional):
```typescript
social: {
  email: "your-email@example.com",
  linkedin: "https://linkedin.com/in/yourprofile",
  twitter: "https://x.com/yourhandle",
  github: "https://github.com/yourusername",
}
```

### About Section

Update your bio:
```typescript
aboutMe: "Your bio text here..."
```

### Skills

Add your technical skills:
```typescript
skills: ["JavaScript", "React", "Node.js", "Python", "AWS", "Docker"]
```

### Projects

Showcase your projects:
```typescript
projects: [
  {
    name: "Project Name",
    description: "Project description",
    link: "https://github.com/yourusername/project",
    skills: ["React", "Node.js"],
  }
]
```

### Experience

Add your work experience:
```typescript
experience: [
  {
    company: "Company Name",
    title: "Your Job Title",
    dateRange: "Jan 2022 - Present",
    bullets: [
      "Achievement or responsibility 1",
      "Achievement or responsibility 2",
    ],
  }
]
```

### Education

Add your educational background:
```typescript
education: [
  {
    school: "University Name",
    degree: "Bachelor of Science in Computer Science",
    dateRange: "2014 - 2018",
    achievements: [
      "Achievement 1",
      "Achievement 2",
    ],
  }
]
```

## Hiding Sections

To hide any section (Skills, Projects, Experience, or Education), simply remove or comment out that section's data in `src/config.ts`.

## Tech Stack

- **Astro** - Static site generator
- **Tailwind CSS v4** - Styling
- **TypeScript** - Type-safe configuration
- **Tabler Icons** - Icon library
