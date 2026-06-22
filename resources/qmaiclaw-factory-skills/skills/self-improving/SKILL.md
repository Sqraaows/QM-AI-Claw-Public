## Self-Improving + Proactive Agent

**Source**: https://clawhub.ai/ivangdavila/self-improving

Self-reflection + Self-criticism + Self-learning + Self-organizing memory. Agent evaluates its own work, catches mistakes, and improves permanently.

### When to Use

- User corrects you or points out mistakes
- You complete significant work and want to evaluate the outcome
- You notice something in your own output that could be better
- Knowledge should compound over time without manual maintenance

### Architecture

Memory lives in `~/self-improving/` with tiered structure:

```
~/self-improving/
├── memory.md          # HOT: ≤100 lines, always loaded
├── index.md          # Topic index with line counts
├── heartbeat-state.md # Heartbeat state
├── projects/         # Per-project learnings
├── domains/          # Domain-specific (code, writing, comms)
├── archive/           # COLD: decayed patterns
└── corrections.md    # Last 50 corrections log
```

### Learning Signals

**Log automatically when you notice these patterns:**

Corrections → add to `corrections.md`:
- "No, that's not right..."
- "Actually, it should be..."
- "You're wrong about..."
- "I prefer X, not Y"
- "Remember that I always..."
- "I told you before..."
- "Stop doing X"
- "Why do you keep..."

Preference signals → add to `memory.md`:
- "I like when you..."
- "Always do X for me"
- "Never do Y"
- "My style is..."

Pattern candidates → track, promote after 3x:
- Same instruction repeated 3+ times
- Workflow that works well repeatedly
- User praises specific approach

### Self-Reflection

After completing significant work, pause and evaluate:
- Did it meet expectations?
- What could be better?
- Is this a pattern?

Log format:
```
CONTEXT: [type of task]
REFLECTION: [what I noticed]
LESSON: [what to do differently]
```

### Tiered Storage

| Tier | Location | Size Limit | Behavior |
|------|----------|------------|----------|
| HOT | memory.md | ≤100 lines | Always loaded |
| WARM | projects/, domains/ | ≤200 lines each | Load on context match |
| COLD | archive/ | Unlimited | Load on explicit query |

### Core Rules

1. **Learn from corrections** - Log when user corrects you
2. **Tiered storage** - HOT/WARM/COLD separation
3. **Promotion/Demotion** - 3x in 7 days → promote to HOT; 30 days unused → demote
4. **Namespace isolation** - Project patterns stay in projects/
5. **Conflict resolution** - Most specific wins (project > domain > global)
6. **Compaction** - Merge/summarize, never delete without asking
7. **Transparency** - Cite source: "Using X (from projects/foo.md:12)"
8. **Security** - Never store credentials or health data
9. **Graceful degradation** - If context limit hit, load only HOT

### Quick Queries

| User says | Action |
|-----------|--------|
| "What do you know about X?" | Search all tiers |
| "What have you learned?" | Show last 10 from corrections.md |
| "Show my patterns" | List memory.md (HOT) |
| "Show [project] patterns" | Load projects/{name}.md |
| "Memory stats" | Show counts per tier |
| "Forget X" | Remove from all tiers (confirm first) |
| "Export memory" | ZIP all files |

### Memory Stats

On "memory stats" request, report:
```
📊 Self-Improving Memory

HOT (always loaded):
  memory.md: X entries

WARM (load on demand):
  projects/: X files
  domains/: X files

COLD (archived):
  archive/: X files

Recent activity (7 days):
  Corrections logged: X
  Promotions to HOT: X
  Demotions to WARM: X
```

### Common Traps

| Trap | Why It Fails | Better Move |
|------|-------------|-------------|
| Learning from silence | Creates false rules | Wait for explicit correction |
| Promoting too fast | Pollutes HOT memory | Keep tentative until repeated |
| Reading every namespace | Wastes context | Load only HOT + matching |
| Compaction by deletion | Loses trust and history | Merge, summarize, or demote |

### Data Storage

Local state in `~/self-improving/`:
- `memory.md` - HOT rules and confirmed preferences
- `corrections.md` - Explicit corrections and reusable lessons
- `projects/` and `domains/` - Scoped patterns
- `archive/` - Decayed or inactive patterns
- `heartbeat-state.md` - Maintenance markers

### Requirements

- No credentials required
- No extra binaries required
- Network access optional (for related skills)

---

*Install date: 2026-04-27*
