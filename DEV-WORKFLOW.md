# Amplifier Development Workflow

> Simple guide to using Amplifier with your projects

## 📊 How Amplifier Works with Your Projects

```
Your Projects Directory              Amplifier Directory
━━━━━━━━━━━━━━━━━━━━━━              ━━━━━━━━━━━━━━━━━━━━━━

~/repos/                             ~/repos/amplifier/
├── evolve/          ────────────┐   ├── amplifier/          (Core toolkit)
│   ├── apps/                    │   │   ├── memory/         • Persistent memory
│   ├── packages/                │   │   ├── knowledge/      • Knowledge graphs
│   └── docs/                    │   │   └── ccsdk_toolkit/  • SDK tools
│                                │   │
├── my-saas/         ────────────┤   ├── .claude/            (Specialized agents)
│   ├── src/                     │   │   └── AGENTS_CATALOG.md
│   └── tests/                   │   │
│                                │   ├── ai_working/         (Your workspace)
├── mobile-app/      ────────────┤   │   ├── evolve/    ──────┘ Symlinks to
│   ├── ios/                     │   │   ├── my-saas/  ────────┘ your real
│   └── android/                 │   │   └── mobile-app/ ───────┘ projects
│                                │   │
└── data-pipeline/   ────────────┘   ├── .data/              (Runtime data)
    ├── pipelines/                   │   ├── memory.json
    └── models/                      │   ├── knowledge/
                                     │   └── transcripts/
                                     │
    YOUR REAL CODE                   └── scenarios/          (Custom tools)
    (never moves!)                       └── your-tools/
```

## 🎯 Core Concept

**Amplifier is a workspace where you work ON your projects, not a dependency you add TO your projects.**

- ✅ Your code stays in `/home/umer/repos/evolve`
- ✅ You work FROM `/home/umer/repos/amplifier`
- ✅ Symlinks connect them
- ✅ Changes appear in your real project instantly

## 🚀 Quick Setup (One-Time)

### 1. Install Amplifier

```bash
cd ~/repos/amplifier
make install
```

### 2. Link Your Projects

```bash
# Link each project you want to work on
cd ~/repos/amplifier/ai_working

# Evolve (already done)
ln -s /home/umer/repos/evolve evolve

# Add your other projects
ln -s /home/umer/repos/my-saas my-saas
ln -s /home/umer/repos/mobile-app mobile-app
ln -s /home/umer/repos/data-pipeline data-pipeline
```

### 3. Verify Setup

```bash
ls -la ai_working/
# Should show:
# evolve -> /home/umer/repos/evolve
# my-saas -> /home/umer/repos/my-saas
# mobile-app -> /home/umer/repos/mobile-app
# data-pipeline -> /home/umer/repos/data-pipeline
```

## 📋 Daily Workflows

### Workflow 1: Normal Development (Quick Tasks)

```bash
# Work directly from your project
cd ~/repos/evolve
code .
claude

# Do normal development
# No Amplifier features, but faster for simple tasks
```

**Use for:**
- Quick bug fixes
- Normal feature development
- Running tests
- Git operations

---

### Workflow 2: Amplifier-Powered Development (Complex Tasks)

```bash
# Work from Amplifier with full power
cd ~/repos/amplifier
code ~/repos/evolve  # Open project in editor
claude               # Start Claude Code from Amplifier

# In Claude Code:
"I'm working on ai_working/evolve..."
```

**Use for:**
- Architecture reviews
- Security audits
- Complex debugging
- Design decisions
- Multi-project work

---

### Workflow 3: Multi-Project Work

```bash
cd ~/repos/amplifier
claude

# In Claude Code:
"I'm working on ai_working/evolve and ai_working/my-saas.

Extract the authentication pattern from evolve/packages/auth
and adapt it for my-saas/src/auth."
```

**Use for:**
- Sharing code between projects
- Applying patterns across projects
- Learning from one project to improve another

---

## 🎓 Complete Examples

### Example 1: Evolve - Add HIPAA Audit Logging

```bash
# Step 1: Start from Amplifier
cd ~/repos/amplifier
claude

# Step 2: Query existing knowledge
"Query the knowledge base about HIPAA compliance requirements"

# Step 3: Use specialized agents
"I'm working on ai_working/evolve.

Use the zen-architect agent to design a HIPAA-compliant audit logging
system for patient data access.

Then use the security-guardian agent to review it."

# Step 4: Implement
"Implement the audit logging system in ai_working/evolve/packages/audit-logger/
with full tests and documentation."

# Step 5: Verify in real project
cd ~/repos/evolve
pnpm test:coverage
git status  # See the new files
git add packages/audit-logger
git commit -m "feat: add HIPAA audit logging"
```

---

### Example 2: My-SaaS - Learn from Evolve's Multi-Tenant Pattern

```bash
cd ~/repos/amplifier
claude

# In Claude Code:
"I'm working on ai_working/my-saas.

1. Analyze the multi-tenant architecture in ai_working/evolve
2. Extract the key patterns
3. Create a simplified version for ai_working/my-saas
4. Document the differences and tradeoffs"
```

---

### Example 3: Mobile-App - Security Review Before Launch

```bash
cd ~/repos/amplifier
claude

# In Claude Code:
"I'm deploying ai_working/mobile-app to production tomorrow.

Use the security-guardian agent to:
1. Review authentication flows
2. Check API security
3. Audit data storage
4. Verify encryption usage

Then use test-coverage to ensure critical paths have tests."
```

---

### Example 4: Data-Pipeline - Parallel Experimentation

```bash
cd ~/repos/amplifier/ai_working/data-pipeline

# Try two different approaches simultaneously
make worktree feature-spark-pipeline
make worktree feature-airflow-pipeline

# Develop in parallel
cd ../../feature-spark-pipeline/data-pipeline
# Work on Spark approach

cd ../../feature-airflow-pipeline/data-pipeline
# Work on Airflow approach

# Compare results
make worktree-list

# Keep winner, delete loser
make worktree-rm feature-airflow-pipeline
```

---

## 🔍 Knowledge Synthesis (Powerful Feature)

### Extract Knowledge from Project Docs

```bash
# One-time setup per project
export AMPLIFIER_CONTENT_DIRS="/home/umer/repos/evolve/docs:/home/umer/repos/my-saas/docs"
make knowledge-update

# Query anytime
make knowledge-query Q="authentication patterns"
make knowledge-query Q="database schema design"
make knowledge-query Q="API rate limiting"

# Visualize knowledge graph
make knowledge-graph-viz
```

### What This Does

- 📚 Reads all your documentation
- 🧠 Extracts concepts, relationships, patterns
- 🔍 Creates searchable knowledge base
- 📊 Builds interactive graph visualization
- 💡 Finds connections across projects

---

## 🤖 Using Specialized Agents

Amplifier has 20+ specialized agents. Use them like this:

```bash
cd ~/repos/amplifier
claude

# In Claude Code:
"I'm working on ai_working/[project-name].

Use the [agent-name] agent to [task]"
```

### Most Useful Agents

| Agent | Use For | Example |
|-------|---------|---------|
| **security-guardian** | Security audits | "Review authentication for vulnerabilities" |
| **bug-hunter** | Complex debugging | "Find why API timeouts occur intermittently" |
| **test-coverage** | Test analysis | "Identify critical test gaps" |
| **zen-architect** | Architecture design | "Design a caching layer following simplicity principles" |
| **performance-optimizer** | Speed issues | "Profile and optimize slow endpoints" |
| **database-architect** | Database design | "Review schema and suggest optimizations" |

See all agents: `cat .claude/AGENTS_CATALOG.md`

---

## 📁 Project Structure Template

For best results, organize your projects like this:

```
your-project/
├── CLAUDE.md              # Project-specific AI instructions
├── DISCOVERIES.md         # Solutions to non-obvious problems
├── docs/                  # Documentation (for knowledge synthesis)
│   ├── architecture/
│   ├── guides/
│   └── reference/
├── src/                   # Your code
└── tests/                 # Your tests
```

**Create CLAUDE.md in each project:**

```markdown
# Project Name

## Build Commands
- Run dev: `npm run dev`
- Run tests: `npm test`
- Build: `npm run build`

## Tech Stack
- Framework: Next.js 14
- Database: PostgreSQL
- Auth: Auth0

## Key Patterns
- Use React Server Components by default
- API routes in app/api/
- Database queries via Prisma ORM

## Testing Requirements
- 80% coverage minimum
- E2E tests for critical flows
```

---

## ⚡ Quick Command Reference

```bash
# Setup
make install                        # Install dependencies

# Knowledge Management
make knowledge-update               # Extract from all docs
make knowledge-query Q="topic"      # Search knowledge base
make knowledge-graph-viz            # Visualize graph

# Parallel Development
make worktree feature-name          # Create experimental branch
make worktree-list                  # List all worktrees
make worktree-rm feature-name       # Remove worktree

# Quality
make check                          # Lint, format, type-check
make test                           # Run all tests
```

---

## 🎯 When to Use What

### Use Normal Workflow (from project directory)
- ✅ Quick bug fixes
- ✅ Normal feature development
- ✅ Running project-specific commands
- ✅ Standard git operations

### Use Amplifier Workflow (from amplifier directory)
- ✅ Architecture decisions
- ✅ Security reviews
- ✅ Complex debugging
- ✅ Multi-project work
- ✅ Learning from documentation
- ✅ Trying parallel approaches

---

## 🔄 Switching Between Projects

```bash
# Working on Evolve
cd ~/repos/amplifier
claude
"I'm working on ai_working/evolve..."

# Switch to My-SaaS (same session)
"Now I'm working on ai_working/my-saas..."

# Work on both simultaneously
"I'm working on ai_working/evolve and ai_working/my-saas.
Extract pattern X from evolve and apply it to my-saas."
```

---

## 💡 Pro Tips

### 1. **Knowledge Synthesis is Your Superpower**
Run `make knowledge-update` regularly to build a queryable knowledge base of all your documentation.

### 2. **Use Agents Proactively**
Don't wait for problems. Use security-guardian before deploys, test-coverage after features, etc.

### 3. **Create Project-Specific CLAUDE.md**
Tell AI about your project's conventions, commands, and patterns.

### 4. **Try Parallel Worktrees**
When unsure about an approach, try 2-3 variants in parallel and compare results.

### 5. **Cross-Project Learning**
Use Amplifier to extract patterns from one project and adapt them for others.

### 6. **Session Transcripts**
Amplifier auto-saves conversation transcripts. Use `/transcripts` to restore context.

---

## 🆘 Common Questions

**Q: Do my files move to Amplifier?**
A: No! They stay in your project. Symlinks just create a "window" into your project.

**Q: Can I still use git normally?**
A: Yes! Git operations work in your project directory as always.

**Q: Do I need to activate virtual environment?**
A: No! `make` commands and Claude Code handle it automatically.

**Q: Can I work on multiple projects at once?**
A: Yes! Link them all in `ai_working/` and switch between them.

**Q: What if I don't want Amplifier features?**
A: Just work from your project directory normally. No Amplifier required.

---

## 📚 Next Steps

1. **Link your projects** - `ln -s ~/repos/my-project ai_working/my-project`
2. **Synthesize knowledge** - `make knowledge-update`
3. **Try one agent** - Use security-guardian or test-coverage
4. **Read agent catalog** - `cat .claude/AGENTS_CATALOG.md`
5. **Create custom tools** - See `scenarios/` for examples

---

**Remember:** Amplifier is a force multiplier, not a requirement. Use it when it helps, work normally when it doesn't. 🚀
