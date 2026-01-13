# Installation Guide - init-aisp-specs Skill

This guide explains how to install the `init-aisp-specs` Claude Code skill.

## Prerequisites

- Claude Code v2.0 or higher
- Git (for method 1 and 2)

---

## Installation Methods

### Method 1: One-Command Install (Recommended)

The fastest way to install - adds the skill globally for all your projects:

```bash
# Step 1: Add the AISP marketplace to Claude Code
/plugin marketplace add bar181/aisp-open-core

# Step 2: Install the skill
/plugin install init-aisp-specs@aisp-open-core
```

That's it! The skill is now available across all your projects.

---

### Method 2: Manual Install

Choose between global (available everywhere) or project-specific (recommended for teams) installation:

#### Option A: Global Installation

Install the skill globally so it's available across all projects:

```bash
# Clone the repository
git clone https://github.com/bar181/aisp-open-core.git

# Copy skill to global skills directory
cp -r aisp-open-core/skills/init-aisp-specs ~/.claude/skills/

# Clean up (optional)
rm -rf aisp-open-core
```

#### Option B: Project-Specific Installation (Best for Teams)

Install the skill for a specific project only:

```bash
# Navigate to your project
cd /path/to/your-project

# Clone the repository
git clone https://github.com/bar181/aisp-open-core.git

# Create .claude/skills directory if it doesn't exist
mkdir -p .claude/skills

# Copy skill to project
cp -r aisp-open-core/skills/init-aisp-specs .claude/skills/

# Clean up
rm -rf aisp-open-core

# Commit to version control (optional but recommended for teams)
git add .claude/skills/init-aisp-specs
git commit -m "Add init-aisp-specs skill"
```

**Benefits of project-specific installation:**
- Team members automatically get the skill when they clone the repo
- Skill is version-controlled alongside your project
- No need for individual team members to install separately

---

### Method 3: Direct Download

1. Download the skill folder from GitHub: [skills/init-aisp-specs](https://github.com/bar181/aisp-open-core/tree/main/skills/init-aisp-specs)

2. Copy to one of these locations:
   - **Global:** `~/.claude/skills/init-aisp-specs/`
   - **Project:** `your-project/.claude/skills/init-aisp-specs/`

3. Ensure the directory structure looks like:
   ```
   .claude/skills/init-aisp-specs/
   ├── SKILL.md
   ├── aisp-spec.md
   ├── minimal-template.md
   ├── symbol-quick-ref.md
   └── README.md
   ```

---

## Verification

After installation, verify the skill is loaded:

1. Open Claude Code in any project
2. Ask: "What skills are available?"
3. You should see `init-aisp-specs` in the list

Or test it directly:
```
Initialize AISP specs for this repo
```

---

## Usage

Once installed, simply ask Claude Code:

```
"Initialize AISP specs for this repo"
```

or

```
"Set up AISP documentation"
```

The skill will guide you through a 5-phase interactive workflow to create high-density (δ≥0.80) AISP specifications.

---

## Troubleshooting

### Skill not found

1. **Check installation location:**
   ```bash
   # Global
   ls ~/.claude/skills/init-aisp-specs/SKILL.md

   # Project
   ls .claude/skills/init-aisp-specs/SKILL.md
   ```

2. **Verify SKILL.md exists:** The file must be named exactly `SKILL.md` (case-sensitive)

3. **Restart Claude Code:** Close and reopen Claude Code to reload skills

### Skill not activating

- Make sure you explicitly mention the skill or ask to "initialize AISP specs"
- Claude Code skills activate based on the `description` field in SKILL.md

### Permission issues

```bash
# Fix permissions if needed
chmod -R 755 ~/.claude/skills/init-aisp-specs
```

---

## Uninstallation

### Global installation:
```bash
rm -rf ~/.claude/skills/init-aisp-specs
```

### Project installation:
```bash
rm -rf .claude/skills/init-aisp-specs
```

### Marketplace installation:
```bash
/plugin uninstall init-aisp-specs
```

---

## Updates

### Marketplace installation:
```bash
/plugin update init-aisp-specs
```

### Manual installation:
```bash
# Re-download the repo and copy the updated skill folder
git clone https://github.com/bar181/aisp-open-core.git
cp -r aisp-open-core/skills/init-aisp-specs ~/.claude/skills/
# Or to project: cp -r aisp-open-core/skills/init-aisp-specs .claude/skills/
rm -rf aisp-open-core
```

---

## Support

- **Documentation:** [GitHub - aisp-open-core](https://github.com/bar181/aisp-open-core)
- **Issues:** [Report an issue](https://github.com/bar181/aisp-open-core/issues)
- **AISP Specification:** [AI_GUIDE.md](https://github.com/bar181/aisp-open-core/blob/main/AI_GUIDE.md)

---

## What's Next?

After installation:
1. Try the skill in a sample project
2. Review the generated specs
3. Share with your team (if using project-specific installation)
4. Explore AISP notation in the generated files

**Coming Soon:**
- `update-specs` skill - Keep specs in sync with code changes
- `validate-aisp` skill - Check spec quality and compliance
