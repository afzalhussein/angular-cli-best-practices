# Angular CLI Best Practices

A collection of recommended practices for using Angular CLI effectively in modern development workflows. This guide includes setup of common dependencies like **Prettier** (for code formatting) and **Bootstrap** (for styling), and is verified to work on both **Windows (PowerShell)** and **macOS/Linux** environments.

---

## 📦 Project Setup

### Initialize a New Angular Project

```bash
ng new Primer --routing false --style css --skip-git --skip-tests
```

- `--routing false`: Avoids setting up Angular Router unless needed.
- `--style css`: Uses plain CSS (change to `scss` or `less` if preferred).
- `--skip-git`: Skips Git initialization.
- `--skip-tests`: Skips generating `.spec.ts` files.

---

## 🧰 Installing Dependencies

### Install Bootstrap (for styling)

```bash
npm install bootstrap@5.2.3
```

Update `angular.json` to include Bootstrap CSS:

```bash
ng config projects.Primer.architect.build.options.styles '["src/styles.css", "node_modules/bootstrap/dist/css/bootstrap.min.css"]'
```

On **Windows PowerShell**, use:

```powershell
ng config projects.Primer.architect.build.options.styles `
'["src/styles.css", "node_modules/bootstrap/dist/css/bootstrap.min.css"]'
```

### Install Prettier (for code formatting)

```bash
npm install --save-dev prettier
```

Add a `.prettierrc` file with your preferred settings:

```json
{
  "printWidth": 80,
  "tabWidth": 2,
  "useTabs": false,
  "semi": true,
  "singleQuote": true,
  "trailingComma": "es5",
  "bracketSpacing": true,
  "arrowParens": "always"
}
```

Format your code using:

```bash
ng format
```

> Ensure your IDE (e.g., VS Code) is configured to use Prettier as the default formatter.

---

## 🛠️ Angular CLI Best Practices

### Generate Code

Always use the Angular CLI to scaffold new files:

```bash
ng generate component my-component
ng generate service my-service
ng generate module my-module
```

#### Useful Flags:
- Preview changes before applying:
  ```bash
  ng generate component my-component --dry-run
  ```
- Generate inline templates and styles:
  ```bash
  ng generate component my-component --inline-template --inline-style
  ```

---

### Organize Files

Use flags to better control file structure:

- Automatically register in a specific module:
  ```bash
  ng generate component shared/my-component --module=app.module
  ```
- Avoid creating extra folders when appropriate:
  ```bash
  ng generate service my-service --flat
  ```

> Use `--flat` sparingly to avoid cluttering root directories.

---

### Maintain Code Quality

Angular CLI integrates tools like TSLint/ESLint and Prettier for consistent code style.

- Run linting:
  ```bash
  ng lint
  ```
- Automatically fix issues:
  ```bash
  ng lint --fix
  ```
- Format your code:
  ```bash
  ng format
  ```

---

### Keep Dependencies Updated

Use `ng update` to safely upgrade Angular packages:

```bash
ng update
ng update @angular/core @angular/cli
```

> Always review migration notes — Angular schematics may automatically apply breaking changes.

---

### Run Tests and Build for Production

- Run unit tests:
  ```bash
  ng test
  ```
- Run end-to-end tests:
  ```bash
  ng e2e
  ```
- Build for production:
  ```bash
  ng build --configuration=production
  ```
  Or shorthand:
  ```bash
  ng build --prod
  ```

---

### Development Server

Start the development server with live reload:

```bash
ng serve
```

#### Useful Options:
- Open browser automatically:
  ```bash
  ng serve --open
  ```
- Use a custom port:
  ```bash
  ng serve --port 4201
  ```
- Disable live reload:
  ```bash
  ng serve --live-reload false
  ```

---

### Integrate Third-Party Libraries

Use schematics for smooth integration:

```bash
ng add @angular/material
```

> Ensure the library supports Angular schematics before using `ng add`.

---

### Manage Configuration

The `angular.json` file controls build, serve, and test configurations.

- Safely modify configuration using the CLI:
  ```bash
  ng config projects.Primer.architect.build.options.styles '["src/styles.css", "node_modules/bootstrap/dist/css/bootstrap.min.css"]'
  ```

On **Windows PowerShell**:

```powershell
ng config projects.Primer.architect.build.options.styles `
'["src/styles.css", "node_modules/bootstrap/dist/css/bootstrap.min.css"]'
```

> Avoid manual edits unless necessary; prefer CLI commands to reduce risk of syntax errors.

---

### CLI Flags and Shorthands

| Flag | Shorthand | Description |
|------|-----------|-------------|
| `--dry-run` | `-d` | Preview file changes without writing |
| `--inline-template` | `-it` | Create component with inline template |
| `--inline-style` | `-is` | Create component with inline styles |
| `--skip-tests` | `-st` | Skip generating test files |
| `--module` | `-m` | Register item in a specific module |
| `--flat` | `-f` | Generate files in current folder |

---

### Automate Tasks with npm Scripts

Define reusable tasks in `package.json`:

```json
"scripts": {
  "start": "ng serve",
  "build:prod": "ng build --configuration=production",
  "lint": "ng lint",
  "test": "ng test",
  "format": "ng format"
}
```

Then run:
```bash
npm run build:prod
```

---

## ✅ Summary Checklist

| Task | Command |
|------|---------|
| Initialize project | `ng new Primer --routing false ...` |
| Install dependencies | `npm install [package-name]` |
| Install Prettier | `npm install --save-dev prettier` |
| Generate code | `ng generate component my-comp` |
| Preview changes | `ng g component my-comp --dry-run` |
| Lint code | `ng lint` |
| Format code | `ng format` |
| Update packages | `ng update @angular/core` |
| Run tests | `ng test`, `ng e2e` |
| Build for production | `ng build --prod` |
| Serve app | `ng serve --open` |
| Add third-party libs | `ng add @angular/material` |
| Configure angular.json | `ng config ...` |

---

## 📝 Contributing

Contributions are welcome! Please read our [Contributing Guide](CONTRIBUTING.md) for details on how to get involved.