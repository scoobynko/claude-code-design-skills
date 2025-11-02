# Claude Code Design Skills

A collection of Claude Code skills for streamlining design-to-code workflows.

## About

This repository contains custom skills for [Claude Code](https://claude.com/claude-code) that help automate and improve the process of converting designs into production-ready code.

## Available Skills

### Figma to Code

Generate production-ready React/Next.js code from Figma designs with systematic workflows, component reuse strategies, and variant mapping.

**Features:**
- Systematic Figma MCP tool usage workflow
- Component reuse prioritization
- Automatic Figma variant to code prop mapping
- Frontend/backend boundary enforcement
- TypeScript type safety
- Accessibility support
- Mock data patterns

[View Documentation →](./figma-to-code/README.md)

## Installation

### Prerequisites

- [Claude Code CLI](https://docs.claude.com/claude-code) installed
- For Figma to Code skill: [Figma MCP Server](https://developers.figma.com/docs/figma-mcp-server) installed

### Install Skills

**For Claude Code CLI:**

1. Clone this repository:
   ```bash
   git clone https://github.com/scoobynko/claude-code-design-skills.git
   ```

2. Copy skills to your Claude Code skills directory:
   ```bash
   # macOS/Linux
   cp -r claude-code-design-skills/figma-to-code ~/.claude-code/skills/

   # Windows
   xcopy claude-code-design-skills\figma-to-code %USERPROFILE%\.claude-code\skills\figma-to-code\ /E /I
   ```

3. Configure the skill according to its documentation

4. Restart Claude Code

**For Claude Desktop:**

1. Download or clone this repository

2. Configure according to its documentation

3. Create a .zip file of the configured `figma-to-code` folder

4. Open Claude Desktop app → **Settings** → **Capabilities** → **Skills** → **Upload skill**

5. Select your `figma-to-code.zip` file and the skill will be validated and activated

## Usage

Each skill includes detailed documentation in its respective directory. Skills are automatically available in Claude Code once installed and can be invoked when relevant to your task.

## Configuration

Each skill requires customization for your specific project. Check the individual skill's README for required configuration placeholders.

## Contributing

Contributions are welcome! If you'd like to add new skills or improve existing ones:

1. Fork this repository
2. Create a feature branch
3. Make your changes (for creating new skills, see [Claude Skills documentation](https://docs.claude.com/en/docs/build-with-claude/skills))
4. Submit a pull request

When creating a new skill, ensure it's generalized with placeholders so others can easily customize it for their projects.

## License

MIT License - See LICENSE file for details

## Author

Created by [@scoobynko](https://github.com/scoobynko)

## Support

For issues or questions:
- Open an issue in this repository
- Check [Claude Code documentation](https://docs.claude.com/claude-code)
- For Figma-specific issues, see [Figma MCP documentation](https://developers.figma.com/docs/figma-mcp-server)
