# 1077 Astro.js Development Environment

A Docker-based development environment for Astro.js with Tailwind CSS, SCSS, and TypeScript.

## Technologies Used

- **[Astro.js](https://astro.build/)** - The web framework for content-driven websites
- **[Tailwind CSS](https://tailwindcss.com/)** - A utility-first CSS framework
- **[SCSS](https://sass-lang.com/)** - CSS preprocessor for enhanced styling capabilities
- **[TypeScript](https://www.typescriptlang.org/)** - JavaScript with syntax for types
- **[Docker](https://www.docker.com/)** & **[Docker Compose](https://docs.docker.com/compose/)** - Containerization platform

## Project Structure

```
1077/
├── app/                  # Application code (mounted to /app in the container)
│   ├── public/           # Static assets
│   ├── src/              # Source code
│   │   ├── assets/       # Project assets
│   │   ├── components/   # Reusable Astro components
│   │   ├── layouts/      # Page layouts
│   │   ├── pages/        # Astro pages
│   │   └── styles/       # SCSS styles
│   │       ├── _variables.scss  # SCSS variables
│   │       └── global.scss      # Main stylesheet
│   ├── astro.config.mjs  # Astro configuration
│   ├── package.json      # Node.js dependencies
│   ├── postcss.config.js # PostCSS configuration
│   └── tailwind.config.js # Tailwind CSS configuration
├── docker-compose.yml    # Docker Compose configuration
├── Dockerfile            # Docker image definition
├── memory-bank/          # Project documentation
└── README.md             # This file
```

## Docker Environment

### docker-compose.yml
```yaml
services:
  app:
    build: .
    container_name: 1077-app
    volumes:
      - ./app:/app
    working_dir: /app
    tty: true
    stdin_open: true
    ports:
      - "4321:4321"  # Map Astro's default port
    command: npm run dev -- --host 0.0.0.0
```

### Dockerfile
```dockerfile
FROM node:22-slim

WORKDIR /app

CMD ["bash"]
```

## Setup & Installation

1. Make sure Docker and Docker Compose are installed on your system.
2. Clone this repository.
3. Start the Docker container and the Astro development server:
   ```bash
   docker compose up -d
   ```
4. The Astro development server will automatically start and be accessible at http://localhost:4321

## Development Workflow

### Accessing the Container Shell

If you need to run commands inside the container:
```bash
docker compose exec app bash
```

### Installing Dependencies

To install additional npm packages:
```bash
docker compose exec app npm install <package-name>
```

### Building for Production

To create a production build:
```bash
docker compose exec app npm run build
```

### Previewing the Production Build

To preview the production build:
```bash
docker compose exec app npm run preview
```

## Accessing the Application

- Development server: http://localhost:4321
- The application features hot reloading, so changes to files will automatically update in the browser.

## Styling with SCSS and Tailwind

This project uses both Tailwind CSS and SCSS:

- **Tailwind CSS** - Use utility classes directly in your HTML/Astro templates
- **SCSS** - Custom styles are defined in `src/styles/global.scss` and can use variables from `src/styles/_variables.scss`

## Additional Resources

- [Astro Documentation](https://docs.astro.build/)
- [Tailwind CSS Documentation](https://tailwindcss.com/docs)
- [SCSS Documentation](https://sass-lang.com/documentation/)
- [TypeScript Documentation](https://www.typescriptlang.org/docs/)
- [Docker Documentation](https://docs.docker.com/)