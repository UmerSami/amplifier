# Using Amplifier with Evolve Healthcare Platform

## 🔗 Setup Complete

Your Evolve project is linked at: `ai_working/evolve/` → `/home/umer/repos/evolve`

## 🚀 Quick Start Workflows

### 1. Knowledge Synthesis (Do This First!)

Extract knowledge from Evolve's extensive documentation:

```bash
# From amplifier directory
export AMPLIFIER_CONTENT_DIRS="/home/umer/repos/evolve/docs:/home/umer/repos/evolve"
make knowledge-update

# Query your architecture
make knowledge-query Q="multi-tenant architecture"
make knowledge-query Q="CMS implementation strategy"
make knowledge-query Q="AWS Cognito authentication"
make knowledge-query Q="HIPAA compliance requirements"
make knowledge-query Q="Payload CMS integration"
```

**What this gives you:**
- Queryable knowledge graph of your entire architecture
- Semantic search across all documentation
- Relationship mapping between concepts
- Productive tension detection (conflicting approaches)

### 2. Working FROM Amplifier

```bash
cd /home/umer/repos/amplifier
claude

# In Claude Code:
"I'm working on ai_working/evolve. Use the security-guardian agent
to review the authentication implementation in packages/auth for
HIPAA compliance issues."
```

**Available Specialized Agents for Evolve:**

- **security-guardian** - HIPAA compliance, AWS Cognito security review
- **test-coverage** - Analyze test gaps, suggest test cases
- **performance-optimizer** - Identify bottlenecks in Next.js apps
- **bug-hunter** - Systematic debugging of issues
- **zen-architect** - Design reviews following simplicity principles
- **api-contract-designer** - Review/design API contracts
- **database-architect** - MongoDB schema optimization
- **integration-specialist** - Review AWS Cognito, Payload CMS integrations

### 3. Parallel Feature Development

Try multiple approaches simultaneously:

```bash
# From amplifier directory
cd ai_working/evolve

# Create parallel worktrees
make worktree feature-cognito-mfa
make worktree feature-sms-verification

# Work on both
cd ../../feature-cognito-mfa/evolve
pnpm test:coverage

cd ../../feature-sms-verification/evolve
pnpm test:coverage

# Compare and choose winner
make worktree-list
make worktree-rm feature-sms-verification
```

### 4. Build Custom Tools for Evolve

Create Amplifier-powered CLI tools for Evolve-specific tasks:

```bash
cd scenarios
mkdir evolve-tools

# Example tools you could build:
# - HIPAA compliance checker
# - Multi-tenant data isolation validator
# - Audit log generator
# - Patient data encryption validator
```

## 🎯 Common Use Cases

### Architecture Review
```
"Use zen-architect to analyze ai_working/evolve/apps/web and suggest
improvements following Amplifier's ruthless simplicity philosophy."
```

### Security Audit
```
"Deploy security-guardian to review ai_working/evolve/packages/auth.
Focus on:
1. AWS Cognito integration security
2. HIPAA compliance gaps
3. Patient data handling
4. Multi-tenant data isolation"
```

### Test Coverage Analysis
```
"Use test-coverage agent to analyze ai_working/evolve/apps/web and
identify critical test gaps. Current coverage requirement is 70%."
```

### Performance Optimization
```
"Deploy performance-optimizer to profile ai_working/evolve/apps/web.
Focus on:
1. Next.js App Router performance
2. Database query optimization
3. MongoDB connection pooling
4. API endpoint response times"
```

### Database Design
```
"Use database-architect to review the MongoDB schema in
ai_working/evolve for:
1. Multi-tenant data isolation
2. Query performance
3. Index optimization
4. HIPAA audit requirements"
```

## 🔄 Development Workflow

### Daily Development
```bash
# 1. Start from Amplifier
cd /home/umer/repos/amplifier

# 2. Use Claude Code with both contexts
claude

# 3. Work on Evolve with Amplifier support
"I'm working on ai_working/evolve..."
```

### Feature Development
```bash
# 1. Create worktree for experimentation
cd ai_working/evolve
make worktree feature-new-auth-flow

# 2. Develop in worktree
cd ../../feature-new-auth-flow/evolve
pnpm dev:web

# 3. Use Evolve's commands (from its CLAUDE.md)
pnpm test:coverage
pnpm test:e2e

# 4. Merge or discard
make worktree-rm feature-new-auth-flow  # Or merge to main
```

### Knowledge Management
```bash
# When you add new documentation
export AMPLIFIER_CONTENT_DIRS="/home/umer/repos/evolve/docs"
make knowledge-update

# Query when you need context
make knowledge-query Q="your architecture question"

# Visualize knowledge graph
make knowledge-graph-viz
```

## 📊 Integration Benefits

### What Amplifier Adds to Evolve

1. **Persistent Memory**
   - Remembers architectural decisions
   - Tracks patterns across sessions
   - Never repeat explanations

2. **Knowledge Synthesis**
   - Queryable documentation
   - Concept relationship mapping
   - Semantic search across 200+ pages of docs

3. **Specialized Agents**
   - Security reviews (HIPAA compliance)
   - Performance optimization
   - Test coverage analysis
   - Architecture design

4. **Parallel Exploration**
   - Try multiple approaches simultaneously
   - Compare results before committing
   - Reduce risk of bad decisions

5. **Session Continuity**
   - Auto-saved transcripts
   - Resume conversations
   - Never lose context

### What Evolve Provides

1. **Project-Specific Commands**
   - `pnpm dev`, `pnpm test`, etc.
   - TurboRepo workspace commands
   - Testing and coverage scripts

2. **Architecture Context**
   - Multi-tenant patterns
   - AWS Cognito setup
   - Payload CMS integration
   - Healthcare domain knowledge

3. **Development Standards**
   - Testing requirements (70% coverage)
   - Code quality standards
   - Component patterns

## 🎓 Learning Resources

**Amplifier Documentation:**
- `/home/umer/repos/amplifier/README.md` - Overview
- `/home/umer/repos/amplifier/docs/THIS_IS_THE_WAY.md` - Best practices
- `/home/umer/repos/amplifier/.claude/AGENTS_CATALOG.md` - All agents

**Evolve Documentation:**
- `/home/umer/repos/evolve/README.md` - Project overview
- `/home/umer/repos/evolve/docs/` - Architecture docs
- `/home/umer/repos/evolve/CLAUDE.md` - Development guide

## 💡 Pro Tips

1. **Always start from Amplifier directory** to access both contexts
2. **Synthesize knowledge first** - Makes everything else more effective
3. **Use agents proactively** - Don't wait for problems
4. **Create worktrees for experiments** - Parallel development is powerful
5. **Query knowledge frequently** - Faster than reading docs manually

## 🚨 Common Patterns

### Before Making Architectural Changes
```
"Query the knowledge base about multi-tenant architecture patterns,
then use zen-architect to design the change, and finally have
security-guardian review it for HIPAA compliance."
```

### Before Deployment
```
"Use security-guardian to audit ai_working/evolve for:
1. HIPAA compliance violations
2. Security vulnerabilities
3. Data exposure risks
Then use test-coverage to ensure critical paths are tested."
```

### When Debugging Complex Issues
```
"Deploy bug-hunter to investigate the authentication timeout issue
in ai_working/evolve/packages/auth. Focus on AWS Cognito token
refresh logic."
```

---

**Next Steps:**
1. Run knowledge synthesis: `/tmp/evolve-knowledge-setup.sh`
2. Try a security review: Use security-guardian on packages/auth
3. Analyze test coverage: Use test-coverage agent
4. Explore your knowledge graph: `make knowledge-graph-viz`
