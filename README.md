# Odoo Project Lifecycle on Odoo.sh

This repository is a starter structure for an Odoo project that will be managed through Odoo.sh using GitHub-based CI/CD.

## Project structure

- `custom_addons/` - place your custom Odoo modules here
- `addons/` - optional local Odoo addons repository if you maintain a custom set of modules
- `.gitignore` - ignores local runtime and editor data

## Recommended lifecycle

1. Development branch
   - Create new features and bug fixes here.
   - Test locally using a local Odoo instance or a development build.

2. Staging branch
   - Promote tested changes for user acceptance testing.
   - Use Odoo.sh staging builds for validation.

3. Production branch
   - Deploy only stable, validated code.
   - Production builds should be triggered only after successful checks.

## Odoo.sh workflow

### 1) Create a GitHub repository

- Create a new GitHub repository.
- Push this project to GitHub.
- Make sure the default branch is the one you want to use as your development branch.

### 2) Create an Odoo.sh project

- Sign in to Odoo.sh.
- Click Create Project.
- Choose a project name, database type, and Odoo version.
- Connect to GitHub and authorize the repository.
- Select the repository to link to the Odoo.sh project.

### 3) Configure branch model

Odoo.sh commonly uses these branches:

- Production: production-ready code
- Staging: pre-production validation
- Development: day-to-day feature work

Map your GitHub branches to the Odoo.sh environments. Keep the flow:

Development -> Staging -> Production

### 4) Trigger builds

- Odoo.sh automatically creates builds when changes are pushed.
- Each build can be used to validate the code before deployment.
- Review build logs for dependency, migration, or module errors.

### 5) Deploy to staging and production

- Promote a successful build to Staging for functional testing.
- After validation, promote the same stable revision to Production.
- Keep production deployments small and controlled.

## Suggested Git flow

```bash
git checkout development
git pull origin development
git checkout -b feature/my-module
git add .
git commit -m "Add custom module"
git push origin feature/my-module
```

Then merge into the appropriate branch in GitHub and let Odoo.sh run the build/deploy pipeline.

## Important notes

- Never deploy untested code directly to production.
- Use staging for UAT and regression testing.
- Keep module names clear and versioned.
- Review Odoo.sh build logs after every push.

## Next step

To fully complete the setup, sign in to Odoo.sh and connect this GitHub repository from the Odoo.sh dashboard. The project is ready to be linked and managed using the Odoo.sh branch/build pipeline.
