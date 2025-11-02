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

- [Claude Code CLI](https://docs.claude.com/claude-code) or [Claude Desktop](https://claude.ai/download) installed
- Figma MCP Server installed ([installation guide](https://developers.figma.com/docs/figma-mcp-server))
- Figma Desktop app running
- React/Next.js project (or compatible framework)

## Installation

**For Claude Code CLI:**

1. Clone or download this repository

2. Copy to your Claude Code skills directory:
   ```bash
   # macOS/Linux
   cp -r figma-to-code ~/.claude-code/skills/

   # Windows
   xcopy figma-to-code %USERPROFILE%\.claude-code\skills\figma-to-code\ /E /I
   ```

3. **Configure for your project** - Customize `SKILL.md` and `examples.md` by replacing placeholders:

   **Directory Structure:**
   - `[FRONTEND_DIR]` - Your frontend directory (e.g., `src`, `app`, `client`)
   - `[BACKEND_DIR]` - Your backend directory (e.g., `server`, `backend`, `api`)
   - `[COMPONENTS_DIR]` - Components directory (e.g., `components`, `src/components`)
   - `[PAGES_DIR]` - Pages/routes directory (e.g., `app`, `pages`)
   - `[TYPES_DIR]` - TypeScript types directory (e.g., `types`, `@/types`)

   **Styling System:**
   - `[STYLING_UTILITY]` - Your styling utility (e.g., `cn`, `classNames`, `clsx`)
   - `[VARIANT_SYSTEM_IMPLEMENTATION]` - Your variant system (e.g., CVA, styled-components)
   - `[RESPONSIVE_LAYOUT_CLASSES]`, `[THEME_AWARE_CLASSES]` - Your styling patterns

   **Design Tokens:**
   - `[YOUR_PRIMARY_COLOR_TOKEN]` - Primary color variable (e.g., `primary-600`, `brand-blue`)

   **💡 Tip:** Use Claude Code to help! Ask: "Replace all placeholders in SKILL.md and examples.md with my project's implementation details"

4. Restart Claude Code

**For Claude Desktop:**

1. Download or clone this repository

2. Configure according to steps above

3. Create a .zip file of the configured `figma-to-code` folder

4. Open Claude Desktop app → **Settings** → **Capabilities** → **Skills** → **Upload skill**

5. Select your `figma-to-code.zip` file and the skill will be validated and activated

## Usage

Provide a Figma design link to Claude Code (e.g., "Generate code from this Figma design: [figma-link]").

The skill automatically:
1. Fetches design metadata, context, and screenshots using Figma MCP tools
2. Searches for existing components in your codebase
3. Generates TypeScript code following your project's conventions
4. Maps Figma variants to component props
5. Implements mock data patterns when backend APIs are needed

See `examples.md` for detailed workflow examples and common patterns.

## Support

- **Figma MCP Server**: [Figma MCP documentation](https://developers.figma.com/docs/figma-mcp-server)
- **Claude Code**: [Claude Code documentation](https://docs.claude.com/claude-code)
- **This Skill**: [Open an issue](https://github.com/scoobynko/claude-code-design-skills/issues)

## License

MIT License - See [LICENSE](../LICENSE) file for details.
