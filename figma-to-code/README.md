# Figma to Code - Claude Code Skill

A Claude Code skill that generates production-ready React/Next.js code from Figma designs with systematic workflows, component reuse strategies, and Figma variant mapping.

## Features

- **Systematic Figma MCP Tool Usage**: Enforces proper metadata → context → screenshot → variables workflow
- **Component Reuse First**: Prioritizes using existing components over creating new ones
- **Variant Mapping**: Automatically maps Figma variant properties to code props
- **Frontend-Only Focus**: Maintains strict boundaries between frontend and backend code
- **Type-Safe**: Generates TypeScript components with proper typing
- **Accessible**: Includes ARIA attributes and semantic HTML
- **Mock Data Support**: Implements frontend with mock data when backend APIs are needed

## Prerequisites

- Claude Code CLI installed
- Figma MCP Server installed ([installation guide](https://developers.figma.com/docs/figma-mcp-server))
- Figma Desktop app running
- React/Next.js project (or compatible framework)

## Installation

1. Clone or download this repository to your local machine

2. Copy the `figma-to-code` directory to your Claude Code skills directory:
   ```bash
   # macOS/Linux
   cp -r figma-to-code ~/.claude-code/skills/

   # Windows
   xcopy figma-to-code %USERPROFILE%\.claude-code\skills\figma-to-code\ /E /I
   ```

3. Restart Claude Code

## Configuration

Before using this skill, you need to customize it for your project. Open `SKILL.md` and `examples.md` and replace all placeholders with your project-specific values.

**💡 Tip:** You can use Claude Code itself to help replace placeholders and adjust these files to match your codebase! Simply ask Claude Code to "replace all placeholders in SKILL.md and examples.md with my project's implementation details" after installing the skill.

### Required Placeholders to Replace

- **`[FRONTEND_DIR]`** - Your frontend directory path
  - Examples: `src`, `app`, `frontend`, `client`, `web`

- **`[BACKEND_DIR]`** - Your backend directory path
  - Examples: `server`, `backend`, `api`, `services`

- **`[COMPONENTS_DIR]`** - Your components directory
  - Examples: `components`, `src/components`, `app/components`

- **`[PAGES_DIR]`** - Your pages/routes directory
  - Examples: `app`, `pages`, `src/pages`, `src/app`

- **`[TYPES_DIR]`** - Your TypeScript types directory
  - Examples: `types`, `@/types`, `src/types`

- **`[API_MODULE]`** - Your API module naming pattern
  - Examples: `modules/products`, `api/products`, `services/products`

### Styling System Placeholders

Replace these based on your styling approach (Tailwind, CSS Modules, styled-components, etc.):

- **`[STYLING_UTILITY]`** - Your styling utility function
  - Examples: `cn`, `classNames`, `clsx`

- **`[UTILITY_PATH]`** - Path to your utility functions
  - Examples: `@/lib/utils`, `~/utils`, `../utils`

- **`[VARIANT_SYSTEM_IMPLEMENTATION]`** - Your variant/styling system
  - Examples: CVA (class-variance-authority), styled-components variants, etc.

- **`[APPLY_STYLES_BASED_ON_VARIANTS]`** - How you apply conditional styles
  - Example: `cn(baseClass, variants[variant])` for Tailwind

- **`[RESPONSIVE_LAYOUT_CLASSES]`** - Your responsive utility classes
  - Example: `"flex flex-col md:flex-row"` for Tailwind

- **`[THEME_AWARE_CLASSES]`** - Your theme/dark mode classes
  - Example: `"bg-white dark:bg-gray-900"` for Tailwind

- **`[CONTAINER_STYLES]`**, **`[HEADING_STYLES]`**, **`[LAYOUT_STYLES]`** - Your common style patterns

### Design Token Placeholders

- **`[YOUR_PRIMARY_COLOR_TOKEN]`** - Your primary color variable
  - Examples: `primary-600`, `brand-blue`, `iris-950`

- **`[EXTERNAL_UTILITIES]`**, **`[PACKAGE]`** - External dependencies you use

## Usage

Once configured, invoke the skill when working with Figma designs:

```bash
# In Claude Code
User: "Generate code from this Figma design: [figma-link]"
```

The skill will automatically:
1. Use Figma MCP tools to fetch design metadata, context, and screenshots
2. Search for existing components in your project
3. Generate code using your project's conventions
4. Map Figma variants to component props
5. Provide mock data patterns for backend-dependent features

## Examples

See `examples.md` for detailed workflow examples including:
- Button component reuse
- Card composition patterns
- Pages with backend requirements
- Creating new components with variants
- Full page layout implementation
- Common patterns and best practices

## Workflow

When you provide a Figma link, the skill follows this workflow:

1. **Fetch Metadata** - Get component structure and variant properties
2. **Get Context** - Extract colors, spacing, typography from design
3. **Get Screenshot** - Visual verification of the design
4. **Check Existing** - Search your codebase for matching components
5. **Decide Strategy** - Reuse, extend, or create new component
6. **Generate Code** - TypeScript component following your conventions
7. **Mock Data** - If backend needed, implement with mock data pattern

## Customization Tips

- Update the **Component Reuse Strategy** section with your project's available components
- Modify the **Coding Standards** section to match your team's conventions
- Adjust the **Quality Checklist** to include your project-specific requirements
- Add project-specific file naming conventions or import aliases

## Support

For issues with:
- **Figma MCP Server**: See [Figma MCP documentation](https://developers.figma.com/docs/figma-mcp-server)
- **Claude Code**: See [Claude Code documentation](https://docs.claude.com/claude-code)
- **This Skill**: Open an issue in your repository

## License

[Add your license here]
