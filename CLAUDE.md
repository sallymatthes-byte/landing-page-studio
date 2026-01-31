# Landing Page Studio

This project has two modes: **Setup Mode** (first time) and **Studio Mode** (ongoing).

**On first conversation:** Complete Setup Mode to configure everything.
**After setup is complete:** The project becomes a landing page creation studio.

---

## Current Mode Detection

Check if setup is complete by looking for these indicators:
- [ ] Skills installed (frontend-design + Nano Banana Pro)
- [ ] Gemini API key configured (GEMINI_API_KEY environment variable)
- [ ] GitHub repository exists and is connected
- [ ] Vercel deployment configured with custom subdomain
- [ ] Vercel MCP server installed and working

If ANY of these are missing → **Setup Mode**
If ALL are complete → **Studio Mode**

---

# SETUP MODE

Complete these steps in order. Do NOT ask the user to do manual tasks — automate everything possible. Only ask for information you cannot obtain yourself (API keys, domain names, account credentials).

## Step 1: Install Required Skills

Two skills are needed to generate landing pages with custom images:

### 1.1 Install Anthropic Frontend Design Skill

Run these commands:
```
/plugin anthropic
```
Then install the `example-skills` which includes `frontend-design`.

### 1.2 Install Nano Banana Pro Skill

Run these commands:
```
/plugin buildatscale-tv/cloud-code-plugins
```
Then install the `nano-banana-pro` skill.

After installing both, restart Claude Code for skills to take effect.

**Reference:** See `references/video-transcript.md` for the original tutorial.

## Step 2: Configure Gemini API Key

The Nano Banana Pro skill uses Google's Gemini models to generate images.

### 2.1 Get the API Key

Guide the user to:
1. Go to https://aistudio.google.com/
2. Sign in with Google account
3. Click "Get API Key" → "Create API Key"
4. Copy the key

### 2.2 Set the Environment Variable

On Windows, set it permanently:
```powershell
setx GEMINI_API_KEY "the-api-key-here"
```

Then restart Claude Code for the variable to take effect.

## Step 3: Create GitHub Repository

Use the GitHub CLI to create and initialize the repository:

```bash
gh repo create landing-page-studio --public --source=. --remote=origin --push
```

This creates the repo, sets it as origin, and pushes the initial files.

## Step 4: Set Up Vercel

### 4.1 Install Vercel CLI (if needed)

```bash
npm install -g vercel
```

### 4.2 Connect to Vercel

```bash
vercel link
```

Follow prompts to:
- Log in to Vercel (browser will open)
- Connect this project

### 4.3 Configure Custom Subdomain

Ask the user for:
- Their main domain (e.g., `example.com`)
- Desired subdomain (e.g., `pages` → `pages.example.com`)

Then in Vercel dashboard or via CLI:
1. Add the custom domain to the project
2. Provide DNS instructions: Add a CNAME record pointing subdomain to `cname.vercel-dns.com`

### 4.4 Set Up Automatic Deployments

Vercel automatically deploys when changes are pushed to GitHub. Verify:
1. Push a test change
2. Check Vercel dashboard for deployment
3. Verify site is live at the subdomain

## Step 5: Install Vercel MCP Server

Add Vercel MCP to `.mcp.json` for deployment automation:

### 5.1 Get Vercel API Token

Guide user to:
1. Go to https://vercel.com/account/tokens
2. Create a new token with deployment permissions
3. Copy the token

### 5.2 Configure MCP

Create or update `.mcp.json`:
```json
{
  "mcpServers": {
    "vercel": {
      "command": "npx",
      "args": ["-y", "@vercel/mcp"],
      "env": {
        "VERCEL_API_TOKEN": "the-token-here"
      }
    }
  }
}
```

Restart Claude Code to load the MCP server.

## Step 6: Verify Setup

Run these checks:
1. **Skills:** Ask Claude to describe the frontend-design skill
2. **Gemini:** Generate a test image with Nano Banana Pro
3. **GitHub:** Run `git status` to confirm repo connection
4. **Vercel:** Use Vercel MCP to check deployment status
5. **End-to-end:** Create a simple test page, deploy, verify at URL

Once all checks pass, mark setup as complete and switch to Studio Mode.

---

# STUDIO MODE

The project is now a landing page creation studio. The user provides content ideas, and you create complete, deployed landing pages.

## How It Works

1. **User provides:** Business/product description, key features, desired tone
2. **You generate:** Custom images using Nano Banana Pro
3. **You build:** Complete HTML landing page using frontend-design skill
4. **You deploy:** Commit to GitHub, Vercel auto-deploys
5. **Result:** Live page at `subdomain.domain.com/page-name`

## Creating a Landing Page

### Step 1: Gather Information

Ask the user for:
- What is this landing page for? (business, product, service)
- Key selling points or features (3-5)
- Desired tone (professional, playful, luxury, etc.)
- Call to action (what should visitors do?)
- Any specific imagery requests

### Step 2: Plan the Design

Based on the input, decide:
- Visual style (colors, typography direction)
- Section structure (hero, features, testimonials, CTA, etc.)
- Images to generate (hero, product shots, backgrounds)

### Step 3: Generate Images

Use Nano Banana Pro to generate images FIRST, before building the page.

Example workflow:
```
Generate images for:
1. Hero image - [description matching brand]
2. Product/service images - [specific descriptions]
3. Background textures if needed
```

Save images to `public/<page-name>/assets/`

### Step 4: Build the Landing Page

Use the frontend-design skill to create the HTML page.

Key requirements:
- Use Font Awesome for icons (not emoji)
- Include all generated images with proper paths
- Make it responsive
- Add smooth scroll and subtle animations
- Include clear calls to action
- Add contact information section
- Optimize for SEO (meta tags, semantic HTML)

Save the page to `public/<page-name>/index.html`

### Step 5: Deploy

```bash
git add .
git commit -m "Add [page-name] landing page"
git push
```

Vercel will automatically deploy. Verify the page is live.

### Step 6: Report to User

Provide:
- Live URL: `https://subdomain.domain.com/page-name`
- Summary of what was created
- Suggestions for improvements if any

## Folder Structure

```
public/
├── index.html              # Main page (portfolio or featured page)
├── coffee-shop/
│   ├── index.html
│   └── assets/
│       ├── hero.png
│       └── ...
├── water-bottle/
│   ├── index.html
│   └── assets/
│       └── ...
└── [new-pages]/
    ├── index.html
    └── assets/
```

Each page has its own folder with an `index.html` and `assets/` subfolder for images.

## Example Prompt to Create a Page

User: "Create a landing page for a local bakery called Sweet Sunrise. They specialize in artisan sourdough and French pastries. Cozy, warm feeling. They want people to visit the shop or order online."

You would:
1. Generate images (hero with fresh bread, pastry display, bakery interior)
2. Build page with warm colors, elegant typography
3. Include sections: Hero, Products, About, Testimonials, Location/Hours, CTA
4. Deploy and provide URL

## Updating Existing Pages

To modify an existing page:
1. Read the current `public/<page-name>/index.html`
2. Make requested changes
3. Regenerate images if needed
4. Commit and push

## Deleting Pages

To remove a page:
1. Delete the folder `public/<page-name>/`
2. Commit and push
3. Vercel will remove it from deployment

---

## Quick Reference

| Task | Command/Action |
|------|----------------|
| Create new page | Follow Studio Mode workflow |
| Deploy changes | `git add . && git commit -m "message" && git push` |
| Check deployment | Use Vercel MCP or check Vercel dashboard |
| Generate image | Use Nano Banana Pro skill |
| View site | Visit the configured subdomain |

---

## Troubleshooting

### Skills not working
- Ensure both plugins are installed
- Restart Claude Code
- Try disabling and re-enabling the plugin

### Images not generating
- Check GEMINI_API_KEY is set: `echo $env:GEMINI_API_KEY`
- Restart Claude Code after setting the variable

### Deployment not updating
- Check `git status` for uncommitted changes
- Verify GitHub push succeeded
- Check Vercel dashboard for deployment status

### Subdomain not working
- Verify DNS CNAME record is configured
- DNS propagation can take up to 48 hours
- Check Vercel domain settings
