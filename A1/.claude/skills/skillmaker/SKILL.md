---
name: skillmaker
description: Create Claude skills according to official documentation with proper structure and best practices
---

# Skillmaker

Instructions for creating Claude skills that follow official documentation and best practices.

## Instructions

When creating a skill, follow these steps:

### 1. Directory Structure
Create the basic skill directory structure:
```
.claude/skills/[skill-name]/
├── SKILL.md              # Main instructions (required)
├── REFERENCE.md          # Detailed API reference (optional)
├── EXAMPLES.md           # Usage examples (optional)
└── scripts/              # Executable scripts (optional)
    ├── utility.py
    ├── helper.sh
    └── [other scripts]
```

### 2. SKILL.md Requirements

#### Required YAML Frontmatter
```yaml
---
name: your-skill-name
description: Brief description of what this Skill does and when to use it
---
```

**Name Requirements:**
- Maximum 64 characters
- Lowercase letters, numbers, and hyphens only
- No XML tags or reserved words ("anthropic", "claude")
- Use gerund form (e.g., "processing-pdfs", "analyzing-spreadsheets")

**Description Requirements:**
- Maximum 1024 characters
- No XML tags
- Include both what the Skill does and when to use it
- Write in third person

#### Required Markdown Structure
```markdown
# Your Skill Name

## Instructions
[Clear, step-by-step guidance for Claude to follow]

## Examples
[Concrete examples of using this Skill]
```

### 3. Content Best Practices

#### Keep SKILL.md Concise
- Keep under 500 lines
- Only include essential information
- Use progressive disclosure for additional content

#### Use Appropriate Freedom Levels
- **High**: Text-based instructions for flexible tasks
- **Medium**: Pseudocode for tasks with preferred patterns
- **Low**: Specific scripts for fragile operations

#### Include Clear Examples
- Provide concrete examples, not abstract descriptions
- Show input/output pairs when possible
- Include common use cases

### 4. Script Development Guidelines

#### When to Use Scripts
- Deterministic operations that need consistency
- Error-prone processes that need validation
- Complex workflows with multiple steps
- Performance-critical tasks

#### Script Best Practices
```python
# HTTP requests typically complete within 30 seconds
REQUEST_TIMEOUT = 30

def process_file(path):
    """Process a file, creating it if it doesn't exist."""
    try:
        with open(path) as f:
            return f.read()
    except FileNotFoundError:
        print(f"File {path} not found, creating default")
        with open(path, 'w') as f:
            f.write('')
        return ''
```

**Key Points:**
- Handle errors explicitly
- Document constants
- Use forward slashes in paths (cross-platform)
- Provide clear error messages

### 5. Security Considerations

#### Critical Security Practices
- Only create skills from trusted sources
- Review all bundled files thoroughly
- Be cautious with external URLs
- Treat skills like software - audit before use

#### What to Audit For
- Unexpected network calls
- Unusual file access patterns
- Operations that don't match the stated purpose
- Potential data exfiltration risks

### 6. Development Workflow

#### Recommended Process
1. **Identify gaps** - Run tasks without skills, document missing context
2. **Create evaluations** - Build test scenarios before extensive documentation
3. **Write minimal instructions** - Address identified gaps
4. **Iterate with Claude** - Use one instance to help create, another to test
5. **Observe usage patterns** - Refine based on real-world usage

## Examples

### Example 1: PDF Processing Skill
```yaml
---
name: processing-pdfs
description: Extract text, images, and metadata from PDF files
---
```

### Example 2: Data Analysis Skill
```yaml
---
name: analyzing-spreadsheets
description: Analyze Excel and CSV files with statistical functions and visualizations
---
```

### Example 3: Image Processing Skill
```yaml
---
name: editing-images
description: Resize, crop, filter, and format images using various libraries
---
```

## Troubleshooting

### Common Issues and Solutions

#### Skills Not Found
1. Check `.claude/skills/` directory exists in project or user home
2. Verify `SKILL.md` has proper YAML frontmatter
3. Ensure name follows naming conventions

#### Skills Not Being Used
1. Check description specificity and keywords
2. Verify skill matches request context
3. Ensure instructions are clear and actionable

#### Performance Issues
1. Keep SKILL.md under 500 lines
2. Use progressive disclosure for large content
3. Structure files for efficient navigation

## Resources

- [Claude Skills Overview](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview)
- [Claude Code Skills Documentation](https://code.claude.com/docs/en/skills)
- [Best Practices Guide](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/best-practices)
- [Agent SDK Skills Integration](https://platform.claude.com/docs/en/agent-sdk/skills)