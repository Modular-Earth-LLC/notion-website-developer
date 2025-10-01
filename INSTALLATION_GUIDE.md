# Notion Website Developer - Installation Guide

This guide provides detailed setup instructions for installing the Notion Website Developer system on your preferred AI platform.

## Table of Contents

1. [Overview](#overview)
2. [Platform-Specific Installation](#platform-specific-installation)
   - [Cursor](#cursor)
   - [GitHub Copilot](#github-copilot)
   - [ChatGPT](#chatgpt)
   - [Claude](#claude)
   - [Other Platforms](#other-platforms)
3. [Configuration](#configuration)
4. [Testing Your Installation](#testing-your-installation)
5. [Troubleshooting](#troubleshooting)

## Overview

The Notion Website Developer consists of three main components:

1. **System Prompt** - Shared context and knowledge base schema
2. **Template Generator** - Creates website structure
3. **Content Generator** - Populates template with content

Installation typically takes 5-10 minutes.

## Platform-Specific Installation

### Cursor

Cursor offers the most automated experience with full tool support.

#### Method 1: .cursorrules (Recommended)

1. Create `.cursorrules` file in your project root:
   ```bash
   touch .cursorrules
   ```

2. Copy the entire contents of `prompts/notion_website_developer.system.prompt.md` into `.cursorrules`

3. Add mode-specific rules at the top:
   ```
   # Cursor Configuration
   preferred_tools: [read_file, write_file, web_search]
   auto_save: true
   
   [Original system prompt content follows...]
   ```

4. Restart Cursor to load the configuration

#### Method 2: Cursor Settings

1. Open Cursor Settings (Cmd/Ctrl + ,)
2. Navigate to "Features" → "Rules for AI"
3. Paste the system prompt content
4. Save settings

#### Using the Prompts

1. Open the specific user prompt you need
2. Copy its contents
3. Paste into Cursor chat
4. Follow the interactive workflow

### GitHub Copilot

GitHub Copilot works best with workspace configurations.

#### Setup Instructions

1. Create `.github/copilot/instructions.md`:
   ```bash
   mkdir -p .github/copilot
   touch .github/copilot/instructions.md
   ```

2. Copy system prompt content into `instructions.md`

3. Add Copilot-specific configuration:
   ```markdown
   ## Copilot Configuration
   tools: ['codebase', 'search', 'fetch', 'websearch']
   
   [System prompt content...]
   ```

4. For specific tasks, create chat modes:
   ```bash
   # Template generation mode
   touch .github/chatmodes/template-generator.md
   
   # Content generation mode  
   touch .github/chatmodes/content-generator.md
   ```

5. Copy respective user prompts into chat mode files

#### Usage

1. Open Copilot Chat
2. Type `/template-generator` or `/content-generator`
3. Follow the guided workflow

### ChatGPT

ChatGPT requires creating a Custom GPT or using direct prompting.

#### Method 1: Custom GPT (Plus/Team users)

1. Go to [chat.openai.com](https://chat.openai.com)
2. Click "Explore" → "Create a GPT"
3. In "Configure" tab:
   - **Name**: Notion Website Developer
   - **Description**: Creates professional portfolio websites in Notion
   - **Instructions**: Paste entire system prompt
   - **Conversation starters**:
     - "Create a Notion website template for me"
     - "Generate content for my portfolio website"
     - "Help me optimize my existing Notion site"
   - **Knowledge**: Upload any reference files

4. Save and publish (private or public)

#### Method 2: Direct Chat

1. Start new chat
2. Paste this initialization:
   ```
   I want you to act as a Notion Website Developer. Here's your system context:
   
   [Paste system prompt]
   
   Now, I'd like to [create a template/generate content].
   ```

3. Continue with specific user prompt

### Claude

Claude Projects provide the best experience for this system.

#### Project Setup

1. Go to [claude.ai](https://claude.ai)
2. Create new Project: "Notion Website Developer"
3. Add Project Instructions:
   - Copy entire system prompt
   - Set as project instructions

4. Add Knowledge (optional):
   - Upload example templates
   - Add reference materials
   - Include style guides

#### Usage

1. Open the project
2. Start new conversation
3. Paste specific user prompt
4. Follow interactive workflow

#### Artifacts

Claude's Artifacts feature is perfect for:
- Viewing generated templates
- Editing content in real-time
- Exporting final files

### Other Platforms

For platforms not listed above, use this general approach:

#### Setup

1. **System Message/Context**:
   - Look for system prompt, context, or instruction settings
   - Paste the system prompt content
   - Save configuration

2. **User Prompts**:
   - Keep user prompts handy
   - Copy/paste as needed

3. **Tool Adaptation**:
   ```
   Note: I'm using [Platform Name]. Available tools:
   - [List available features]
   
   Please adapt your workflow accordingly.
   ```

## Configuration

### Essential Files Structure

```
notion-website-developer/
├── prompts/
│   ├── notion_website_developer.system.prompt.md
│   ├── notion_website_template_generation.user.prompt.md
│   └── notion_website_content_generation.user.prompt.md
├── inputs/
│   └── knowledge-bases/
│       └── job_search_knowledge_base.yaml (optional)
├── outputs/
│   └── websites/
│       └── [Your generated files]
├── .cursorrules (Cursor only)
├── .github/
│   └── copilot/ (GitHub Copilot only)
└── README.md
```

### Knowledge Base Setup (Optional)

If you have existing data:

1. Create `inputs/knowledge-bases/my_data.yaml`:
   ```yaml
   user_profile:
     basic_info:
       full_name: "Your Name"
       professional_title: "Your Title"
       email: "email@example.com"
   # ... follow schema from system prompt
   ```

2. Reference in your prompts:
   ```
   Please use the data from inputs/knowledge-bases/my_data.yaml
   ```

## Testing Your Installation

### Quick Test

1. Start with template generation:
   ```
   "Create a simple Notion website template for a software engineer"
   ```

2. Expected response should include:
   - Greeting and process explanation
   - Questions about your preferences
   - Research phase
   - Template generation
   - Markdown output

### Full Workflow Test

1. **Template Generation**:
   - Run template generator
   - Save output as `template.md`

2. **Content Generation**:
   - Run content generator
   - Reference the template
   - Provide your information
   - Save output as `content.md`

3. **Import to Notion**:
   - Create new Notion page
   - Copy/paste markdown
   - Verify formatting

## Troubleshooting

### Common Issues

#### "System prompt not recognized"

- Ensure you've saved the configuration
- Restart your AI platform
- Try repasting the prompt

#### "Tools not working"

- Check platform capabilities
- Use manual mode as fallback
- Provide information directly

#### "Output too long"

- Request chunked delivery
- Focus on specific sections
- Use multiple sessions

### Platform-Specific Issues

#### Cursor
- Check `.cursorrules` is in project root
- Verify file permissions
- Try Cursor settings method

#### ChatGPT
- Ensure Custom GPT saved properly
- Check token limits
- Use GPT-4 for best results

#### Claude
- Verify project instructions saved
- Check artifact settings
- Use Claude 3 Opus/Sonnet

### Getting Help

1. Check error messages carefully
2. Review platform documentation
3. Try manual mode as fallback
4. Report issues on GitHub

## Next Steps

After successful installation:

1. **Gather Your Materials**:
   - Resume/CV
   - LinkedIn profile
   - Portfolio pieces
   - Target job descriptions

2. **Start Building**:
   - Begin with template generation
   - Iterate on structure
   - Add your content
   - Refine and polish

3. **Optimize and Launch**:
   - Test on mobile
   - Verify all links
   - Publish to Notion
   - Share your success!

---

**Need help?** Check the [System Prompts Guide](SYSTEM_PROMPTS_GUIDE.md) for advanced configuration →
