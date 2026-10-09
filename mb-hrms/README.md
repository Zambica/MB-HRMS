# MB-HRMS: Malawi Banking HR Management and People Analytics

A static web application with a sign-in page, role-based access, employee profiles, MB-TNAF training-needs scoring (six indicators and a composite Skills Gap Index), training history, course recommendations, leave workflow and CSV import/export.

## Deploy with GitHub Actions
1. Create a repository (for example `mb-hrms`) and upload `index.html`, `README.md` and the `.github/workflows/deploy-pages.yml` folder to the `main` branch.
2. Open **Settings → Pages**. Under **Build and deployment → Source**, choose **GitHub Actions**.
3. Push to `main` (or run **Actions → Deploy MB-HRMS to GitHub Pages → Run workflow**). The site appears at `https://YOUR-USERNAME.github.io/mb-hrms/`.

## Sign-in accounts
Starter usernames and passwords are listed in `requirement.txt` (they are no longer shown on the login page or stored as plain text in `index.html`). Change them in User Management after first sign-in, and delete `requirement.txt` if the repository is public.

## Features
- Sign-in page with salted PBKDF2 password hashing, 5-attempt lockout (5 minutes), 15-minute idle timeout, change password, forced change for new or reset accounts
- User Management (admin): add users, assign roles and scope, reset passwords, disable or delete, activity log
- Dashboard: employees in scope, average SGI, high-priority count, pending leave, department and indicator averages
- Import CSV using readable headers (Employee ID, Full Name, Job Title, Department, Appraisal Need, ...); template download included
- Reports exported with plain-word column headers

## Important limitations
GitHub Pages hosts static files only. Accounts, passwords and data are stored in each user's browser (local storage), so sign-in is access control for demonstration and cannot protect data from someone with access to the browser or the page source. There is no shared database, so different users on different devices do not see each other's changes. Do not enter real or confidential employee information. For production use, add a real backend (for example an identity provider, a server-side database, audit logging and HTTPS-only hosting) and validate indicator definitions, weights, thresholds, privacy and access control first. The SGI here is an equal-weight average of six 0–100 indicators, which is illustrative and not a validated model.
