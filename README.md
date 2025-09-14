# PR Compliance Templates

A comprehensive repository of PR compliance checklist templates organized by programming languages and technology stacks for automated code review systems.

See the latest and most detailed instructions in the [Qodo Merge documentation](https://qodo-merge-docs.qodo.ai/tools/compliance/).

## Overview

This repository provides production-ready `pr_compliance_checklist.yaml` templates designed to implement intelligent code review automation. Each compliance checklist is carefully crafted to focus on high-value reviews that require contextual understanding beyond what automated linting tools can provide.

**Important**: These templates should be reviewed, customized, and approved by your organization before deployment. Teams will need to commit the finalized compliance files to their repositories.

## Deployment Checklist

- [ ] **Identify repository mapping** strategy (local vs. hierarchical)
- [ ] **Select relevant language templates** for your tech stack
- [ ] **Customize compliance items** for your specific requirements
- [ ] **Configure metadata.yaml** for hierarchical setup
- [ ] **Test with sample PRs** to validate compliance detection
- [ ] **Train development teams** on compliance requirements
- [ ] **Establish review processes** for compliance violations
- [ ] **Monitor and iterate** on compliance effectiveness

## Repository Structure

```
├── codebase_standards/
│   ├── global/                           # Universal compliance rules
│   │   └── pr_compliance_checklist.yaml
│   └── groups/                           # Technology-specific compliance
│       ├── back-end/
│       ├── cpp/
│       ├── csharp/
│       ├── dart/
│       ├── dockerfile/
│       ├── front-end/
│       ├── go/
│       ├── javascript/
│       ├── kotlin/
│       ├── php/
│       ├── python/
│       ├── ruby/
│       ├── rush/
│       ├── scala/
│       ├── swift/
│       └── typescript/
└── metadata.yaml                         # Example repository mapping configuration
```

## Compliance Philosophy

### What These Templates Cover
- **Architecture patterns** and best practices specific to each technology
- **Performance considerations** that impact user experience
- **Maintainability issues** that automated tools cannot detect
- **Framework-specific pitfalls** and anti-patterns
- **Security vulnerabilities** that require contextual analysis

### What These Templates Don't Cover
- **Basic linting** (formatting, style rules) - handled by existing tools
- **Simple syntax errors** - caught by compilers/interpreters
- **Import organization** - automated by IDEs and linters

## Quick Start

### Deployment

#### Option 1: Local Repository Setup
Place `pr_compliance_checklist.yaml` in your repository root or within a `codebase_standards` folder:
```bash
# Option A: Repository root
your-repo/
└── pr_compliance_checklist.yaml

# Option B: Codebase standards folder
your-repo/
└── codebase_standards/
    └── your-repo/
        └── pr_compliance_checklist.yaml
```

#### Option 2: Global Hierarchical Setup
Create a centralized `pr-agent-settings` repository in your organization:

```bash
pr-agent-settings/
├── metadata.yaml
└── codebase_standards/
    ├── global/
    │   └── pr_compliance_checklist.yaml
    └── groups/
        ├── frontend_repos/
        ├── backend_repos/
        ├── python_repos/
        └── [your-custom-groups]/
```

Update `metadata.yaml` to map repositories to compliance paths (this is an example configuration):
```yaml
# Backend Python service
my-api-service:
  pr_compliance_checklist_paths:
    - "groups/python"
    - "groups/backend_repos"

# Frontend React application
my-web-app:
  pr_compliance_checklist_paths:
    - "groups/javascript"
    - "groups/front-end"

# Monorepo with multiple services
my-monorepo:
  pr_compliance_checklist_paths:
    - "my-monorepo"
  monorepo_subprojects:
    api-service:
      pr_compliance_checklist_paths:
        - "groups/python"
    web-client:
      pr_compliance_checklist_paths:
        - "groups/typescript"
        - "groups/frontend_repos"
```

## Customization Guidelines

### Adding Custom Compliance Items

Each compliance item should include:

```yaml
pr_compliances:
  - title: "Descriptive Title"
    compliance_label: true  # or false - determines if labels are applied
    objective: "Clear description of what this compliance aims to achieve"
    success_criteria: "Specific conditions for compliance"
    failure_criteria: "Specific conditions for non-compliance"
```

### Best Practices for Writing Compliance Items

1. **Be Specific**: Avoid subjective criteria that are hard to verify
2. **Focus on Impact**: Prioritize security, business requirements, and critical standards
3. **Use Clear Language**: Developers should understand exactly what's expected
4. **Avoid Style Preferences**: Focus on meaningful requirements, not formatting
5. **Consider Context**: Leverage what an LLM can understand that automated tools cannot

## Support and Customization

This repository serves as a starting point for automated PR compliance. Each organization should:

1. **Evaluate templates** against their specific coding standards
2. **Add custom compliance items** relevant to their domain
3. **Remove or modify** items that don't align with their practices
4. **Establish governance** around compliance updates and maintenance

## Contributing

When adding new compliance templates:
- Focus on issues that require contextual understanding
- Provide clear success/failure criteria
- Test with real-world code examples
- Document the rationale for each compliance item
