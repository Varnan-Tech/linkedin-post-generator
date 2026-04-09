# linkedin-post-generator

Generate LinkedIn posts from any content: blog posts, articles, GitHub PRs, or a brief description of what you built. The agent reads your source material, applies LinkedIn's proven content patterns, and produces a post with the right hook, story arc, and formatting — ready to copy-paste or publish directly via Composio.

## Post Styles

| Style | Use When | Example Input |
|-------|----------|---------------|
| Founder/Ship | Personal story of building or shipping | "We just merged our streaming SDK after 3 weeks" |
| Insight | Educational observation or lesson | Blog article, pattern you noticed, lesson learned |
| Product Launch | Announcing a new tool or feature publicly | PR description, launch brief, new feature going GA |
| Tutorial Summary | Distilling a long technical post | Tutorial URL, deep-dive article, step-by-step guide |

The agent auto-detects the right style. You can override it by asking for a specific style.

## Requirements

- No LLM API key needed. The agent IS the LLM.
- Composio is optional, for direct LinkedIn posting.

## Setup

### 1. Configure Composio (Optional — for direct posting)

Without Composio, the agent outputs the formatted post as text for copy-paste. This is the default and works with zero configuration.

To enable direct posting:
1. Get your API key at https://app.composio.dev/settings
2. Connect your LinkedIn account at https://app.composio.dev/app/linkedin
3. Complete the OAuth flow
4. Add the key to your `.env` file:

```bash
cp .env.example .env
# Edit .env and add your COMPOSIO_API_KEY
```

## How to Use

From a URL:
```
"Turn this into a LinkedIn post: https://yourblog.com/my-post"
"Write a LinkedIn post about this article: [URL]"
```

From pasted text:
```
"Here's a case study, turn it into a LinkedIn post: [paste text]"
"Convert this to a LinkedIn post: [paste article]"
```

From a PR or shipped feature:
```
"Write a LinkedIn post about this PR we merged: [paste PR description]"
"Announce our new feature on LinkedIn: [describe the feature]"
```

With a style override:
```
"Write a LinkedIn post in Tutorial Summary style about: [topic]"
"Use the Product Launch style for this: [description]"
```

With direct posting:
```
"Post this to LinkedIn: [paste content]"
"Generate and post a LinkedIn update about [topic]"
```

## Output

| Output | Description |
|--------|-------------|
| LinkedIn post | Formatted text, 900-1,300 characters, ready to publish |
| First comment | Prepared text with source links — post this immediately after publishing |
| Hook alternatives | 2 additional hook line options in different formats |
| Posted confirmation | If Composio is configured and you confirm posting |

## Why the Agent Formats Posts This Way

Four rules drive every post:

- **Hook first.** The first line is all most people see. It must work standalone.
- **Short paragraphs.** 1-3 lines, then a blank line. LinkedIn is mobile-first.
- **Links in comments.** URLs in the post body reduce LinkedIn's distribution. All links go in the first comment.
- **Question or CTA.** End with one or the other, not both. Comments matter more than reactions for distribution.

## Project Structure

```
linkedin-post-generator/
├── SKILL.md                              # Agent instructions
├── README.md                             # This file
├── .env.example                          # Environment variables template
├── evals/
│   └── evals.json                        # Test prompts for skill evaluation
└── references/
    ├── linkedin-format.md                # Full LinkedIn content spec and format rules
    └── output-template.md               # Post templates for all 4 styles with examples
```

## License

MIT
