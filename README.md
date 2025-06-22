# CourtListener MCP Integration

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![MCP](https://img.shields.io/badge/MCP-Model%20Context%20Protocol-blue)](https://modelcontextprotocol.io/)

> AI-powered legal research using CourtListener API with Model Context Protocol (MCP) integration for Claude

## Project Overview

A comprehensive legal research tool that combines:
- **MCP Server**: Enables Claude to conduct legal research via CourtListener API
- **Judicial Writing Analysis**: AI model training for judge-specific opinion generation
- **Citation Verification**: Bluebook citation validation and formatting

## 🚀 Features

### MCP Integration (In Development)
- **Case Law Search**: Full-text search across millions of court opinions
- **Citation Verification**: Validate case citations and Bluebook formatting
- **Docket Access**: Retrieve detailed docket information
- **Smart Filtering**: Filter by jurisdiction, date, and precedential status
- **Natural Language**: Claude interprets natural language legal queries

### Judicial Writing Analysis (Complete ✅)
- **Judge Style Profiles**: Analyze individual judicial writing patterns
- **Training Data Generation**: Create AI training datasets from real opinions
- **Citation Pattern Analysis**: Extract citation integration styles
- **Bluebook Compliance**: Ensure proper legal citation formatting

## 📁 Repository Structure

```
courtlistener-mcp/
├── mcp-server/           # MCP server implementation
│   ├── index.js          # Main server entry point
│   └── tools/            # CourtListener API tools
├── judge-analysis/       # Judicial writing analysis
│   ├── comprehensive_foley_training.txt
│   └── style-analyzer.js
├── docs/                 # Documentation
└── examples/             # Usage examples
```

## 🛠️ Installation

```bash
# Clone the repository
git clone https://github.com/open-legal-tools/courtlistener-mcp.git
cd courtlistener-mcp

# Install dependencies
npm install

# Configure API credentials
cp .env.example .env
# Edit .env with your CourtListener API key
```

## 📖 Usage

### MCP Server with Claude Desktop

1. Add to your Claude desktop configuration:

```json
{
  "mcpServers": {
    "courtlistener": {
      "command": "node",
      "args": ["path/to/courtlistener-mcp/mcp-server/index.js"],
      "env": {
        "COURTLISTENER_API_KEY": "your-api-key"
      }
    }
  }
}
```

2. Use natural language queries:
   - "Find recent Supreme Court cases about AI and copyright"
   - "Check if Miranda v. Arizona is still good law"
   - "Show me 9th Circuit cases on qualified immunity from 2023"

### Judge Writing Analysis

```bash
# Analyze a judge's writing style
node judge-analysis/style-analyzer.js --judge "Foley" --court "ind"

# Generate training data
node judge-analysis/training-generator.js --input opinions/ --output training.txt
```

## 🔧 API Reference

### Available MCP Tools

#### `search_opinions`
```typescript
{
  query: string;          // Search query
  court?: string;         // Court identifier
  after?: string;         // Date after (YYYY-MM-DD)
  before?: string;        // Date before (YYYY-MM-DD)
  precedential?: boolean; // Only precedential opinions
}
```

#### `verify_citation`
```typescript
{
  citation: string;  // Full citation string
}
```

#### `get_citing_cases`
```typescript
{
  id: string;     // Opinion ID
  limit?: number; // Maximum results
}
```

## 🎯 Current Status

- **Phase 1 Complete ✅**: Judge writing style analysis and training data
- **Phase 2 In Progress 🔄**: MCP server implementation
- **Phase 3 Planned 📋**: Advanced citation network analysis

## 🤝 Contributing

Contributions welcome! See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

## 📄 License

MIT License - see [LICENSE](LICENSE) for details.

## 🙏 Acknowledgments

- [CourtListener](https://www.courtlistener.com/) by the Free Law Project
- [Model Context Protocol](https://modelcontextprotocol.io/) by Anthropic
- Indiana Court of Appeals for publicly available opinions

## 📞 Support

- Issues: [GitHub Issues](https://github.com/open-legal-tools/courtlistener-mcp/issues)
- CourtListener API: [Documentation](https://www.courtlistener.com/api/)
- MCP Docs: [Anthropic MCP Guide](https://support.anthropic.com/en/articles/11503834-building-custom-integrations-via-remote-mcp-servers)
