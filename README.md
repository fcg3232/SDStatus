# SDStatus - SecondaryDAO Service Monitoring

Zero-cost uptime monitoring powered by GitHub Actions and Upptime.

## Services Monitored

### Production (naked domains)

- admin.secondarydao.com
- app.secondarydao.com
- api.secondarydao.com/health
- rent.secondarydao.com
- explorer.secondarydao.com

### Development (test\* domains)

- testadmin.secondarydao.com
- testapp.secondarydao.com
- testapi.secondarydao.com/health
- testrent.secondarydao.com
- testexplorer.secondarydao.com

## Setup Instructions

### 1. Create Repository from Upptime Template

```bash
# Visit https://github.com/upptime/upptime
# Click "Use this template" → "Create a new repository"
# Owner: fcg3232
# Repository name: SDStatus
# Visibility: Public (required for GitHub Pages)
# Click "Create repository"
```

### 2. Configure Repository

```bash
# Clone the new repo
cd /home/phelix/SD
git clone git@github.com:fcg3232/SDStatus.git
cd SDStatus

# Copy configuration files
cp ../SDStatus-config/.upptimerc.yml .
cp -r ../SDStatus-config/.github .

# Commit and push
git add .
git commit -m "Configure SDStatus monitoring

- 10 service endpoints (5 prod + 5 dev)
- Auto-labeling and routing workflow
- SecondaryDAO branding

🤖 Generated with [Claude Code](https://claude.com/claude-code)

Co-Authored-By: Claude <noreply@anthropic.com>"
git push
```

### 3. Enable GitHub Pages

```bash
# Via GitHub CLI
gh repo edit fcg3232/SDStatus --enable-pages --pages-branch gh-pages

# Or via web UI:
# Settings → Pages → Source: "gh-pages" branch → Save
```

### 4. Set DNS CNAME

Add this DNS record to your domain provider:

```
Type: CNAME
Name: status
Value: fcg3232.github.io
TTL: 3600
```

### 5. Wait for First Run

GitHub Actions will:

- Run every 5 minutes to check all services
- Generate status page at https://status.secondarydao.com
- Create issues for outages
- Auto-label and route incidents

## Features

- 5-minute health checks
- Auto-generated status page with 90-day history
- Incident issues with auto-labeling (production/development, service)
- Response time graphs
- Dark theme with SecondaryDAO branding

## Next Steps

Once SDStatus is live:

1. Create "SD Master Operations" GitHub Project
2. Integrate Claude error digest to create GitHub issues
3. Add auto-close script for resolved errors

## Documentation

- Upptime: https://upptime.js.org
- GitHub Actions: https://docs.github.com/en/actions
